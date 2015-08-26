Infrastructure
=================================================

![FORGE support services deployment
diagram](/files/saas.png "FORGE support services deployment diagram")

![FORGE computing services deployment
diagram](/files/iaas.png "FORGE computing services deployment diagram")

Admin node
=====================================

Admin node is at <URL REMOVED> and its purpose is to be the
centralized point for administrative tasks in Forge.

The tasks that should be done on it:

-   User and group adding
-   quota management
-   default network creating

Installation
-----------------------------------------

The admin node is described with ansible role and playbook.

The playbook is at
<https://git.forgeservicelab.fi/ansible/admin_config/tree/master>

The role is at <https://git.forgeservicelab.fi/ansible-roles/admin_node>

To spawn a admin node, one should get a machine where he can ssh, clone
the playbook, get the roles on which it depends, create secrets.yml in
the directory of the playbook, containing gitlab_private_token to read
the ssh_keys repo, e.g.

    gitlab_private_token: PRIVATETOKEN

which is a token for the "keyreader" account.

Check the playbook to tune details, e.g. installed users.

And then in the playbook directory:

    $ ansible-playbook -s -e "h=<node_ip>" main.yml

Barebone node
==============================================

There is a barebone Ubuntu server in DIGILE premises.

Specs
------------------------------

DIGILE-SERVER-01

-   1 x HP ProLiant ML350p Gen8 - Xeon E5-2609V2 2.5 GHz
-   1 x Intel Xeon E5-2609V2 - 2.5 GHz - 4 cores-10 Mt cache
-   8 x HP - RAM - 16 Gt - DIMM 240-pin - DDR3
-   3 x HP Enterprise - Hard disk- 600 Gt - hot-swap - 2.5" SFF - SAS-2
-   3 x HP Common Slot High Efficiency - power supply
-   1 x UPS 5PX3000IRTN Eaton 5PX RT 2U 3000 VA / 2700 W Netpack
    (tehdasasennettu SNMP-kortti)


External IP Address: 83.150.108.249 (Internal IP Address: 172.17.210.139)

 OS: Ubuntu Server 14.04 LTS
 Account: digile , this account has Sudo -rights
 Password: Ask (USERNAMES REMOVED)
 Open firewall rules: SSH

Function
------------------------------------

This server can act as a video editor station and is configured for RTM
real time audio transmission over 1Gbps ethernet and remote X (e.g. via
Xephyr)

This is FORGE's data warehouse for the filesystem and databases of:

-   Digile's dbserver (Redmine and Gitlab databases)
-   Forgeservicelab.fi (Plaza)
-   Gitlab repositories
-   Jenkins configuration and job definitions
-   Insightly
-   Performance reports for Plaza (devel, testing, production)

UPS
--------------------------

This server is connected to an Eaton 5PX UPS to ensure continuous
operation. The UPS web interface is available on
<http://172.17.210.130>
 The UPS's power outlets group1 and group2 are both connected to the
barebone server as complementary power sources.

The UPS is monitored from Ubuntu via NUT and configured to gracefully
shut down upon receiving a low battery alert.
 The server's BIOS is configured to boot the system upon power
resumption.

### Power Race condition

The typical power drain shutdown and resume chain happens as follows:

    Loss of main power -> Low battery alarm -> server shutdown -> UPS shutdown -> power resumption -> server boot

In the corner case where the main power returns between server shutdown
and UPS shutdown, the UPS will not cut power to outlet groups 1 and 2,
therefore the server's BIOS will not detect a power shortage (because it
never really happened) and understand that the server was purposefully
shut down and won't boot.

In this case, it is possible to remotely accessing the UPS Control
interface on <http://172.17.210.130>, cutting power to the outlet groups
1 and 2 and then resuming it, thus triggering a power shortage on the
server and causing the BIOS to boot it up.

![UPS
Control](/files/Screenshot_from_2015-01-15_14_20_49.png)

ComponentOwnership
==============================================================

Component ownership gives insight to responsibilities of different
parties involved in Forge. There acually is a (RACI)
Responsible-Accountable-Consuled-Informed) matrix which assigns parts of
FROGE to the involved parties, but it is rather general. The RACI matrix
document is an appendix of CSC's LVM contract.

This resource might serve as a simple pointer to a responsible person in
case of component malfunction or improvement suggestions.

	Component         Owner         Contact
	----------------- ------------- ---------------------
	OpenStack         CSC           
	Openfire (XMPP)   Digile        
	Redmine           Kainuun Etu   
	Git               Digile        

References
----------------------------------------------

^\[1\]:^ Sections 2.1.2 and 2.5 in Digile-Kainuun Etu contract.

Identity management
================================================================

