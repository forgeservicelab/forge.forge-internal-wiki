System administration guides
===========================================================================================

Backup and restore FORGE (WiP)
=========================================================================================

There are a number of services in FORGE currently being backed up. This
is a work in progress with the ultimate goal of safeguarding all of
FORGE's services so they can be restored in case of catastrophic
events.

As of this writing:

### Backed up services

-   Authentication Service (CASino)
-   FORGE Service Lab portal (Plaza)
-   Gitlab
-   Jenkins (work in progress)
-   FORGE DBserver
-   Monitoring server (Nagios)
-   Insightly

### Services pending backup procedures

-   Support node (handled by CSC VMWare cloud procedures), includes:
    -   Redmine
    -   XMPP server
    -   Password reset application
-   Admin node (handled by CSC VMWare cloud procedures), includes:
    -   Forge LDAP tools
    -   OpenStack CLI tools
-   Auth node (handled by CSC VMWare cloud procedures), includes:
    -   OpenLDAP server and LDAP database.

### Services pending restore procedures

-   Jenkins

### Retention policy

Backed up data is stored for one year.

Backup procedures
-----------------------------------------------------------------

A replication node exists to act as a data warehouse for the various
FORGE services.\
 An In-House server exists to act as a safekeeping warehouse.

Following are the specific procedures by which the above services are
being backed up.

### Authentication Service

The Authentication application (CASino) does not keep persistent data so
no safekeeping is needed. An Ansible playbook exists to restore the
service application if needed.

### Plaza