-   [Openstack new ldap](#openstack-new-ldap)

This page captures three main aspects of the identity management in
FORGE:

-   how we create identity entities
-   LDAP scheme so that it's understandable by oenstack
-   mapping of data from contracts to LDAP, so that we have clear
    understanding how to create entries

Specifications
======================================================

What data we have from the contract
------------------------------------------------------------------------------------------------

-   Technical and administrative contacts: name, surname, email, mobile
    phone
-   Organization: business ID, name of organization, postal address
-   Contract type: Service Developer, Partner, Partner with CRA

What data we need for which resources
----------------------------------------------------------------------------------------------------

-   **for user**
    -   name, surname, email, mobile phone
    -   we have to create a login string (not necessary for
        administrative contact)
    -   initial type: Service Developer, Partner, Partner with CRA
-   **for organization**:
    -   technical and administrative contact details (twice the set of
        data for user), name of organization, business ID, postal
        address
    -   we have to create a group id string
    -   initial type: Service Developer, Partner, Partner with CRA

Creating new user and new organization
------------------------------------------------------------------------------------------------------

Moved to [Resource_Allocation_Process](3_OperationalGuides.md#resource-allocation-process)

Schemes descriptions
==================================================================

![LDAP](/files/LDAP.png)

Users
------------------------------------

-   under ou=accounts
-   we use the inetOrgPerson class for users
-   cn is the login
-   attributes that must be filled are: mail, mobile, cn, sn, givenName,
    displayName (givenName + sn), userPassword
-   the user must be able to receive messages and calls on the mobile
    phone number
-   userPassword hash is SSHA
-   insightly contact ID goes on the employeeNumber attribute
-   example:

		dn: cn=USERNAME,ou=people,dc=forgeservicelab,dc=fi
		objectClass: top
		objectClass: inetOrgPerson
		cn: USERNAME
		mail: someone@org.com
		mobile: PHONENUMBER
		givenName: NAME
		sn: Hnen
		displayName: NAME
		employeeNumber: 1234567
		userPassword::  PASSWORD

Projects
------------------------------------------

-   are under ou=projects,dc=forgeservicelab,dc=fi
-   we use the groupOfNames for projects
-   group id is in "cn"
-   group members are listed by distinguished names in "member"
    attributes
-   dn of technical contact account goes on the "owner" attribute of the
    entry
-   dn of administrative contact accounts go on the "seeAlso" attributes
    of the entry
-   insightly project ID goes to "o" attribute
-   customer groups must have description attribute "type: "

Tenants
----------------------------------------

-   are children of the project they are related
    to (cn=tenant,cn=project,ou=projects,dc=forgeservicelab,dc=fi)
-   we use the groupOfUniqueNames for tenants
-   tenant members are listed by distinguished names in the
    "uniqueMember" attributes

### Business info

This is CRM information that has no impact on identity operations, it is
therefore not stored on LDAP.

Roles:
-------------------------------------

Roles in ou=roles are used to group accounts regarding their access
privileges

### LDAP_administrators

These are the accounts allowed to modify LDAP entries

    dn: cn=LDAP_administrators,ou=roles,dc=forgeservicelab,dc=fi
    objectClass: top
    objectClass: organizationalRole
    cn: LDAP_administrators

### Special groups

These are dynamically created groups (static `groupOfNames`, regularly
synced from `groupOfURLs` dynlists) under the roles tree
(ou=roles,dc=forgeservicelab,dc=fi)

-   **developers**

    -   Users belonging to a project with type:SDA, a tenant of a
        project with type:SDA, the Digile project, or the Digile.SBD
        project should be here
    -   This group grants access to gitlab
-   **partners**:

    -   Users belonging to a project with type:FPA should be here
-   **partners_cra**:

    -   Users belonging to a project with type:FPA (CRA) should be here
-   **technical_contacts**:

    -   The technical contacts of all projects should be listed here

**DEPRECATED**
==================================================

Schemes descriptions
====================================================================

Users
--------------------------------------

-   under ou=people
-   we use the inetOrgPerson class for users
-   cn is the login
-   attributes that must be filled are: mail, mobile, cn, sn, givenName,
    displayName (givenName + sn), userPassword
-   the user must be able to receive messages and calls on the mobile
    phone number
-   userPassword hash is SSHA
-   example:

		dn: cn=USERNAME,ou=people,dc=forgeservicelab,dc=fi
		objectClass: top
		objectClass: inetOrgPerson
		cn: USERNAME
		mail: someone@org.com
		mobile: PHONE
		givenName: NAME
		sn: Hnen
		displayName: NAME
		userPassword::  PASSWORD

General Groups
------------------------------------------------------

-   are under ou=groups,dc=forgeservicelab,dc=fi
-   we use the groupOfNames for groups
-   groups are affiliates and in effect tenants in Openstack.
-   we do not support group of groups
-   group id is in "cn", and in "ou"
-   group members are listed by distinguished names in "member"
    attributes
-   dn of technical contact account will go to the "owner" attribute of
    the entry
-   full name can go to "o" attribute
-   customer groups must have description attribute "contract_type: "
-   if group should be an openstack tenant, it should have a decsription
    attribute with string "openstacktenant"
-   =&gt; a group with "contract_type:parter" will not have the
    "openstacktenant" description attribute

### Adminsitrative contact and business info

-   As we need to store more information for an organization than the
    groupOfNames objectclass offers, we store that information in
    description attributes. A record can have more description
    attributes, and we can just prefix the value with field name.
-   thus, business_id value 111111-11 will be stored in a group record
    as *description: business_id:111111-11*
-   analogically, there will be fields:

    -   business_id
    -   address
    -   admin_contact_name
    -   admin_contact_mobile
    -   admin_contact_mail
-   brief example would then be:


		# testgroup, groups, forgeservicelab.fi
		dn: ou=testgroup,ou=groups,dc=forgeservicelab,dc=fi
		objectClass: groupOfNames
		cn: testgroup
		owner: cn=USERNAME,ou=people,dc=forgeservicelab,dc=fi
		o: Test Org Inc.
		member: cn=USERNAME,ou=people,dc=forgeservicelab,dc=fi
		description: openstacktenant
		description: contract_type:service_developer
		description: business_id:000000-00
		description: address:ADDRESS
		description: admin_contact_name:NAME
		description: admin_contact_mail:EMAIL
		description: admin_contact_mobile:PHONE
		ou: testgroup


Special groups
--------------------------------------------------------

-   **developers**

    -   Users belonging to a group with
        contract_type:service_developer should be here
    -   This group grants access to gitlab
-   **partners**:

    -   Users belonging to a group with contract_type:partner should be
        here
-   **partnerscra**:

    -   Users belonging to a group with
        contract_type:partner_with_cra should be here

Roles:
---------------------------------------

-   roles in ou=roles are used only for the OpenStack context (admin and
    member role), and for admin access to LDAP (the "admin" role)
-   roles are the means to assign different privileges to different
    users in the same group (in a tenant/affiliate)
-   the technical contact and the administrative contact roles are
    already captured in the group attributes
-   declaration in the top scope next to people and groups

    `ldap dn: cn=admin,ou=roles,dc=forgeservicelab,dc=fi objectClass: top objectClass: organizationalRole cn: admin`

-   definition under a group

		dn: cn=admin,cn=csc,ou=groups,dc=forgeservicelab,dc=fi
		objectClass: top
		objectClass: organizationalRole
		cn: admin
		roleOccupant: cn=USERNAME,ou=people,dc=forgeservicelab,dc=fi

### "The role of roles in OpenStack"

-   roles are used by openstack to assign different privileges (within
    a tentant) to different users
-   with the v2 API in Grizzly release, role "admin" within a tenant
    will give user admin privileges across all openstack. **We don't
    want to assign user accounts to the admin role in any group.**
-   in order to use openstack, user must have the member role. The
    member role allows to do everything within a tenant.
-   knowing this, what we should do is then:
    -   give the role "admin" only to super-users (CSC, KE, Digile)
    -   give the role "member": technical contact and other
        affiliate users. Members can do most of user-tasks in
        Openstack - run vms, upload images, assign floating ips, etc.
-   privileges for different roles can be customized in policy file for
    each openstack component
-   Defaults for Grizzly:
    -   nova:
        <https://github.com/openstack/nova/blob/stable/grizzly/etc/nova/policy.json>
    -   keystone:
        <https://github.com/openstack/keystone/blob/stable/grizzly/etc/policy.json>
    -   neutron:
        <https://github.com/openstack/neutron/blob/stable/grizzly/etc/policy.json>

Openstack new ldap
=============================================================

Openstack notes on moving to auth2.

Moving OpenStack to use the auth2 server will bring some changes in the
usermanagement process. LDAP-wise, the biggest change is removing the
role information from LDAP.

Originally OpenStack users, projects and roles came from LDAP. After the
change users and groups come from LDAP, projects and roles come from
SQL.

Group is a new concept, it's just a group of users. Groups can be mapped
to projects in OpenStack.

Here are some examples of workflows. Since this uses the v3 keystone
api, you will need the new openstack cli instead of the keystone cli.
Recommended way to install is in a virtual environment from git.

Virtual environments

<http://www.pythonforbeginners.com/basics/how-to-use-python-virtualenv>
 openstack-client from git
 <http://git.openstack.org/cgit/openstack/python-openstackclient>

**Important**: Changes to your openrc file. Change the OS_AUTH_URL to
point to the v3 endpoint, and add the identity api version
 export OS_IDENTITY_API_VERSION=3
 export OS_AUTH_URL=<https://cloud.forgeservicelab.fi:5001/v3>

Now the process will look like
 New group + user
 1) User + group is created in LDAP.
 2) Project is created in Keystone, same name as group
 - openstack project create projectname
 3) Group is given a member role in the project in Keystone
 - openstack role add --group projectname --project projectname member

Add user to project
 1) User is added to group in LDAP
 2) Everything else should work, since the group is already mapped

Adding admin role to an admin
 1) User is given admin role to project in Keystone
 - openstack role add --user username --project projectname admin

Note!
 Admin management will change away from group role based to domain based
at some point. We'll make this change later so we don't change too many
things at once.

Infrastructure overview
============================================================================

This page gives an overview of our infrastructure besides OpenStack.
OpenStack is documented at
[ForgeOpenstackComponents](#forge-openstack-components).

Hosts
----------------------------------------

We currently have ~~3~~ 2 vms from CSC cloud, those are

-   auth2.forgeservicelab.fi - CentOS 7, LDAP server (openldap), CAS for
    SSO (RubyCAS behind apache), IdP (simpleSAMLphp behind apache),
    password changing php app.
    -   runs LDAP master
    -   synced slaves on two Keystone nodes to save traffic and remove
        SPOF for Openstack
-   ~~support.forgeservicelab.fi - CentOS 6.3, runs Redmine for issue
    tracking (behind apache), wiki and documentation; openfire for XMPP;
    and password changing php app.~~
-   ~~git.forgeservicelab.fi - CentOS 6.4, GitLab (behind nginx).~~
-   forgeadmin.csc.fi - CentOS 6.5, admin machine

### Backups

The hosts are backed up by our friends in CSC. Every night a filesystem
snapshot is taken. History is kept for 3 months.

List of hosts and services
----------------------------------------------------------------------------------

| Environment | Service | FQDN | IP | Port | other |
|-------------|---------|------|----|------|-------|
| Production | Plaza (live LB) | forgeservicelab.fi | 193.166.24.185 | 443 | |
| Production | Drupal | drupal01.forgeservicelab.fi | 86.50.28.4 | 443 | |
| Production | Drupal | drupal02.forgeservicelab.fi | 86.50.28.5 | 443 | |
| Production | Plaza MySQL (service IP) | mysql.forgeservicelab.fi | 86.50.28.9 | 3306 | |
| Production | Plaza MySQL (server 1) | mysql01.forgeservicelab.fi | 86.50.28.2 | 3306 | |
| Production | Plaza MySQL (server 2) | mysql02.forgeservicelab.fi | 86.50.28.3 | 3306 | |
| Production | Plaza NFS (service IP) | nfs.forgeservicelab.fi | 86.50.28.8 | | |
| Production | Plaza NFS (server 1) | nfs01.forgeservicelab.fi | 86.50.28.6 | | |
| Production | Plaza NFS (server 2) | nfs02.forgeservicelab.fi | 86.50.28.7 | | |
| Production | CASino | auth2.forgeservicelab.fi | 86.50.28.78 | 443 | |
| Production | LDAP | auth2.forgeservicelab.fi | 86.50.28.78 | 636 | |
| Production | phpLDAPadmin | auth2.forgeservicelab.fi | 86.50.28.78 | 8443 | |
| Production | SimpleSAMLphp | idp.forgeservicelab.fi | 86.50.28.78 | 443 | |
| Production | Jenkins | ci.forgeservicelab.fi | 193.166.24.197	| 443 | |
| Production | Postgresql | dbserver.forgeservicelab.fi | 193.166.24.112 | 5432 | |
| Production | KaPA secure server | forgess00.forgeservicelab.fi | 193.166.25.26 | 443 | 4000 |
| Production | GitLab | git.forgeservicelab.fi | 193.166.24.105 | 443 | 10022 |
| Production | Nagios | nagios.forgeservicelab.fi | 193.166.24.126 | 443 | |
| Production | Redmine | support.forgeservicelab.fi | 193.166.25.157 | 443 | |
| Production | Openfire | xmpp.forgeservicelab fi | 193.166.25.157 | 5222 | 9091 |
| Testing     | Redmine | support-test.forgeservicelab.fi | 193.166.24.138 | 443 | |
| Testing | KaPA secure server | forgess00-test.forgeservicelab.fi | 193.166.24.117 | 443 | 4000 |
| Testing | GitLab | gitlab-test.forgeservicelab.fi | 193.166.24.210 | 443 | 10022 |
| Testing | CASino | testauth.forgeservicelab.fi | 193.166.25.240 | 443 | |
| Testing | LDAP | testauth.forgeservicelab.fi | 193.166.25.240 | 636 | |
| Testing | phpLDAPadmin | testauth.forgeservicelab.fi | 193.166.25.240 | 8443 | |
| Testing | SimpleSAMLphp | testidp.forgeservicelab.fi | 193.166.25.240 | 443 | |
| Testing | Openfire | xmpp-test.forgeservicelab.fi | 193.166.24.138 | 5222 | 9091 |
| Development | Plaza (live LB) | devel.forgeservicelab.fi | 193.166.24.150 | 443 | |

Services
----------------------------------------------

DIGILE ltd. has asked from pineroot ltd. to assess its uses of FOSS from
a compliance perspective and to make recommendations with the goal to
ensure ongoing compliance in the FORGE Service Lab activities. The
results are described in the [Due_diligence](3_OperationalGuides.md#due-diligence) and the
components listed below were provided as an input for the assessment.

| service name | exposure | port number/s | details | version,licence |
|----- | ---- | -----| ----- | ----- |
| LDAP  | support,git,Keystone slaves,Plaza | 636 | master on ldaps://auth.forgeservicelab.fi | openldap-2.4.23,OpenLDAP |
| gitlab 7.9  HTTPS | everywhere | 80,443 | git.forgeservicelab.fi [[GitLabAdministration]] | gitlab-6.2,MIT |
| gitlab 7.9  SSH access | everywhere | 10022 | git.forgeservicelab.fi [[GitLabAdministration]] | gitlab-6.2,MIT |
| CAS SSO  | everywhere | 80,443 | CASino over HTTPS auth.forgeservicelab.fi:/var/www/casino | casino-2.0.2,MIT |
| Redmine 2.6.3  | everywhere | 80,443 |support.forgeservicelab.fi:/opt/redmine | redmine-2.6.3,GNU GPL v2 |
| Self-service password | everywhere | 80, 443 | auth.forgeservicelab.fi:/var/www/html/password | rubycas-server-1.1.3,MIT |
| Openfire XMPP client to server | everywhere | 5222 | support.forgeservicelab.fi:/var/lib/openfire | openfire-3.10.0,Apache license v2.0 |
| Openfire admin console | ADMIN_IPS | 9091 | https://xmpp.forgeservicelab.fi:9091, support.forgeservicelab.fi:/var/lib/openfire  | openfire-3.10.0,Apache license v2.0 |
| SSH | ADMIN_IPS | 22 | /etc/ssh/sshd_config | openssh-5.3,Simplified BSD License |
| Plaza | Load balancer everywhere, rest to tenant network | 443 | [[Plaza_cluster_architecture]] | drupal-7.25,GNU GPL v2 or later |
| OpenStack | everywhere | 80,443 | cloud.forgeservicelab.fi | Icehouse, Apache License 2.0 |
| Ubuntu | OpenStack |  | Virtual disk image from https://cloud-images.ubuntu.com/ | 14.04, Free software licenses (mainly GPL) according to licencing policy http://www.ubuntu.com/about/about-ubuntu/licensing |
| CentOS | OpenStack |  | Virtual disk image, built by DIGILE according to http://docs.openstack.org/image-guide/content/centos-image.html | 6.5, Free software (GPL and other licenses) |
| Debian | OpenStack |  | Virtual disk image, built by DIGILE | 7.7, Free software licenses according to Debian Free Software Guidelines (DFSG) |

Port 80 is open only to be forwarded by the app to 443. In apache it's a
rewrite rule:

    RewriteEngine On
    RewriteCond %{HTTPS} off
    RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI}`

Same thing on nginx:

    server {
        location / {
            return https://$host$request_uri;
        }
    }

LDAP management
------------------------------------------------------------

### Restore from backup

We have auth filesystemp snapshot and backed-up from CSC. To restore
OpenLDAP db, you will need a snapshot of /var/lib/ldap. That contains
bdb files of LDAP database. You will need to export the database in the
LDIF format. You can do that with slapcat. To point slapcat to your
restored directory (e.g. in /root/ldap), you must create a dummy
slapd.conf file, for example by "cp
/usr/share/openldap-servers/slapd.conf.obsolete dummy.slapd.conf". Then,
change the "directory" directive to point on the restored direcotry, in
our case to /root/ldap. Then "slapcat -f dummy.slapd.conf &gt;
dump.ldif" will dump thre restored db to ldif format. The data can then
be loaded by "slapadd -c -l dump.ldif", when slapd is turned down.

It is good idea to restore the records in order:
 1. Users
 2. Groups
 3. Roles

Run the slapadd first for users, then for group and then for roles. If
you run all at once, you will probably miss oem roles and some group
members. It is because if a group is restored before a member user, it
will not add the dn of the nonexistent user, because members are
distinguished DNs and are checked for existence.

### Creating and deleting records

~~The access control list for the LDAP records is under cn=config tree
in attributes olcAccess of olcDatabase={2}bdb,cn=config.~~
 The current (29/04/2015) ACL is

    access to attrs=userPassword
                    by self write
                    by dn.base="cn=Manager,dc=forgeservicelab,dc=fi" write
                    by group/organizationalRole/roleOccupant="cn=ldap_admins,ou=roles,dc=forgeservicelab,dc=fi" write
                    by dn.base="cn=pwdchanger,ou=accounts,dc=forgeservicelab,dc=fi" write
                    by dn.base="cn=syncer,ou=accounts,dc=forgeservicelab,dc=fi" read
                    by anonymous auth
                    by * none
    access to *
                    by self write
                    by dn.base="cn=Manager,dc=forgeservicelab,dc=fi" write
                    by group/organizationalRole/roleOccupant="cn=ldap_admins,ou=roles,dc=forgeservicelab,dc=fi" write
                    by users read
                    by * none

As shown, to edit records of other users in LDAP, one should occupy the
admin role (cn=ldap_admins, ou=roles, ..). ~~Only Manager can edit the
admin role, so one has to login as Manager in LDAP client and edit it.~~

### LDAP synchronization

LDAP is the central user info repository for Forge. This means that
openstack will also use it. To make openstack use it, LDAP is replicated
from the server locally to each fronted running keystone at CSC.

LDAP Syncrepl is used to pull the data from the master to the slaves.

-   Synced every 10 mins
-   Separate sync account with full read access used for this
-   Firewall ports opened to the cloud API machines
-   Client side sync configured using the torial-ldap puppet module.
    Config in CSC's puppet git.

Monitoring and analytics
===============================================================================

Monitoring
---------------------------------------------------

### Nagios monitoring

<http://nagios.forgeservicelab.fi/nagios/>

Nagios files a "Nagios" category bug in Redmine in Digile project when
it detects exceeded tresholds. The bug is automatically assigned to
FORGE QA. Nagios also closes the bug when it detects the situation is
back to normal.

### New Relic monitoring (DEPRECATED)

-   we are using NewRelic for monitoring of the FORGE infrastrucutre:
    <https://rpm.newrelic.com>
-   account to log in: <admin@forgeservicelab.fi>, password:
    PASSWORD
-   Gitlab availability monitoring:
    <https://rpm.newrelic.com/accounts/455523/applications/2839837/ping_targets>
-   the three servers are monitored for the basic stats: CPU
    utilization, disk I/O utilization, amount of free RAM, fullest disk
    free capacity
-   gitlab and redmine are monitored for availability
-   the user interface is quite intuitive
-   Alerts are sent to <admin@forgeservicelab.fi>

Analytics
-------------------------------------------------

FORGE Service Lab has two systems in use for analytics. Google Analytics
and Piwik. Services analysed are support.forgeservicelab.fi,
git.forgeservicelab.fi and forgeservicelab.fi.

### Google Analytics

GA is maintained by Google and it is accessible in
<http://www.google.com/analytics/> and after you select "Access Google
Analytics". Accessing the service requires Digile account. Admins:
(USERNAMES REMOVED).
Note! the FORGE web pages are not tracked anymore in GA so it's
recommended to use Piwik instead.

### Piwik

Piwik analytics server is maintained by FORGE Service Lab and it is
accessible in <https://analytics.forgeservicelab.fi/piwik> . Accessing
the service requires an FORGE account and access is possible only from
DIGILE office and VPN networks. Piwik is deployed using forge-piwik
playbook <https://git.forgeservicelab.fi/forge/forge-piwik>

BI Reporting
-------------------------------------------------------

FORGE Service Lab maintained analytics server that is running in
analytics.forgeservicelab.fi has a BIRT viewer service on Apache Tomcat.
The service is capable of visualizing BI reports created with Eclipse
BIRT. There are several BI reports available and they are accessible
without credentials from DIGILE office network and DIGILE vpn. BI
reporting system is deployed using forge-birt-reports-ansible playbook
<https://git.forgeservicelab.fi/ansible/forge-birt-reports-ansible>. The
playbook supports deploying BI report designs separately to the BI
environment deployment.

-   FORGE project issues from Redmine:
    <http://analytics.forgeservicelab.fi/birt-viewer/run?__report=forge_birt_reports/forge_status.rptdesign&sample=my+parameter>
-   FORGE IaaS reports:
    <http://analytics.forgeservicelab.fi/birt-viewer/run?__report=forge_birt_reports/iaas.rptdesign&sample=my+parameter>

FORGE project issues reports are generated from the backup database.
FORGE IaaS reports are generated from the datawarehouse that is in
analytics.forgeservicelab.fi. The datawarehouse is a postgresql iaas
database and is being populated with new data every day at 21.00. The
following cronjob of USER user adds previous day's data every day at
21.00.

    0 21 * * *      cd ~USER/bin/resource-usage-reporting; ./report_to_db.sh >> ./report_to_db.log 2>&1


FORGE OpenStack components
=====================================================================================

Openstack Components & configurations

Overview
-------------------------------------------------

Please note that this picture is only approximate. Not all network
connections are visible, nor are VLANs within the network. This is just
to convey the general architecture.

Components
-----------------------------------------------------

![Forge components](/files/Forge-components.png)

### Identity

-   Keystone using LDAP backends
-   SSL directly in keystone
-   (most likely not PKI tokens)

### Nova-API

-   SSL provided by apache proxypass
-   Nova and EC2 APIs enabled

### Compute

-   Nova compute with KVM
-   Libguestfs for key injection
-   Running images on shared NFS (on equalogic)
-   Network and disk exposed as virtio devices
-   VNC remote consoles

### Neutron (service)

-   Per network VLANs
-   Overlapping IP's allowed
-   Private addresses by default for VMs
-   SSL provided by apache proxypass

### Neutron net components

-   Linuxbridges + linux network namespaces
-   Per-tenant external routers
-   Metadata service proxying

### Neutron compute components

-   Neutron-linuxbridge-agent (linuxbridges)

### block storage (Cinder)

-   Equalogic backends for block storage
-   SSL provided by apache proxypass

### Object storage (Swift)

-   Swift with 4 backend nodes (gross 12*3TB storage per node)
-   Swift fontends on shared frontends
-   Swift and S3 apis enabled
-   Swift SSL with apache proxypass

### Image storage (Glance)

-   Glance with storage on the NFS backend
-   SSL provided by apache proxypass

### PKI management (nova cert)

### Apache

-   Handles SSL proxying for most services

Service deployment
---------------------------------------------------------------------

Services run on two frontend machines. The services are split into two
VM pairs. VM pairs are in an active/passive HA setup, controlled by
Pacemaker.

### Pair 1 (API nodes)

-   DRBD (mirrored network disks)
    -   Used for persistent data
-   Nova
-   Neutron (service)
-   Glance
-   Cinder
-   Swift proxy
-   Apache

-   Keystone

-   Horizon

-   QPID

-   Nova cert

-   MySQL

### Pair 2 (Network nodes)

-   Neutron-dhcp-agent
-   Neutron-l3-agent
-   Neutron-linuxbridge-agent
-   Neutron-metadata-agent

### The compute nodes

-   Nova-compute
-   Neutron-linuxbridge-agent

### Swift backend nodes

-   Swift container, account and object servers

Status of the Services
-----------------------------------------------------------------------------

-   [Status page](#openstack-status) - which OpenStack components are ready
    to be tested and used?

Hadoop nodes
===========================================

This page contains general information about using the HP SL4540 nodes
as hypervisors for OpenStack.

Hardware
-----------------------------------

The hardware for the hadoop cluster consists of 4 HPSL4540 chassises.
Each chassis contains 4 servers, which gives us 12 servers in total.

Server specs

	* 20 core intel cpu
	* 192 GB of memory
	* Mirrored OS disks
	* Dual 10gbit NICs
	* HP P420 controller with 7*4TB disks
	* HP P420 controller with 8*4TB disks

Both controllers are configured to have one RAID5, with 6+1 and 7+1
disks respectively. These arrays are used as physical volumes for one
large LVM volume group.

OpenStack specifics
---------------------------------------------------------

OpenStack has different ways of using local storage disk for virtual
machine images. The default is to have each VM disk as a file on a local
filesystem. This is simple, but also adds overhead due to an extra
filesystem in all IO operations.

The other option is using logical volumes as the VM backing disks. This
means that a logical volume is automatically created from an existing
volume group when a machine is launched.

There are some limitations with using the OpenStack LVM driver.

### Striped Volumes

OpenStack only supports linear volumes, not striped volumes. This means
that one backing physical volume is filled up before using the next. In
situations with multiple physical volumes it means that in most cases
only one backend device is used when doing IO operations. This
significantly reduces IO throughput. Using striped volumes both physical
disks must be used equally. This means that in our case one of the disks
of the 7+1 disk RAID5 array is wasted, but considering the performance
boosts of striped volumes, this should be acceptable.

### Disk zeroing

The second limitation is that for security the logical volume is written
full of zeroes when a VM is killed. This guarantees that the next VM
will not be able to read any old data from the disk. With 40+ TB of
storage zeroing the disk can take 12-24 hours. OpenStack has support for
"sparse volumes" that do not leak data in the same way, and the zeroing
could be skipped, but when during testing there were problems with the
volumes.

What has been done for these tests, is add striped volume support for
OpenStack, and add support for thin volumes. These act a bit like sparse
volumes, so that if you try to read data you have not explicitly written
to the volume, it will return 0.

NB! The changes made to OpenStack are not of the quality to submit
upstream. Currently the timetable does not allow for designing and
committing these changes. This might be done at a future time.

IO Schedulers
---------------------------------------------

The linux kernel uses schedulers to decide in which order IO operations
are executed. There are several on these IO schedulers. The default is
the Completely Fair Scheduler (CFQ). In practice we have has success
using the deadline scheduler for virtualized workloads, so both will be
tested here.

Benchmarks
---------------------------------------

4 different benchmark setups were tested

	* XFS filesystem backend with the CFQ IO scheduler
	* XFS filesystem backend with the deadline IO scheduler
	* LVM filesystem backend with the CFQ IO scheduler
	* LVM filesystem backend with the deadline IO scheduler

For each setup, two different tests were run

	* 1 hypervisor running 1 large VM doing IO operations on the disk
	* 1 hypervisor running 4 smaller VMs doing IO operations on the disk

For all benchmarks the FIO software was used. FIO ran four tests,
streaming write, streaming read, random 4k write and random 4k read.
Each test was run with 1, 2, 4, 8, 16, 32, and 64 simultaneous threads.
All test used direct IO. Due to the number of the graphs, not all
results from thread amounts were added to graphs. All data is available
in the spreadsheets though.

All XFS fileystems use a striped logical volume as a backend. All LVM
volumes for LVM backed storage are striped thin volumes.

In the case of 4 smaller VMs, the numbers are per-VM numbers. To get the
server performance, multiply by 4. In the 4k random read/write cases,
the results are in IO operations per second (IOPS), not MB/s, since IOPS
is a more relevant unit here.

The ODS document with the data and associated graphs is attached to this
page. Each graph has 4 groups, XFS-CFQ, XFS-DL, LVM-CFQ and LVM-DL. I
did not manage to get those labels in, but I fought enough with
openoffice to not care anymore. So, when you look at the graps

XFS-CFQ, XFS-DL, LVM-CFQ, LVM-DL

### Some observations

In general it seems that LVM backed VMs performed much better than XFS
backed in a shared environment. The more concurrency, the better they
performed. XFS backed performance tended to stay the same, or degrade
with more concurrency. Streaming writes and reads in general seemed to
be much better with LVM, the only exception being single threaded reads
from 4 concurrent VMs. Also the speed of random reads in a multi-VM
environment are pretty much unacceptable with an XFS backend, but
realatively good with LVM.

From the scheduler side, it seems that the deadline performs a bit
better than CFQ, especially with a lot of concurrency.

### Recommendations

Based on these benchmarks it's recommended to use LVM thin volumes with
the deadline scheduler for these nodes.

OpenStack scheduling
-----------------------------------------------------------

When these nodes are taken into use, OpenStack should schedule only
hadoop flavors to hadoop nodes, and generic flavors to generic nodes.
This will be done using host aggregates.

The following procedure should take cade of that (CSC takes care of
adding the right schedulers to OpenStack)

1. A host aggregate is created for hadoop
2. Hadoop nodes are added to the hadoop host aggregate
3. The hadoop aggregate is tagged with the flag hadoop=true
4. The CPU allocation ratio is set to 1.0 for the hadoop aggregate
(prevent oversubscription)
5. A host aggregate is created for generic vms
6. Generic nodes are added to the generic host aggregate
7. The generic aggregate is tagged with the tag generic=true
8. All current flavors are tagged with generic=true
9. Flavors are created for hadoop with public=false and the hadoop=true tags

The OpenStack scheduler is aware of the tags, and only schedules
machines if they have the right tags associated. Now generic flavors
should only be scheduled to generic nodes, and hadoop flavors to the
hadoop nodes. Hadoop flavors will not be visible by default to the end
users.

In Icehouse there will be an addition to the scheduling, so you can
group VMs. This group can have restrictions, e.g. no VMs in the group
are allowed on the same physical host. When this is implemented, it
should result in more consistently performing hadoop clusters.

End user notes
-----------------------------------------------

Note! Because these nodes are special, some attention is needed when
using them.

cloud-init needs to be installed on all VM images that are run on these
machines. Due to LVM, openstack can't inject the ssh credentials to the
disk, they have to be provisioned using cloud-init.

xfsprogs should to be installed on the VM images. in CentOS 6 ext4 has a
limitation on 16 TB partitions, and by default OpenStack partitions the
ephemeral disks. Thus the config was changed to make XFS partitions
instead on the ephemeral disks. If one wants to use them without
reparitioning, XFS needs to be supported.

live migration is not possible on hadoop nodes. This means that service
breaks might affect end-users VMs on hadoop nodes.

To make sure all hadoop data nodes go on different physical nodes, an
they should be scheduled within an AntiAffinity group. More information
here
<https://raymii.org/s/articles/Openstack_Affinity_Groups-make-sure-instances-are-on-the-same-or-a-different-hypervisor-host.html>

Image creation and update process
==========================================================================================================

Environment
--------------------------------------------------------------

-   Images are built in barebone
-   User account is **imgbuild** with password currently set to
    PASSWORD
-   imgbuild user account uses butler.service credentials for OpenStack
    interaction

Process details
----------------------------------------------------------------------

-   Build configuration principles
    -   For each new major release, a new cron entry needs to be added
    -   Minor/update releases are picked up automatically from the repos
        and thus do not need new crontab entries
    -   One-off builds for example for a security fix are technically
        possible
-   Interval
    -   Images are built every two weeks on saturday-sunday night
-   Naming
    -   Image filenames do not carry timestamps or minor version
        information
        -   E.g. generated image files are called centos.qcow2 /
            ubuntu.qcow2 / debian.qcow2
    -   Openstack side image name syntax is
        [distribution]-[version]-server-[architecture]
-   Delivery
    -   Image testing is done by the CSC automation tool (which needs
        some additional tests on top of the ICMP test)
    -   New images are set as public
    -   Old images are not deleted, but renamed with a {DEPRECATED}-
        prefix and set non-public
        -   E.g. every fortnight a new DEPRECATED- image is generated
            for each distro
        -   Retention to be discussed after Juno upgrade is complete
-   Automatic updates
    -   Images are built with automatic updates set to ENABLED (think
        least hassle for novices)
    -   Successively, FORGE playbook(s) are modified to disable
        automatic updates as per the
        [Server_updates](3_OperationalGuides.md#server-updates) policy.

Image creation commands
--------------------------------------------------------------------------------------

-   Required packages: debootstrap, debian-archive-keyring.gpg
-   Example crontab:


		PATH=$PATH:$HOME/.local/bin
		# centos
		# 0 2 * * 0 [ `expr \`date +\%s\` / 86400 \% 2` -eq 1 ] && . ~/.openrc/Digile.Devel-openrc.sh && . ~/.ssh/ssh-enable && cd ~/scripts && bash image_create_centos-7.sh; ssh-agent -k 
		# debian
		# 15 2 * * 0 [ `expr \`date +\%s\` / 86400 \% 2` -eq 1 ] && . ~/.openrc/Digile.Devel-openrc.sh && . ~/.ssh/ssh-enable && cd ~/scripts && bash image_create_debian-wheezy.sh; ssh-agent -k
		# ubuntu
		# 45 2 * * 0 [ `expr \`date +\%s\` / 86400 \% 2` -eq 1 ] && . ~/.openrc/Digile.Devel-openrc.sh && . ~/.ssh/ssh-enable && cd ~/scripts && bash image_create_ubuntu-trusty.sh; ssh-agent -k
		# 0  3 * * 0 [ `expr \`date +\%s\` / 86400 \% 2` -eq 1 ] && . ~/.openrc/Digile.Devel-openrc.sh && . ~/.ssh/ssh-enable && cd ~/scripts && bash image_create_ubuntu-precise.sh; ssh-agent -k