The FORGE Service Lab portal is a complex cluster system, as described
in [Plaza cluster architecture](2_Infrastructure.md#plaza-cluster-architecture). The
critical components to be backed up are:

* Exported Data on NFS server cluster
* Data on the MySQL cluster

For the NFS exports, the replication node synchronizes the export
directory on the NFS cluster with its own filesystem on an hourly basis,
this creates a "live" copy of the entire drupal directory tree on the
replication node that is at most one hour old. This filesystem carbon
copy is tarballed on a daily basis and committed to warehousing.

For the MySQL cluster the replication node hosts a MySQL replication
slave, thus keeping a local copy of the production database (read
queries are possible against this node). A snapshot of this database is
created on a daily basis via `mysqldump` and committed to warehousing.

### Gitlab

Since the GitLab backend database is now detached from the GitLab node,
its backup procedure will only concern the repositories' directory tree.
For the backup procedure of GitLab's database see [FORGE
DBserver](#forge-dbserver).

The GitLab repositories' directory tree is synchronized to the
replication node on an hourly basis, effectively creating a carbon copy
on the replication node that is at most one hour old. This filesystem
copy is tarballed on a daily basis and committed to warehousing.

### Jenkins

Jenkins does not keep persistent data, but the job configuration files
are of capital importance to completely restore the jenkins instance.
Each job on Jenkins contains a `config.xml` file with which it is
possible to restore the job in case of data loss, these files then are
synchronized with the replication node on an hourly basis. The jobs
directory tree is kept as well. On a daily basis this directory tree is
tarballed and committed to warehousing.

### FORGE DBserver

The FORGE DBserver is a node running a single-node PostgreSQL cluster
with schemas for Redmine and GitLab on both testing and production
environments. The replication node hosts a single-node PostgreSQL
cluster working as a hot\_standby to FORGE DBserver for streaming
replication (read queries are possible against this node, and actively
performed by BI on Analytics node). A snapshot of this cluster is
created on a daily basis via `pg_dumpall` and committed to warehousing.

### Monitoring server (Nagios)

The Monitoring server (Nagios) does not keep persistent data so no
safekeeping is needed. An Ansible playbook exists to restore the service
application if needed.

### Insightly

Insightly response

-   Insightly does not provide individual backup or data restoration
    services for customers, but you have three options to make copies of
    your Insightly data, and I recommend doing so on a regular basis.
    None of these options are meant as a complete backup and only serve
    as an emergency function in case a user was to unintentionally
    delete data.

-   You can export all the basic records to a CSV file. This is the only
    option available if you want to re-import your records to Insightly
    through our website. See: How do I export my data from Insightly?
	
    We offer an XML export in System Settings &gt; Data Export. The
    exported file is an archival format that requires an application or
    service to read or convert XML data. This file type cannot be
    imported to Insightly.
	
    Customers with the appropriate technical resources have the option
    of using our API to create their own interfaces with other
    applications or for exporting data. See our API developers page.
    Please let us know if you have any other questions.

What is being done by FORGE

-   Insightly data is been backed up by backup machine every Friday by
    cron running a lyfetch.py -a command
    (<https://git.forgeservicelab.fi/forge/insightly-fetch/>) and
    placing resulted tarball to
    /data/insightly/insightlybackup-YYYY-MM-DDTHH-MM.tar.gz file.

### Warehousing

The In-House server at digile's premises acts as a data warehouse for
the daily snapshots taken on the replication host.

Every day at midnight the In-House server will pull any and all new
snapshots of all databases and filesystems backed up on the replication
host. Since the replication host runs its snapshot procedures at around
6:30, this means that any given day the In-House data warehouse will
hold *yesterday's* data, as succinctly shown in the following diagram:

![Warehousing
Diagram](/files/Warehouse_scheme.png)

Note that the depicted data blocks represent data volume rather than
time. Snapshot and warehouse procedures don't necessarily overlap and
ideally won't.

Restore procedures
-------------------------------------------------------------------

Although we strive to automate as much of our procedures as possible, as
of this writing a great deal of the restoration procedures is still
manual.

### Authentication Service

There is an [Ansible
role](https://git.forgeservicelab.fi/ansible-roles/casino) available to
provision an instance with CASino. Read the role's [README.md
file](https://git.forgeservicelab.fi/ansible-roles/casino/blob/master/README.md)
for more information on how to use it.

### FORGE Service Lab portal

The FORGE Service Lab portal is a complex system and several restore
scenarios are possible.

#### Database data loss

If the MySQL database gets corrupted, it is possible to restore from any
of the daily snapshots available on the replication node or on the
In-House server. The procedure is as follows, provided at a station with
access to the production MySQL server:

-   Decompress the snapshot (they are available on the replication node
    under `/data/database_snapshots/plaza`).

        $ gunzip plaza_production-YYYY-mm-dd.sql.gz

-   These snapshots are capable of being restored to the replication
    slave (this is by design), since we're restoring to the replication
    master, we need to remove the slave configuration statements. Open
    the file on your editor of choice and comment out or remove the line
    `CHANGE MASTER TO [...]`

-   Restore the database

        $ mysql -h hostname_or_ip -u your_user -p < plaza_production-YYYY-mm-dd.sql

#### User data loss

If user uploads are lost they can be recovered in a number of ways:

-   If the loss is caught within the hour (synchronization happens at 5
    minutes to the hour), the lost files should still be present on the
    replication node under `/data/filesystem/plaza/sites/default/files`
-   If the lost data is not found in the live sync, it can be found in
    any of the daily snapshots on the replication node under
    `/data/filesystem_snapshots/`
    -   As of this writing, the filesystem snapshots contain a
        monolithic copy of the `/data/filesystem` tree on the
        replication node. After decompression, the missing file should
        be under `data/filesystem/plaza/sites/default/files`.

With the lost files located they can be restored on any of the drupal
nodes or the NFS master on the Plaza cluster on the following locations,
respectively:

-   `/var/www/sites/default/files`
-   `/data/exports/sites/default/files`

If the lost files were not originally under `sites/default/files` then
that means that they weren't uploaded by portal users and therefore they
should be present on version control, in which case a redeployment from
Jenkins will restore them.

#### Massive loss

In the case of catastrophic loss of any number of the nodes of the
cluster restoration will proceed as follows:

-   Instantiation of replacements for the lost nodes (prerequisites
    apply, this includes attached volumes, ssh access, firewall
    rules, etc.)
-   Complete run of the [Plaza
    playbook](https://git.forgeservicelab.fi/ansible/ansible_plaza) (not
    just redeployment)
-   Run the procedures for [database loss](#database-data-loss) and/or
    [user data loss](#user-data-loss) as needed.

### Gitlab

There are two major scenarios for data loss on GitLab, plus a couple of
minor configuration hiccups that may occur along the way, as exposed
below:

#### Repository data loss

Gitlab repositories backed up on the replication node as explained
[above](#gitlab), repository data can be retrieved from there and
restored to it's proper location on the GitLab machine (typically
`/data/apps/gitlab/repositories`).

After restoration, the activity on these repositories may not be shown
on GitLab UI, or they may appear as empty repositories or even have
desyncrhonized data, to fix this, run the following task on the gitlab
install directory as the gitlab user:

    $ bundle exec rake gitlab:import:repos RAILS_ENV=production

#### Database data loss

Gitlab's database runs on FORGE DBserver, for restoration info see
[DBserver's](#forge-dbserver) restoration procedures.

#### SSH authorized_keys desynchronization

It can be the case that gitlab user's authorized_keys file is lost or
becomes somehow corrupted. This file is used by gitlab-shell to manage
authentication and authorization of git requests. To regenerate it, run
the following task on the gitlab install directory as the gitlab user:

    $ bundle exec rake gitlab:shell:setup RAILS_ENV=production

#### Missing satellites directories

After restoring or manually importing repositories, gitlab's satellite
directory for a given repo may be missing or desynchronized, to fix this
run the following task on the gitlab install directory as the gitlab
user:

    $ bundle exec rake gitlab:satellites:create RAILS_ENV=production

### Jenkins

Jenkins' restoration procedure is a work in progress. At the time of
this writing, an [Ansible
role](https://git.forgeservicelab.fi/ansible-roles/jenkins) capable of
setting up a blank instance with jenkins and all the plugins needed for
FORGE's CI service.

A second [Ansible role with
mods](https://git.forgeservicelab.fi/ansible-roles/forge_jenkins_mods)
applies modifications to the CI instance to accomodate to FORGE's Look &
Feel.

The job configuration files are being backed up. It is possible to
restore a job by running jenkins-cli as follows:

    $ java -jar jenkins-cli.jar -s http://jenkins.url/ create-job jobname < config.xml

The immediate future plans are to compose a FORGE specific playbook for
jenkins that ties all roles together and is capable of restoring a fully
functioning instance, including job restoration.

### FORGE DBserver

The daily snapshots from FORGE DBserver can be restored by logging in to
the node as the `postgres` user (this will grant us full access to the
database server) and running the following commands:

    $ gunzip dbserver-YYYY-mm-dd.psql.gz
    $ psql -f dbserver-YYYY.mm.dd.psql

Since these snapshots are taken with `pg_dumpall` they will restore the
entirety of the database's schemas, including users and their
permissions. If restoration of only one database is required then it'll
be needed to extract the relevant statements from the dump file. This
can be done with [this
script](http://madssj.com/blog/2010/04/09/extracting-a-single-database-from-a-pg_dumpall-postgresql-dump/),
e.g.:

    $ gunzip dbserver-YYYY-mm-dd.psql.gz
    $ postgresql_dump_extract.sh <dump_file> <db_name> > database.sql
    $ psql -f database.sql

### Monitoring server (Nagios)

Nagios can be completely restored by running its dedicated [Ansible
playbook](https://git.forgeservicelab.fi/ansible/nagios4). Please, read
the playbook's [README.md
file](https://git.forgeservicelab.fi/ansible/nagios4/blob/master/README.md)
for more information on how to use it.

### Other procedures

The services listed under [Services pending backup
procedures](#ervices-pending-backup-procedures) are being handled by
CSC. This means that restoration of these VMs full or of single files
from their filesystems is possible by issuing a restoration request to
CSC.


External SP into IdP
====================

This is a brief description about the process of adding an external SP
into IdP after customer request.

1.  Install python-bs4 if not present
2.  Checkout <https://git.forgeservicelab.fi/ansible/SP_adder>
3.  Copy customer provided metadata.xml into SP_adder directory
4.  Ensure metadata.xml doesn't have a validUntil entry (or at least an
    expired one)
5.  Verify that playbook contains proper URL for POST target (idp,
    testidp etc...)
6.  Verify from saml20-sp-remote.php that SP name is not empty,
    otherwise it's not clickable in SAML UI
7.  After verifying from SAML UI that configuration looks ok,
    notify customer.

FORGE admin host
==========================================================

FORGE admin (forgeadmin.csc.fi) is a central server for running FORGE
related administrative scripts, playbooks and other tasks. It's
currently hosted in CSC VMware cloud. Basic configuration of a similar
server can be done with the
<https://git.forgeservicelab.fi/ansible/admin_config> playbook. The host
contains both user specific accounts and a central one called
butler.service.

Centralized playbooks
--------------------------------------------------------------------

The butler.service user's home directory contains playbooks for
performing various FORGE sysadmin tasks. These are divided into
subdirectories playbooks-git and playbooks-non-git. The former contains
playbooks checked out from git.forgeservicelab.fi and the latter
contains playbooks which, for strategic or security reasons, reside only
on local disk and are versioned to the replication host and warehouse
servers.

Once logged in with your own user, you can access the butler account
with:

` [user@forgeadmin ~]$ sudo su - butler.service`

Let's say there's a host outside standard DIGILE tenants where the
FORGE admin group accounts need to be added. A playbook to perform this
task is run as follows:

` [butler.service@forgeadmin ~]$ cd playbooks-non-git/account_create_oneoff/ [butler.service@forgeadmin account_create_oneoff]$  [butler.service@forgeadmin account_create_oneoff]$ ./account_create.sh -t 193.166.25.222 -u debian`

Please note that the `playbooks-non-git/account_enforcement` playbook
is intended to be periodically run from CRON:

` [butler.service@forgeadmin account-cleanup]$ crontab -l|grep play */5 * * * * cd /home/butler.service/playbooks-non-git/account_enforcement; ./account_enforcement.sh -f 50 2>&1 | egrep 'failed=1|unreachable=1'`

Let's now consider the situation where a user needs to be removed from
a host. This is done with the `playbooks-git/account-cleanup` playbook.

` [butler.service@forgeadmin ~]$ cd playbooks-git/account_cleanup/ [...add tenant to nova.yml...] [...add user to remove to group_vars/all...] [butler.service@forgeadmin account_cleanup]$ ./account_cleanup.sh`

GitLab Administration
======================================================================

This page describes the specifics of our gitlab installation and
suggests ways to perform administration tasks.

GitLab is a Git hosting application. It resembles GitHub in many ways.
We have a GitLab instance for use in FORGE. It is installed in
git.forgeservicelab.fi, a VM provided from CSC VMware cloud. The OS is
RHEL 6.

Installation details
--------------------------------------------------------------------

-   Installed version: 6.1
-   Installed Ruby version: 2.0.0 over rvm
-   Installed Git version: 1.8.4
-   Roughly follows
    <https://github.com/gitlabhq/gitlab-recipes/tree/master/install/centos>
-   uses init script gitlab-unicorn from
    <https://github.com/gitlabhq/gitlab-recipes/tree/master/init/sysvinit/centos>

GitLab has dedicated user "gitlab" whose home diris /data/apps/gitlab.
The GitLab app itself installed in /data/apps/gitlab/gitlab. It's using
mysql as a database, redis for caching, nginx as web server, and openssh
for SSH access. Email notifications are send over Google smtp server
from service account <git@forgeservicelab.fi>.

Gems for gitlab are installed with budle. Not as a deployment budle but
system-wide (it's easier to customize and we don't plan to run any other
ruby app there anyway). If you'd like to change gem dependencies, you
would list the gems in /data/apps/gitlab/gitlab/Gemfile and then run

    $ root@git $ bundle install

Gitlab is configured from files in /data/apps/gitlab/gitlab/config,
mainly gitlab.yml. See the directory through for available settings.

User login and SSO hack
--------------------------------------------------------------------------

GitLab allows to login users from more providers - LDAP/Google
account/CAS/Twitter etc. However, by default a user's identity is given
by username-provider combination, e.g. tkarasek-SSO and tkarasek-LDAP
are two different users. That is, in my opinion, undesirable as we
should allow single user log in from different provider and see that
same account. User's identity should be given simply by his username.
That's why I modified the relevant logic in GitLab, so that we can use
either our CAS SSO (in browser) or git https transport (git client) and
use the same identity. The diff is very simple. It's just a few
modifications in lib/gitlab/oauth/user.rb:

    --- user.rb.old 2013-09-26 16:04:57.103543287 +0300
    +++ user.rb 2013-09-27 11:23:29.249895849 +0300
    @@ -41,7 +41,7 @@
             private
             def find_by_uid_and_provider`
    -          model.where(provider: provider, extern_uid: uid).last`
    +          model.where(username: uid).last`
             end
             def uid`
    @@ -53,11 +53,11 @@
             end
           def name`
    -          auth.info.name.to_s.force_encoding("utf-8")`
    +          auth.info.first_name.to_s.force_encoding("utf-8") + " " + auth.info.last_name.to_s.force_encoding("utf-8")`
             end
             def username`
    -          email.match(/^[^@]*/)[0]`
    +          auth.info.name.to_s.force_encoding("utf-8")`
             end
             def provider`

### sshd for Gitlab

In order to separate gitlab sshd from the sshd for administation, we run
another instance dedicated to Gitlab. It's listening on port 10022.
There is a special initscript and config file for the instance
(/etc/init.d/sshd\_gitlab and /etc/ssh/sshd\_gitlab\_conf)

### developers memebership check

In order to control membership in the "developers" group, there is one
more check in `/data/apps/gitlab/gitlab/lib/gitlab/oauth/user.rb` so
that the method find\_by\_uid\_and\_providers looks like

            def find_by_uid_and_provider
              log.info("find_by_uid_and_provider uid: #{uid}, provider: #{provider}")
              #model.where(provider: provider, extern_uid: uid).last
              ldap_handle = OmniAuth::LDAP::Adaptor.new(Gitlab.config.ldap)
              q = 'memberOf=ou=developers,ou=groups,dc=forgeservicelab,dc=fi'
              filter = Net::LDAP::Filter.construct(q)
              base = uid
              if provider == :cas
                # when provider == :cas, the uid is only the cn, not whole dn
                # as in case of provider == :ldap
                user_tree = Gitlab.config.ldap['base']
                base = "cn=#{uid},#{user_tree}"
              end
              log.info("find_by_uid_and_provider filter: #{filter}")
              r = ldap_handle.connection.search(base: base, filter: filter)
              log.info("result: #{r}")
              if r == []
                raise_error("You are not a FORGE developer")
              end
              model.where(username: uid).last
            end

Updating
--------------------------------------------

There is an update guide coming with new release. However, as there are
a few hacks present, update is not always straightfoward and there are a
few things to be done in addition. In the update guide you will be asked
at some point, to go to /data/apps/gitlab/gitlab and git checkout of the
new release tag. Few things are useful to be done prior to the checkkout
and few after the checkout, but before the "bundle install" and database
migrations.

### Before checking out the new release

-   copy out the gitlab/config directory because it will be re-written
    by git checkout of the new version, there are some modifications
    that need to be restored. You can find out what differs by *diff -qr
    oldconfig gitlab/config*. There is a lot of modifications, related
    to gitlab user and home, ldap, CAS, etc.
-   copy out app/assets

### After checking out the new release, but before running "bundle install"

-   add following line to the Gemfile:

        gem 'omniauth-cas'

-   make sure the newrelic config file is in gitlab/config

-   do modifications in lib/gitlab/oauth/user.rb as shown in the diff
    above

-   update /etc/init.d/gitlab from gitlab-unicorn from
    <https://github.com/gitlabhq/gitlab-recipes/tree/master/init/sysvinit/centos> -
    diff existing version with the new file first and update possible
    variable values (path, username...)

OpenStack Administration Knowledge base
=============================================================================================================

-   This page contains help for various OpenStack administration tasks.
-   It focuses on FORGE specific issues.
-   Aim is not to copy OpenStack administration guide or manual pages
    but to provide hints to avoid wasting time again when somebody has
    learned to do some task.

**THIS PAGE IS UNDER CONSTRUCTION**

-   All the tasks are done with the command line tools via
    Administrative APIs which are restricted in the OpenStack
    installation firewall.
-   Please contact (USERNAME REMOVED) in case of the access
    problems or any other problems or questions.

User and project Management
=====================================================================================

Add
-------------------------------------

### Add a new project

Using LDAP.

See [Resource_Allocation_Process](3_OperationalGuides.md#resource-allocation-process)

### Add a user

Using LDAP.

See
[Resource_Allocation_Process](3_OperationalGuides.md#resource-allocation-process)

### Add a customer network

Remove users and groups
-----------------------------------------------------------------------------

### Remove user from a project

Using LDAP.

Please note that if the user is logged in, the session stays valid for
24 hours and they are able to act as usual.

The resources created by the user remains untouched in Project's
perspective e.g. the instances created and by the user will remain
running.

### Remove a project

Using LDAP.

Clean the resources (instances, snaphots, images, volumes).

Data retention policy? Warning procedure before time of the Project
ends?

Resource management
=====================================================================

Project quota
---------------------------------------------------------

### Nova (CPU, RAM, Ephemeral disk)

    keystone tenant-list
    nova quota-show --tenant <tenant id>
    nova help quota-update

### Cinder (Volumes)

    cinder quota-show <tenant name>
    cinder help quota-update 

### Quantum (amount of floating IPs)

    quantum quota-show --tenant-id <tenant id>

Administrating the flavors
-----------------------------------------------------------------------------------

    nova flavor-list
    nova help flavor-create 
    nova flavor-delete

It is technically possible to create a Project specific flavor e.g. to
satisfy some project's specials needs.

FORGE OpenStack SecurityGroups
=================================================================================================

Naming convension
-----------------------------------------------------------------------

At forge we use following naming convention for Security Groups

     <TENANT>_<Where>_to_<Service>

For example:

Digile -tenant has rule from Digile premisis to PostgreSQL

	Name                             IP Protocol   To Port   IP Range
	-------------------------------- ------------- --------- -------------------
	DIGILE_Digile_to_PostgreSQL   tcp           5432      83.150.108.249/32

To list all the security groups for tenant run

    $nova secgroup-list

To list rules for security group run

    $nova secgroup-list-rules <secgroupName or id>

OpenStack projects
=============================================================

FORGE needs to generate certain usage statistics of IaaS usage. The
statistics contain separate reports for customer usage and all usage.
Customer usage reports must exclude all internal tenants. Therefore a
following naming convention for the internal tenant names must be
followed.

Internal tenant names must have one of the following strings as a prefix
or postfix (without asterisk) in the name of the tenant.

    digile*
    Digile*
    forge*
    Forge*
    *test
    test*
    demo*
    *Sandbox

E.g. digile-testing, forge-devel, plaza-test, plazatest, testplaza,
demoproject... are good names for the internal tenants.

Note! There is no need to change the current internal tenant names which
are in place 2015-02-12.

Statistics is available in
<http://analytics.forgeservicelab.fi:8080/birt-viewer/run?__report=forge_birt_reports/iaas.rptdesign&sample=my+parameter>\
 from the following networks.

-   digile
-   kainuunetu
-   csc

In order to have access from another network, send the IP-range to
(USERNAME REMOVED)

Securing FORGE
=================================================

In here we document the efforts to secure the infrastructure around
FORGE

Brief description of assests can be found at:
[Infrastructure_overview](2_Infrastructure.md#infrastructure-overview). As out machines
are RedHad-based operating systems, we followed\

<https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Security_Guide/sect-Security_Guide-Server_Security.html>

Strong passwords
-----------------------------------------------------

We have enforced the strong password policy for all user accounts. The
passwords are not stored as is but as hashes so DIGILE is not able to
read them.

Access to admin services only from whitelisted IPs
-------------------------------------------------------------------------------------------------------------------------

Access to SSH, OpenFire admin console, etc is allowed only from a set of
IP addresses. This is controlled at two places: the CSC firewall and the
iptables of the machine. Entries in CSC firewall can be requested, but
it takes some time and there's little control of it, e.g. not possible
to query the list of open ports or whitelisted IPs.

iptables on the machines are easier to control and show. It's possible
to create a custom chain in iptables. If we add all the ranges to the
chain, we can then re-use it for each admin service. I list currently
allowed ranges in /etc/sysconfig/iptables

    # list of IPS for which admin access to services is allowed.
    -N ADMIN_IPS

    # CSC office network
    -A ADMIN_IPS -s 193.166.1.0/24 -j ACCEPT
    -A ADMIN_IPS -s 193.166.2.0/24 -j ACCEPT
    # CSC VPN
    -A ADMIN_IPS -s 193.166.84.0/24 -j ACCEPT
    -A ADMIN_IPS -s 193.166.85.0/24 -j ACCEPT

    # DIGILE
    -A ADMIN_IPS -s 212.68.9.98 -j ACCEPT

    # Kainuun Etu
    -A ADMIN_IPS -s 213.145.192.0/24 -j ACCEPT
    # If source is none of those, DROP
    -A ADMIN_IPS -j DROP

    [..]
    # The chain can then be use for SSH as
    -A INPUT -m state --state NEW -m tcp -p tcp --dport 22 -j ADMIN_IPS

IPv6 firewall should follow the same logic at some point. At the moment,
it's only a few CSC people accessing the machines with IPv6.

    -N CSC
    -A CSC -s 2001:708:10:4008:a::/80 -j ACCEPT
    -A CSC -s 2001:708:10:4008:b::/80 -j ACCEPT
    -A CSC -s 2001:708:10:10::/80 -j ACCEPT
    -A CSC -j DROP

    -A INPUT -m state --state NEW -m tcp -p tcp --dport 22 -j CSC

SELinux
-----------------------------------

selinux is in enforcing mode on all the three machines. Few policies
were created, mostly in order to make mod\_passenger (ruby for redmine)
work okay.

Apache
---------------------------------

Apache is running on auth and support. It's serving CAS, password app,
and redmine.

-   mod\_evasive and mod\_security are enabled
-   ruleset from OWASP is used with mod\_security
    (<https://www.owasp.org/index.php/Projects/OWASP_ModSecurity_Core_Rule_Set_Project>)
-   DAV and autoindex modules disabled

then:

 ` ServerSignature Off ServerTokens ProductOnly TraceEnable Off`

### Resolving 403 in web applications behind Apache with mod\_security

If you attempt to GET or POST to a web app behind apache and you get 403
Forbidden, it is very likely that you have hit one of the regular
expressions in the OWASP ruleset. There is a huge amount of rules and
they for sure overlap with legit use-cases of, for example, redmine.

At the moment the applications behind Apache are:

-   Redmine on support.forgeservicelab.fi
-   Password changer on support.forgeservicelab.fi
-   CASino on auth.forgeservicelab.fi

If you submit something to Redmine and you get 403, the way to resolve
this is as follows:

-   ssh to support
-   go to /var/log/httpd
-   the HTTP request, response, and reason for rejection is logged
    in modsec\_audit.log. There's a timestamp which you can use to
    locate the log message for your request.

    -   example:

			[02/Dec/2013:17:13:15 +0200] Upyjh1YyGyUAAEtcgZMAAAAK 212.68.9.98 43053 86.50.27.37 443
			(...)
			Message: Access denied with code 403 (phase 2).
			Pattern match "(?i:[\"\\'].*?\\[ ]*(([^a-z0-9~_:\\'\" ])|(in)).+?\\()" at
			ARGS:content[text]. [file "/etc/httpd/modsecurity.d/activated_rules/modsecurity_crs_41_xss_attacks.conf"]
			[line "488"] [id "973334"] [rev "2"] [msg "IE XSS Filters - Attack Detected."]
			[data "Matched Data: 's use pre-provided components) 2. [[WordPr
			(...)

    The example shows that a rule from file
    */etc/httpd/modsecurity.d/activated\_rules/modsecurity\_crs\_41\_xss\_attacks.conf*
    line 488 denied your request. So you need to

			# go to line 488 in the file and comment out the rule (with "#")
			sudo vim /etc/httpd/modsecurity.d/activated_rules/modsecurity_crs_41_xss_attacks.conf
			# restart apache
			sudo httpd restart
	
Disabling unnecessary services
---------------------------------------------------------------------------------

CentOS has a few RPC daemons running, supposedly in order to make NFS
work. I had to stop them and remove their runlevel entries. Then there
are a few services, probably related to backups: cvd and EvMgrC.

Security scan
-----------------------------------------------

OpenVAS has been used to scan vulnerabilities of forge servers. Scan
reports are attached at the end of this wiki page.

-   git.forgeservicelab.fi
-   support.forgeservicelab.fi

Security updates
-----------------------------------------------------

The nodes are trying to install security updates every day:\

` [USERNAME REMOVED@auth:~] $ sudo crontab -l 4 3 * * * /usr/bin/yum -y update --security &> /tmp/yum-sec-update`

Vulnerability assessment reports
-------------------------------------------------------------------------------------

### 2013-10-10

-   OpenVAS vulnerability assessment was performed from inside
    the firewall. Finding has been filed as issues in Redmine
-   nmap port scan was performed from inside the firewall. No surprises
    were found.

SingleSignOn
=============================================

It would be nice to have Single Sign On between FORGE sites, including
Horizonm, the openstack dashboard.

The SSO tools always employ

-   a "login server" which is a third-party component connected to an
    authentication backend (LDAP, sql, /etc/shadow, ...)
-   an "application server" which is a web-server running a site with
    restricted access. The application server is usually implemented as
    web-server extension (in the super-cool case - apache module from
    distribution package). Sometimes, application server needs more,
    like e.g. shibboleth needs to run a separate daemon (shibd) and
    loads of xml configs.

When accessing a restricted resource, user is redirected to the login
server and shown a login page. When he successfully logs in, he is
redirected back to originally requested resource, or redirected to some
portal with available sites listed.

Possible candidates
-----------------------------------------------------------

-   CAS <https://wiki.jasig.org/display/CASUM/Home>

    -   CASino - <http://casino.rbcas.com/>
        -   even more cool then RubyCAS
    -   RubyCAS - RubyOnRails app that ascts as a login server -
        <https://github.com/rubycas/rubycas-server/wiki/Quick-Start>
        -   can't be worse than the reference implementation which is in
            Java
            <https://wiki.jasig.org/display/CASUM/Best+Practice+-+Setting+Up+CAS+Locally+using+the+Maven2+WAR+Overlay+Method>
        -   can be installed from gem. Can be deployed with webrick,
            or apache.
        -   easy - I managed to deploy it with users and passwds in SQL.
            I also deplyed two redmines that use it for auth.
-   Shibboleth <http://shibboleth.net/about/basic.html>

-   Pubcookie
    <http://www.pubcookie.org/docs/how-pubcookie-works.html>

    -   pubcookie uses symmetric keys for authenticating application
        servers in the login server - login server shares a private key
        with each of its application server.
    -   the login server runs as a xinetd "plugin"
    -   is packaged on CentOS: mod\_pubcookie, mod\_pubcookie-server
        (login templates with the xinetd plugin)

Discussion
-----------------------------------------

A meeting was held on 3.9.2013.

### Notes:

-   two categories of available SSO solutions: "single Identity-Provider
    SSO", "SSO with federation support"
-   picked implementetations from the two categoriess: CAS and
    shibboleth
-   CAS: <http://www.jasig.org/cas>. It's a java project. There's more
    lightweight imeplementation in Ruby:
    <https://github.com/rubycas/rubycas-server/wiki/Overview>
-   shibboleth: <http://shibboleth.net/>, a free implementations of the
    SAML standard. It's a federated identity solution.
-   main differences:
    -   effort to set up, shibbolet in weeks, CAS in days
    -   Shibboleth will allow us to authorize id from other corporations
    -   does this fit in FORGE approach: tech contact will be
        responsible for user creation for an affiliate
    -   it is possible to substitute one SSO system with another with
        not-so-much effort
    -   both implementations have good client (i.e.
        web-application side) support
    -   It is non-trivial to set up federation with another Identify
        Provider, paperwork
    -   Openstack dashboard does not support neither of them at
        the moment. Some support expected in Havana.

As an excutable script
========================================================================================

Basic usage
------------------------------------------------------------------

-   ssh to FORGE admin machine at forgeadmin.csc.fi
-   the tool is available in /usr/bin/local/forge\_ldap
-   **SORT OF IMPORTANT** In order to authorize to LDAP, you must
    provide your username and password. The util takes username from the
    "USER" environment variable. The USER env var is likely to be
    already set from your ssh session and hopefully it's the same as
    your ldap usename. Password will be asked on script start. If you
    don't want to be asked everytime, you can store your LDAP password
    it to \~/.ldappass (you might also want to chmod 600 \~/.ldappass).
    The script will read the password from \~/.ldappass.
-   run as *$ forge_ldap*, you will be presented with a shell where
    you can add users, groups, roles; handle membership, etc.
-   do "help" or "help &lt;command&gt;" to learn about available
    commands

Handling Users
------------------------------------------------------------------------

### add new user with login USERNAME

    (USERNAME REMOVED@FORGE_LDAP) $ newuser USERNAME
    Creating new user 'USERNAME':
    Given name(s) of the user:
    FIRSTNAME
    Surname(s) of the user:
    SURNAME
    Email of the user:
    USERNAME@gmail.com
    Mobile phone number for the user in theinternational format without spaces.
    E.g. xxxxxxxxx:
    +xxxxxxxx
    INFO: adding user {'givennames': 'FIRSTNAME',
    [...]

### list all users whose login starts with "t"

    (USERNAME@FORGE_LDAP) $ listusers cn=t*
    INFO: listing under ou=people,dc=forgeservicelab,dc=fi with filter cn=t*
    INFO: searching for ('ou=people,dc=forgeservicelab,dc=fi', 1, 'cn=t*', ['cn'])
    USERNAME
    testmanager
    [...]

### show details of user "USERNAME"

    (USERNAME@FORGE_LDAP) $ showuser USERNAME
    [...]

### add user "USERNAME" to group

    (USERNAME@FORGE_LDAP) $  addusertogroup USERNAME <developers|partners|partnerscra>

### find out to which users and roles user "USERNAME" belongs:

    (USERNAME@FORGE_LDAP) $  showusersgroups USERNAME
    [...]
    (USERNAME@FORGE_LDAP) $  showusersroles USERNAME
    [...]

### removing user "USERNAME"

Before you remove user, you should first\
 1. remove him from all the roles he occupies\
 2. remove him from all the groups he occupies

The tool will complain if user has any roles or group membership left.

    (USERNAME@FORGE_LDAP) $ removeuserfromrole  USERNAME member jokegroup
    (USERNAME@FORGE_LDAP) $ removeuserfromrole  USERNAME admin  jokegroup
    (USERNAME@FORGE_LDAP) $ removeuserfromgroup USERNAME jokegroup
    (USERNAME@FORGE_LDAP) $ removeuser USERNAME

You can also remove the roles and groups straight away.

Handling Groups
--------------------------------------------------------------------------

### add new group with id testgroup

If you select the group to be an openstack tenant, the "member" and
"admin" roles will be created and the technical contact will be added to
the "member" role.

    (USERNAME@FORGE_LDAP) $ newgroup testgroup
    Creating new group 'testgroup':
    Organization name:
    Test Org Inc.
    Business ID:
    000000-00
    Postal address in one line:
    ADDRESS
    Please enter username of technical contact user.User must already exist:
    USERNAME
    Do you want this group to be an openstack tenant? y/[n]:
    y
    Name and surname of administrative contact:
    FIRSTNAME SURNAME
    email of administrative contact:
    USERNAME@DOMAIN
    Mobile phone number of the administrative contact:
    +xxxxxxxx
    INFO: adding group {'address': 'ADDRESS',
     'admin_contact_mail': 'USERNAME@DOMAIN',
    [...]

### show details of group "csc"

    (USERNAME@FORGE_LDAP) $ showgroup csc
    [...]

### removing group "jokegroup"

You can remove group no matter how users it has in. If the group has
member and admin roles below, these roles will be removed too.

 ` (USERNAME@FORGE_LDAP) $ removegroup jokegroup`

Consistency check
------------------------------------------------------------------------------

We have several constraints in the db, like that all users belonging to
a partner organization must be in the role-group "partners". There is a
command that verifies this - "consistencycheck".

As a Python module
================================================================================

Just "import forge_ldap" iny your script. To understand how to use it,
just see the test.py script in the git repo, or see how the Cmd object
is using it.

Virtual instance duplication
===========================================================================================

Important notice
-------------------------------------------------------------------

This is an extremely unorthodox practice and it is highly recommended to
**NOT** use it unless it becomes a last resort.

This procedure copies *EVERYTHING* from a running instance into
another.

Rationale
-----------------------------------------------------

Openstack does not allow resizing instances to flavors that have smaller
root disk sizes. However it is possible to create a blank instance of
the desired smaller flavor and copy the filesystem tree from the live
instance that was intended to be resized down, this all *provided that
the data on the source instance fits on the new smaller target
instance*.

To do this, follow these steps.

Procedure
-----------------------------------------------------

### Target image instantiation

It is of the utmost importance to make sure that the new instance has
the exact same base image as the instance that we want to size down.
This will minimize the impact of copying system files from the source
instance into the target.

Once the base image of the source instance is found out, we can
instantiate the target from that same image on the desired smaller
flavor.

### Source preparation

We are going to rsync almost everything on the filesystem tree of the
source instance from the target instance, therefore we need to ensure we
can access the source as root.

-   Edit `/etc/ssh/sshd_config` to enable root login, make sure to set
    the `PermitRootLogin` as follows:

		PermitRootLogin    without-password

-   The `root` user is configured by cloud-init to prevent ssh logins,
    edit `/root/.ssh/authorized_keys`:
    -   Comment out or remove the first line containing
        `no-port-forwarding,no-agent-forwarding,no-X11-forwarding,command="echo 'Please login as the user [...]`
    -   Add the public key of the user that's going to perform the sync

### Target preparation

We also need to get root privileges on the target instance, there's two
ways to go about this:

1.  Generate a keypair for the root user, and use that to log in to the
    source instance
2.  Allow sudo to get access to the SSH\_AUTH\_SOCKET thus giving root
    access to a standard user's ssh agent. To do this:
    -   Create `/etc/sudoers.d/ssh_auth_sock`
    -   Add the line `Defaults set_env+=SSH_AUTH_SOCK` to it
    -   Set its mode to 0440 with
        `chmod 0440 /etc/sudoers.d/ssh_auth_sock`

### Data transfer

On the target instance run:

    sudo rsync -aAxv --exclude{"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} root@<source>:/* /

Reboot the target instance and verify that all works as expected.

XMPP adminstration
=============================================================

This page describes configuration of the Openfire XMPP server.

Openfire is installed on support.forgeservicelab.fi in /opt/openfire.

It can be managed from administration console at
<https://xmpp.forgeservicelab.fi:9091>. It's connected to LDAP - ask
(USERNAMES REMOVED) to get admin privileges.