-   Example one-off run with diskimage-builder-csc-automation (Needs
    ICMP in the default secgroup to succeed)


		imgbuild@barebone:~$ cd scripts
		imgbuild@barebone:~/scripts$ source ~/.openrc/Digile.Devel-openrc.sh
		imgbuild@barebone:~/scripts$ ./image_create_centos-7.sh 


OpenStack quota and flavor
=====================================================================================

Backround
---------------------------------------------------

In the CRA contract the following parameters are defined

-   VCPU Cores
-   RAM
-   Storage
-   Bandwidth in
-   Bandwidth out

The OpenStack configuration, the default quota is as follows

-   10 instances
-   20 vcpus
-   51.2G RAM
-   350 external IPs and can grow up to ~800 IPs (altogether)

It is close to impossible to define the default CRA that would meet the
customer needs without knowing the type of usage. There are so many user
scenarios that one default CRA most likely doesn't fit any of them
properly. For instance:

-   In video encoding a lot of computing capacity and disk space is
    required
-   In web service, a load balancer and several virtual cores are needed
-   In network storage service a lot of disk space is required

### Hardware

Compute hardware is illustrated in the attached file
[iaas_hw.ods](/files/iaas_hw.ods)

In the system setup we have 16 generic nodes. These nodes belong to the
"default" host aggregate which has the "generic=true" tag. Each node has

-   32 Cores (hyper threading) (without over committing)
-   128G RAM
-   6*900G local disk (backup for the instance store, hadoop use
    scenarios where fast local disk speed is needed in the future)

We also have 12 Hadoop nodes. These nodes belong to the "hadoop" host
aggregate which has the "hadoop=true" tag. Each of these have

-   20 cores (non-hyper-threaded)
-   192 GB RAM
-   15*4TB disks -&gt; 43 TB usable storage

Then we have additionally

-   60TB usable network storage
    -   10 TB currently for the NFS virtual disks storing
        images and ephemeral disks
    -   40 TB currently for the Volumes (Cinder)

CRA
---------------------------------------

Planning assumption is that we'll have 20-30 projects in the cloud.
Based on the experience from the previous cloud setups and discussion in
the FORGE Technical Project meeting 2013-12-02 the proposal for setting
default quota is:
 Following quota allows 52 CRAs

-   Overcommit CPUs with the factor of 2 which would make the available
    vcpus up to 64 in one node
-   RAM would not be overcommitted but dedicated.
-   The default quota for the tenant is 1/4 of the node capacity
    -   16 instances
    -   16 vcores (Note! 2x overcommitted)
    -   32G RAM
    -   10G/vcore instance storage
    -   1TB volume storage (from ~40TB usable)
    -   1TB object storage (from ~45TB usable)
    -   5 external IPv4 IPs
    -   No IPv6 addresses (support is pending OpenStack support)
    -   Network bandwidth is shared among all projects

|	Purpose	|	Nodes	|	Sum - VCOREs	|	Sum - RAM(GB)	|	Sum - SATA(usable GB)	|	Sum - SATA (ephemeral GB)	|	Sum - volumestorage(GB)	|	Sum - objectstorage(GB)	|
|	--------	|	--------	|	--------	|	--------	|	--------	|	--------	|	--------	|	--------	|
|	CRA	|	m1.small	|	16	|	32	|	160	|		|	1000	|	1000	|
|	Total Result	|		|	16	|	32	|	160	|		|	1000	|	1000	|


### Flavors

Flavors would be OpenStack default except m1.tiny would have 1024MB RAM
(instead of 512MB). Note! That would only consume 16GB RAM if all
instances from quota were m1.tiny. All flavors need to have a tag.
Currently this is either "generic=true" for non-hadoop nodes or
"hadoop=true" for hadoop nodes. This is needed for working scheduling.
This can be done with a command nova flavor-key m1.tiny set
generic=true. So, following flavors have the generic=true tag, so they
only get scheduled to generic nodes.

| Name      | Memory_MB | Disk | Ephemeral | Swap | VCPUs | RXTX_Factor | Is_Public |
|-----------|-----------|------|-----------|------|-------|-------------|-----------|
| m1.tiny   | 1024      | 10   | 0         |      | 1     | 1.0         | False|
| m1.small  | 2048      | 10   | 0         |      | 1     | 1.0         | False     |
| m1.medium | 4096      | 20   | 0         |      | 2     | 1.0         | False     |
| m1.large  | 8192      | 40   | 0         |      | 4     | 1.0         | False     |
| m1.xlarge | 16384     | 80   | 0         |      | 8     | 1.0         | False     |

Flavors configured for Microsoft Windows instances

| Name      | Memory_MB | Disk | Ephemeral | Swap | VCPUs | RXTX_Factor | Is_Public |
|-----------|-----------|------|-----------|------|-------|-------------|-----------|
| win.medium| 16384     | 80   | 0         |      | 4     | 1.0         | False     |
| win.large | 32768     | 80   | 0         |      | 8     | 1.0         | False     |


### Changes to flavors

When you remove tenant access from a flavor, please note that if the
tenant has VMs with that flavor, the API and web interface will give
errors. In this case the customer has to be informed.

If you completely replace a flavor, this will break existing VMs using
this flavor. In this case, please delete the old flavor, and tell CSC to
mark the deleted flavor public in the database. This workaround should
fix any problems.

CRA (bigdata)
---------------------------------------------------------

Clusters to be 1 + 2 + 10 (1 monitor(tiny/small), 2
namenodes(hadoop.small), 10 datanodes(dn)). This means a quota of min.
14 instances (+1 control vm for ansible and such, tiny flavor) plus
flavor demands.
 Following quota allows 5 bigdata CRAs

-   16 instances
-   46 vcores
-   400G RAM
-   10G/vcore instance storage
-   2150G/vcore ephemeral storage on big data specific flavors (cannot
    be snapshotted)
-   1TB volume storage (from ~40TB usable)
-   1TB object storage (from ~45TB usable)
-   15 external IPv4 IPs
-   No IPv6 addresses (support is pending OpenStack support)
-   Network bandwidth is shared among all projects

|	Purpose	|	Nodes	|	Sum - VCOREs	|	Sum - RAM(GB)	|	Sum - SATA(usable GB)	|	Sum - SATA (ephemeral GB)	|	Sum - volumestorage(GB)	|	Sum - objectstorage(GB)	|
|	----------	|	----------	|	----------	|	----------	|	----------	|	----------	|	----------	|	----------	|
|	CRA(bigdata)	|	hadoop.medium	|	40	|	360	|	400	|	86000	|		|		|
|		|	hadoop.small	|	4	|	36	|	40	|	8600	|		|		|
|		|	m1.small	|	2	|	4	|	20	|	0	|	 	|	 	|
|	Total Result	|		|	46	|	400	|	1220	|	94600	|	1024	|	1024	|

### Flavors (bigdata)

Bigdata flavors look like this. Bigdata nodes don't use CPU
overcommitting. Note that these flavors are not public by default. These
flavors have the hadoop=true tag, so they only get scheduled to hadoop
nodes.

| Name          | Memory_MB | Disk | Ephemeral | Swap | VCPUs | RXTX_Factor | Is_Public |
|---------------|-----------|------|-----------|------|-------|-------------|-----------|
| m1.tiny   | 1024      | 10   | 0         |      | 1     | 1.0         | False      |
| m1.small  | 2048      | 10   | 0         |      | 1     | 1.0         | False      |
| hadoop.small  | 18432     |  20  | 4300      |      | 2     | 1.0         | False     |
| hadoop.medium | 36864     |  40  | 8600      |      | 4     | 1.0         | False     |
| hadoop.large  | 92160     | 100  | 21500     |      | 10    | 1.0         | False     |

Requesting more quota
---------------------------------------------------------------------------

Affiliates will be able to request for more resources. The request will
be decided case by case basis (“tarveharkinta”) and doesn'’t necessarily
cause any changes in billing. The tenant's quota would then be modified
according to the request and decision. Any quota parameter could be
increased individually except CPU and RAM would be bound together (1
Core/2G RAM)

-   Additional vcores (will also increase RAM respectively)
-   Additional instance storage
-   Additional volume storage
-   Additional IPs

OpenStack Status
=============================================

This page lists the readiness of the OpenStack services and possible
problems.
 The monitoring will be a separate issue.
 CSC is responsible of these.

Ready components
-------------------------------------------------------

*When the components are properly tested (process to be defined later)
they are listed here. DIGILE decides exposing them for the customers.*

-   None

Components available for testing
---------------------------------------------------------------------------------------

When CSC informs that the components are available for the FORGE
internal testing they are listed in this section.

-   Nova : Virtual Machine management
    -   commmand line APIs (excluding EC2)
-   Networking
    -   Metadata
    -   Public IPs
    -   Firewall configurations
-   Horizon : the web user interface containing interfaces for various
    components
    -   available at <https://forge.csc.fi>
    -   ssh key handling
    -   VM management
    -   Images
    -   VNC
    -   Volumes
-   Glance : Uploading own virtual machine images
    -   command line APIs
-   Cinder : Volumes from the central storage
    -   Command line API
    -   NB! There is still a risk that volumes go into the
        "error_deleting" state when deleting a volume. The volume is
        actually deleted, but the cinder info can be cleaned up with the
        "cinder force-delete" command
-   Swift : Object storage
    -   Known problem: Downloading large files from Horizon fails.
        Horizon caches the downloads in memory, so if file &gt; free
        memory it will give an error. Also copy does not seem to work.
        TODO: recheck the issues with Havana. If cannot fix easily,
        document or disable Swift in Horizon.
-   VM disk storage on NFS for live migration. More testing needed.

Components which still need to be installed and configured
-------------------------------------------------------------------------------------------------------------------------------------------

-   EC2 API
-   Horizon : the web user interface containing interfaces for various
    components
    -   Monitoring / accounting

Windows Server
=================================================

OpenStack is able to run Windows virtual machines under KVM hypervisor.
 By default, FORGE currently doesn't provide any kind of support for
Windows. Also Microsoft does not give technical support.

DIGILE has made one exception. The exception is valid only for the particular
support request and for a particular project. Along with the support
request, the project project has accepted following terms.

    DIGILE:n linjaus ja rajaukset Microsoftin tuotteiden ja käyttöjärjestelminen käytöstä tämän tukipyynnön yhteydessä ovat seuraavanlaisia:

    Ko. hanke voi käyttää Microsoftin palvelinkäyttöjärjestelmää Palvelupaja FORGE:n IaaS alustalla edellyttäen että:

    - Ko. hanke hankki omalla kustannuksellaan tarvitsemansa MS:n käyttöjärjestelmälisenssin siten, että MS:n lisenssiedot täyttyvät.
    - Ko. hankekkeen jokin juridinen henkilö lähttää DIGILE:lle kirjallisen ilmoituksen siitä, että se sitoutuu maksamaan MS:n IaaS alustalisenssien lisenssimaksut. CSC maksaa ko. alustalisenssimaksut MS:lle, laskuttaa ne suoraan DIGILE:tä ja DIGILE edelleen em. taholta. Ilmoituksen voi lähettää sähköpostitse (NAME REMOVED)
    - Palvelupaja FORGE:n palveluvalikoimaan ei kuulu minkälaista MS spesifistä tukea, ts. hanke joutuu järjestämään teknisen tuen ko. tuotteille itse.

    Terveisin,
    (NAME REMOVED)

Since the project has accepted the terms, DIGILE has enabled windows server
image and windows specific flavors for the project. Also,
 information that can and should be provided to the project are
attached two files: the End User License Term by Microsoft and a User
Guide done by CSC.

Plaza architecture
=============================================================

FORGE Plaza has been designed basicly in content type or content types
per Plaza area way. Architecturally we can separate Plaza to 6 different
kind areas :
 1. Blogs
 2. Plaza
 3. Tutorial
 4. Front page
 5. Projects
 6. Wizard

Blogs
-----------------------------------

On blogs we're using two different content types
 1. Blog
 2. Blog post

With Blog you can create actual Blogs and blog posts are put into blogs

Plaza
-----------------------------------

On Plaza we're currently using 5 different content types
 1. Service offers
 2. Product offers
 3. Organizations

Organizations are eligible to create different kind of offers.
Organizations can be created by Partner categorized users.

Tutorial / Dashboard
---------------------------------------------------------------

On tutorial we're using only one content type:
 1. Tutorial

Tutorial is part of website where developer categorized users can
access.

Front page
---------------------------------------------

On front page we're using 4 different content types:
 1. Page
 2. FAQ-item
 3. Tweet
 4. News

Page is basic page content type that could be also used on other parts
of website. FAQ-items are for FAQ-listing, tweets are generated from
twitter tweet-objects with Feeds-module and News are actual news. Page,
FAQ-item and News type of content can be added to website by
Digile-workers and other admins. Tweets are imported automatically.

Projects
-----------------------------------------

Project content-type is used to manage projects area. Can be added by
Digile-workers and other admins.

Wizard
-------------------------------------

Wizard aka Join Forge -multistep form is it's own content type. Webform
3.0 with FillPDF are used on this content type. Includes also custom JS

sites/all/themes/forgeweb/template.php. Higly complex, created by Ari
Ruuska (<ari.ruuska@druid.fi>)

Access control
=====================================================

Most of access control on FORGE Plaza has been created by using Drupal
Cores permissions. However, three contrib modules we're used to expand
core.
 1. Content access
 drupal.org/project/content_access
 Content access allows to manage permissions for content types by role
and author. It allows you to specifiy custom view, edit and delete
permissions for each content type.

1.  Comment permissions
     drupal.org/project/comment_perms
     Allows you to manage permissions for comments by role, author and
    content type.

2.  Field permissions
     drupal.org/project/field_permissions
     Allows you to manage permissions FOR EACH FIELD by role and author.

Content Access is used on tutorial to give read permissions for
developers only, on offers and organizations to give add permissions for
partners only and read permissions to all FORGE Member on all Plaza
content. Content Access is also giving us possibility to give
permissions for each nodes, so on Wizard we're restricting all view, add
or edit permissions to the user who is currently filling up the form.

Drupal core permissions can be found from admin/people/permissions.
Content Access permissions and Field permissions can be found from
admin/structure/types/manage/NAME_OF_CONTENT_TYPE/access.

Field permissions are used on both offers to set pricing and contract
fields not visible for anonymous users.

Authentication
=====================================================

Important authentication related stuff can be found from LDAP & CAS
Study. However, we didn't get ldap_authorization module work properly.
We spent like a week on debugging it, but we couldn't find any sane way
to debug it effectivily. Issue is that we get correct role-information
and in some cases it just doesn't map role in right way. We resolved the
issue by writing a small custom module that is querying all roles from
LDAP and a small user interface where you can click the right roles for
right groups. The module can be found from sites/all/custom/ldap_forge

Caching and other performance related stuff
===============================================================================================================

We currently have 3 different caching-strategies
 1. Additional PHP-caching
 2. Drupal core cache by time
 3. Drupal core cache when saving content

Between May and July we had some serious problems on site-performance.
Biggest reason for this was that we chose time-based only strategy.
Time-based strategy is relatively good when site is not updated that
often, like we have, and when we have a lot of users, which we don't
have. This led to a point where most of content was created on every
single load by anonymous users. On views we have two options, cache
rendered output and cache queries. At this stage we're using same time
for both on each case.

And the end of July we changed time based caching to longer. Most of
views on website are cached for a day and some, like projects, are
cached for 6 days.

As PHP Cache we use XCache. It's part of Ansible playbook and deployed
automatically.

Other important stuff on caching

Normal caching on Views-module queries does not really compute with
exposed filters (f.ex. feed and plaza-front page search). Because of
this we had to patch Views-module. Patch can be found from
sites/all/modules and in case views-module is updated (WILL HAPPEN) make
sure that the patch applies with new views.

What we should still do on caching
---------------------------------------------------------------------------------------------

1.  Install SQL-caching (or key-value caching) like memcached or Redis.
2.  Install Front-caching like Varnish or use nginx as front-cache. Both
    will be highly complex with current server setup.

Other performance related stuff
---------------------------------------------------------------------------------------

All JS ans CSS is minified. Out of the box Drupal puts all javascripts
to , we've moved nearly all JS from to so that most of DOM gets rendered
before JavaScripts are called. For minifying and JS-movement
contrib-module called advagg. drupal.org/project/advagg

General stuff on sitebuilding
===================================================================================

Site has been build with modules called Features.
drupal.org/project/features

Most of to-be-taken-seriously Drupal-companies in world are handling
stuff in same way. Features modules is basicly making a convert from
Drupal UI to PHP code. Where Features is really good is that you can
pack relevant stuff for each feature to one feature set.

F.ex. On Front-page FAQ-feature we have:
 1. FAQ view that is listing stuff to front-page
 2. Context where we are setting FAQ-view to correct page
 3. FAQ content type

Example feature can be found from
en/admin/structure/features/forge_web_faq

Really good thing on Features is that if we make a decission to drop
let's say whole FAQ feature out. Good way to handle thing is to:
 1. Take FAQ-feature out of our GIT repositry
 2. Redeploy
 -&gt; you're ready to go

We have similar feature for each and every single unique feature on
Plaza. List of features can be found from en/admin/structure/features

Other important modules and why they're on use
======================================================================================================================

1.  Context
     drupal.org/project/context
     Allows you to define which elements are shown on which page. Ie you
    can say that when path is we will show slideshow, what&where, faq
    and feed. Or, when we are on which ever page show footer. UI can be
    found from admin/structure/context. Notice that Context UI module
    must be enabled if you want to see the UI. Context will work without
    UI module enabled anyways.

2.  Display Suite
     drupal.org/project/ds
     Allows you to take full control over how your content is displayed
    using a drag and drop interface. Arrange your nodes, views,
    comments, user data etc.
     Can be found from admin/structure/types/manage/NAME OF CONTENT
    TYPE/fields

3.  Feeds + Feeds OAuth
     drupal.org/project/feeds
     Is used to import twitter-json as nodes on Drupal end. Will be
    documented clearly. Highly complex and far from clear.

4.  Entity translation
     drupal.org/project/entity_translation
     Enables multilingual functionality on FORGE

Digital Signature
===========================================================

There's two different digital signature solutions:
 1. Onnistuu.fi
 2. Signicat

Onnistuu.fi
----------------------------------------------

Onnistuu.fi is finnish digital signature service. It's written in PHP,
it's simple and easy. The module for onnistuufi can be found from
sites/all/modules/custom/onnistuufi. Basic idea in module is that we
have three different tokens we're sending to onnistuufi via their API.
Tokens came with contract, so in case contract is changing make sure
that we have correct tokens in code.

Signicat
-----------------------------------------

Signicat is international digital signature service. API to Drupal is
basicly quite complex SOAP-call collection. Module can be found from
sites/all/modules/custom/signicat. At this point I don't see any reason
at any point to why module would be in need of changes. Except if the
API is somehow changing. The API is so complex that I see no reason why
they would change it.

Plaza cluster architecture
=====================================================================================

The entirety of the Plaza cluster runs on Debian Wheezy machines.
 The devel and environments are built on
OpenStack and they require an allocation of three floating IPs, one for
the Load Balancer which will be exposed to the world and two others for
the NFS and MySQL highly available clusters, respectively.

Overview
-------------------------------------------------

![Plaza
Architecture](/files/plaza.png)

The server cluster for Plaza is based on the Drupal-HA cluster
architecture with the addition of CAS,
LDAP and Redmine integration.

CAS integration
---------------------------------------------------------------

Drupal is integrated with CASino via the [CAS
module](https://drupal.org/project/cas) and the profile field
syncronization is possible through the [CAS Attributes
module](https://drupal.org/project/cas_attributes). These modules are
dependent on the [phpCAS
library](https://wiki.jasig.org/display/CASC/phpCAS).

    $ sudo apt-get install php-cas

Once installed, the CAS module provides two submodules, 'CAS' and 'CAS
server'; we only need the first one enabled to provide integration with
CASino.
 ![Enabled
Modules](/files/Screenshot_from_2014-01-17_14_46_13.png)

The basic module settings to allow communication with CASino are as
follows:
 ![Basic
Settings](/files/Screenshot_from_2014-01-17_14_51_12.png)

The fine tuning settings for this module are described in detail on the
[Plaza CAS integration settings](#plaza-cas-integration-settings)
article.

LDAP integration
-----------------------------------------------------------------

While the drupal CAS module above is enough to provide Single Sign On
capabilities, we decided to use drupal's [LDAP
module](https://drupal.org/project/ldap) to provide the authorization
layer and map roles on drupal to groups on the LDAP database.
 The LDAP module has a dependency on PHP's LDAP library.

    $ sudo apt-get install php5-ldap

The devel and testing environments use a testing ldap that shows SSL
verification issues. To properly interact with it we need to tell our
client to ignore these errors by editing the `/etc/ldap/ldap.conf` file
and appending this line:

    TLS_REQCERT never

The LDAP module has a wide array of submodules that introduce extra
dependencies on separate modules, namely drupal's [ctools
module](https://drupal.org/project/ctools) and the [entity
API](https://drupal.org/project/entity). Following is the list of
submodules that we need enabled for Plaza's LDAP integration:

Chaos Tools suite:
 ![ctools
submodules](/files/Screenshot_from_2014-01-17_14_58_24.png)

Entity API:
 ![entity
submodules](/files/Screenshot_from_2014-01-17_15_02_20.png)

LDAP module:
 ![ldap
submodules](/files/Screenshot_from_2014-01-17_15_02_05.png)

The fine tuning settings for the LDAP module are described in detail on
the [Plaza LDAP integration settings](#plaza-ldap-integration-settings)
article, the entity API and the ctools suite do not provide extra
settings.

The Token module
-----------------------------------------------------------------

Drupal's [Token module](https://drupal.org/project/token) is not
required for the authentication/authorization procedure but it provides
important functionality in terms of account provisioning. Since Drupal
creates its own user accounts regardless of the authentication method,
the Token module allows pulling profile info from the LDAP server.
 This module has no configuration parameters, it just provides
functionality for the CAS and LDAP modules.

The Role Delegation module
-------------------------------------------------------------------------------------

On the baseline [Drupal Roles and Mappings](#drupal-roles-and-mappings)
document the 'editor assigner' role is defined. This role is capable of
assigning the role of 'editor' to other users and to provide this
functionality we will use drupal's [Role
Delegation](https://drupal.org/project/role_delegation) module.
 This module doesn't have configuration parameters but rather adds
options to the role permissions list, which will be configured as
follows:

![Role
Delegation](/files/Screenshot_from_2014-01-21_09_54_19.png)

Drupal Roles and Mappings
==================================================================================

Overview
------------------------------------------------

![](/files/roles.png)

Rationale
--------------------------------------------------

The permission matrix for Plaza is divided horizontally in roles and
vertically in organizations. Vertical division is out of the scope of
this article and we just need to bear in mind that the horizontal
divisions overlap the vertical ones, that is the roles are always system
wide in the sense that the same role will have the same permissions
across different vertical organizational partitions, of course, the
vertical partitioning ensures that the roles subjected to it can only
exercise their permissions within their organization, for example:

Take two vertical organizations A and B, and the horizontal roles R and
S where S is a base access role not subjected to vertical partitioning.
 While members of role S will appear as S-belonging to both
organizations no matter what, members of role R on organization A will
appear as members of role S on organization B and conversely.

This approach will ensure data compartmentalization within the entirety
of Plaza, restricting the users' elevated rights to the subset of data
that they are allowed to manage.

It is important to note that the role hierarchy is downward inclusive,
meaning that higher roles will include all the permissions from the
roles below.

Role Burndown
----------------------------------------------------------

### System-Wide roles

These are the topmost roles in the hierarchy and they are not subject to
vertical partitioning. In the scope of Plaza these roles are assigned to
a select group of trusted few for platform management tasks.

-   **User 1:** This is a drupal-only role, it consists of a single user
    created during installation and has no mapping to any roles within
    Forge's hierarchy; it has complete control over the installation and
    its use should be avoided as much as possible.
-   **Administrator:** This role maps to members of the Digile team, it
    has full control over the platform.
-   **Operator:** Members of this role wield a subset of the
    administrator permissions. Basically operators can manage the
    entirety of the platform save for the modules critical to the
    integration with other Forge systems such as LDAP or CAS.
-   **Registered User:** This is the baseline role for users with any
    kind of direct business relationship with Forge, it provides the
    least permissions while still allowing to browse
    Forge-restricted content. All users appear as Registered Users
    outside their vertical organizational partition.

### Roles subject to compartmentalization

Compartmentalized roles apply only within the users' vertical
organizational partition, nevertheless the permissions are the same
across partitions.

-   **Editor Assigner:** This role allows its members to promote
    Registered Users within their vertical partition to the role
    of Editor.
-   **Editor:** Members of this role are allowed to create content and
    edit/delete content within their vertical organizational partition.
    This is a drupal-only flag role that has no mapping outside drupal's
    user database, to the rest of Forge editors are Registered Users,
    that is members of any group with some contractual relationship
    with Forge.

### Public roles

These roles grant low level access to users outside Forge. Members of
these roles do not have any direct or contractual relationship with
Forge.

-   **Authenticated User:** This role is drupal-only and has no mapping
    within the Forge hierarchy. The purpose is to grant commenting
    rights to arbitrary people outside the Forge organization. Users of
    this group will map to Forge Friends who are not Forge Affiliates
-   **Anonymous User:** This is the lowermost access level to Plaza and
    it is completely public in the widest sense of the word. Absolutely
    anybody with an internet access is an Anonymous User. The role has
    no permissions other than viewing public content on Plaza.
	
Plaza CAS integration settings
=================================================================================================

Following are the detailed settings for the [CAS
module](https://drupal.org/project/cas).
 First, we want the site's login forms to default to CAS login.

![](/files/Screenshot_from_2014-01-21_15_00_36.png)

According to our [Drupal Roles and
Mappings](#drupal-roles-and-mappings), anybody who can login with CAS is
a registered user so we'll allow the module to automatically create the
drupal accounts and assign the default roles. Account details such as
email and password are pulled from the LDAP records so we don't want to
allow local changes on the drupal accounts.

![](/files/Screenshot_from_2014-01-21_15_00_44.png)

The baseline redirection uses default settings, but it might change in
the future:

![](/files/Screenshot_from_2014-01-21_15_00_52.png)

We want to redirect logged out accounts to the public front page. Also
the password reset functionality must be handled by the in-house
solution running on
[auth.forgeservicelab.fi](https://auth.forgeservicelab.fi/password/index.php)

![](/files/Screenshot_from_2014-01-21_15_01_04.png)

The miscelaneous settings don't offer any interesting functionality as
of this writing.

![](/files/Screenshot_from_2014-01-21_15_01_10.png)

On the CAS Attributes tab we'll be able to set the mappings from the
account attributes fetched from CAS to drupal account fields.
 ![CAS
Attributes](/files/Screenshot_from_2014-01-21_15_02_34.png)

Plaza LDAP integration settings
====================================================================================================

The first requirement for LDAP integration is the connection setting to
the LDAP server, please note that the specific settings portrayed below
are specific to the testing environment and also temporary due to plans
to set up a full-fledged server for testing purposes instead of a proxy
to the production server:

![](/files/Screenshot_from_2014-01-21_14_57_27.png)

Then we need to specify which method drupal should use to bind to the
LDAP server:

![](/files/Screenshot_from_2014-01-21_14_57_35.png)

Drupal needs to know where within the LDAP database to look for the user
accounts and which attributes hold what pieces of information.
 The last two setting parameters on the following screenshot are not
mandatory.

![](/files/Screenshot_from_2014-01-21_14_57_56.png)

The Group Configuration is necessary to leverage the Authorization
module, we need to tell drupal how to find members of LDAP groups so
that we can later map those to drupal roles.

![](/files/Screenshot_from_2014-01-21_14_58_14.png)

We leave pagination off by default since there are not so many records
on LDAP at the moment.

![](/files/Screenshot_from_2014-01-21_14_58_32.png)

Having taken care of the server configuration and now that we have a
working connection to the LDAP server we can configure the LDAP User
Settings.
 We saw on [Plaza CAS integration
settings](#plaza-cas-integration-settings) that CAS will create drupal
accounts automatically on login, now we need to map those accounts to
the LDAP entries so that they can be used for authorization.

![](/files/Screenshot_from_2014-01-21_14_59_01.png)

When the drupal account is mapped to the LDAP entry, we need to specify
how the LDAP attributes map to drupal account attributes.

![](/files/Screenshot_from_2014-01-21_14_59_19.png)

We don't allow drupal to push private accounts to LDAP

![](/files/Screenshot_from_2014-01-21_14_59_36.png)

With the User settings in place, we can continue to configure
authorization.
 First we need to select which LDAP server the authorization settings
apply to and enable the configuration.

![](/files/Screenshot_from_2014-01-21_14_59_55.png)

Then we need to define the mappings from LDAP records to drupal roles.
In our case, the only roles managed by LDAP Authorzation module are
administrator, operator and editor assigner. Note that we need to leave
the last option on the next block unchecked so that the other roles on
the system can still be managed through other tools.

![](/files/Screenshot_from_2014-01-21_15_00_03.png)

Finally we make sure we check the assigned roles on a fairly regular
basis.

![](/files/Screenshot_from_2014-01-21_15_00_09.png)


