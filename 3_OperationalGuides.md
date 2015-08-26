Operational guides
=============================================================

Contributions
==============================================

The basic principle is that DIGILE develops stuff for itself and doesn't
put effort into anything just for the sake of the contribution unless
decided otherwise. DIGILE aims at contributing back to the community if
the output can be considered as useful and it's feasible to put it
upstream. Also, it's been decided that we won't focus on legal analysis
but we focus on documenting used components and changes that we make so
that we are able to demonstrate that we care about the licences and we
appreciate open source community.

Document contributions
----------------------------------------------------------------

Applies to contributions which FORGE Service Lab TC document refers to.
E.g. Documentation in Wiki, presentations, videos.

-   Contribution license is **Creative Commons Attribution-ShareAlike
    3.0 Unported License** in case of a new contributions.
-   Copyright must be indicated in the material as mentioned in the
    [Copyright](#copyright) section below.
-   Licence should be indicated in the material according to
    instructions of Creative Commons Attribution-ShareAlike 3.0
    Unported License. 

SW contributions 
-----------------------------------------------------

Apply following practicalities to all software contributions:

-   In case of a change to existing SW

    -   The licence suitability should always be checked. In addition to
        checking the licence suitability there are no restrictions in
        submitting changes to existing SW. Check the suitability against
        recommendations made in [Due diligence](#foss-components).
-   In case of a new SW contribution

    -   If the new contribution has dependencies, then the suitability
        and compatibility of the direct dependencies' licences must
        be checked. The compatibility can be checked against the
        compatibility table
        <http://www.dwheeler.com/essays/floss-license-slide.html>. The
        suitability can be checked against the recommendations made by
        [Due diligence](#foss-components). The result of the
        investigation is to be documented as part of the contribution
        files e.g. Readme file.
    -   The license for the contribution is to be determined in the "SW
        contribution process" meeting. Basic principle is that we use
        GPLv3 or GPLv2 for SW contributions when we want somebody else
        to contribute as well. We use BSD or MIT licence if we don't
        care about the future of the SW contribution.
    -   Source codes should have all the secrets removed and replaced
        with e.g. \[USERNAME\], \[PASSWORD\]
    -   After the licence investigation is ready and the contribution is
        ready to be published then the author invites a "SW contribution
        process" meeting with following participants: (USERNAMES REMOVED).

Copyright
======================================

DIGILE 
---------------------------------

-   In case DIGILE staff or DIGILE bodyshopped staff contributes, then
    all copyrights should be DIGILE Ltd as in the example below.

		Copyright (c) 2015 DIGILE Ltd. This contribution has been created by FORGE Service Lab funding granted by Finnish Ministry of Transport and Communications.

DIGILE subcontractor
------------------------------------------------------------

-   In case DIGILE subcontractor. Note! Copyright
    sentence can be modified by the subcontractor to suit better to
    subcontractor's policy or community requirements.

		Copyright (c) 2015 SUBCONTRACTOR. This contribution has been funded as part of DIGILE Ltd's FORGE Service Lab.

Modified work
----------------------------------------------

-   In case the contribution is a change to existing code, then the
    copyrights follow the format of

		Modified work Copyright (c) 2015 DIGILE Ltd. This contribution has been created by FORGE Service Lab funding granted by Finnish Ministry of Transport and Communications.

Format and location
==========================================================

Format
--------------------------------

There are two options of the format how the asset should be published:
Tarball and Repository

-   *Tarball* is not considered as a proper way of publishing anything
    to the community because the reusability of assets would suffer and
    it's generally not considered a proper way by the community.
    Publishing a tarball would also require a storage location e.g.
    SourceForge, GitLab, GitHub, web page or ftp-site.
-   Publishing whole *repository* is the preferred way since it allows
    easy reusability for by others. FORGE has stored it's source code
    asset into repositories.

Storage location
----------------------------------------------------

Making asset publicly available requires a storage location where the
asset should be placed into. There are several options for storing the
asset but in practice only two viable options: FORGE's GitLab (where the
source code already is), GitHub which is publicly available free of
charge.

-   FORGE Service Lab has maintained GitLab as a repository management.
    Using FORGE's GitLab would require handing over it's maintenance to
    some other party and maintenance activities as long as it exists
-   GitHub is available free of charge and is preferred way to publish
    sourcecode asset among open source community. This option is
    selected by the project that could be used as a reference:
    <https://github.com/educloudalliance>

The method in which asset is to be published is **whole repositories in
GitHub**

Checklist
======================================

The following checklist is to be used in the "SW contribution process"
meeting.

-   Licence ok
-   Secrets removed
-   Copyright text

More information
====================================================

For more information contact FORGE Service Lab FOSS
Compliance Officer.

FOSS components
====================================================

-   OpenStack cloud middleware is used to provide the IaaS platform:
    <https://wiki.openstack.org/wiki/Open>.
-   Ubuntu, CentOS and Debian virtual disk images are being used both as
    a basis to FORGE SaaS and they are provided as is for affiliate use.
    Debian is built from source code by DIGILE and other images are used
    as they are provided by the vendor. It's assumed that DIGILE uses
    virtual machine images as they are provided and DIGILE doesn't
    change their content. Any exception to this assumption must be
    discussed and decided separately in order to understand if due
    diligence must be conducted or not.
-   Miscellaneous open source components have been selected to
    build SaaS. The components are listed in
    [Infrastructure_overview](2_Infrastructure.md#infrastructure-overview).
-   DIGILE has made an [due diligence](#due-diligence) assessment
    for a set of selected components it uses to build and offer SaaS
    for affiliates. The up to date list of components is maintained in
    [Infrastructure_overview](#2_Infrastructure.md#infrastructure-overview).

FOSS component usage practicalities
--------------------------------------------------------------------------------------------

-   Modifications to components should be documented as part of the
    normal source code version control practices e.g. commit message. In
    case of contribution to original source code, then FOSS
    contributions section applies.
-   Components selected and their licenses must be documented, analysed
    and kept up to date in
    [Infrastructure_overview](2_Infrastructure.md#infrastructure-overview). Even though it
    is not likely that source code distribution would either cause
    significant problems for DIGILE, taking components in use that are
    licensed under Affero License or GPL v3 with Affero addendum is not
    recommended because of unknown side effects within the
    software architecture.
-   Documentation of dependencies in the software architecture
    **TBD B)**

Due diligence
================================================

-   DIGILE has made an due diligence assessment for a set of selected
    components it uses to build and offer SaaS for affiliates. The list
    of components is maintained in
    [Infrastructure_overview](2_Infrastructure.md#infrastructure-overview).
-   The result of the due diligence and advice are in
    [OSS_Memorandum_03-2014.pdf](/files/OSS_Memorandum_03-2014.pdf).
-   New due diligence will be triggered ad hoc if there are amendments
    in FORGE practices or activities or if major concerns as to
    compliance arise.

FOSS compliance issues
==================================================================

Compliance issues are to be reported by filing a new bug into Redmine
with category "license" selected. The normal [issue
management](#issues-management)
procedure applies.

More information
======================================================

For more information contact FORGE Service Lab FOSS
Compliance Officer.

TBD
============================

B) Automatically generated architecture diagram that lists component
dependencies and licenses used as in
[Infrastructure_overview](2_Infrastructure.md#infrastructure-overview).


Security and confidentiality
===========================================================================================

Code visibility
-----------------------------------------------------------------

-   Code written by DIGILE according to FOSS default is private
    -   FORGE Ansible playbooks visibility in gitlab is private
    -   Generic Ansible playbooks visibility in gitlab is internal
    -   Ansible roles visibility in gitlab is public and roles must not
        include any confidential information
-   Code inherited from upstream and modified according to FOSS default
    is private

TBD
-----------------------------------------

-   <https://git.forgeservicelab.fi/forge/casinoapp> public or private
    or internal

Server updates
=================================================

Policy
---------------------------------

-   The update may concern one of these
    -   Distribution upgrade
    -   System update (daily updates for the distribution)
    -   Application update (by the playbook and if not done by CI)
    -   Security update
-   Only attended server updates are to be performed. Note! server
    updates are not unattended because there is a risk that updates
    cause problems.
-   Prior to update it should be evaluated if it's a) necessary and b)
    safe to perform the upgrade (does the custom application still
    continue running after the update)
-   If the conf file is to be changed to the package maintainer's
    version, that the default should be used as long as it works and
    change to maintainers version only if it's must and then apply
    custom changes on it
-   Upgrades are to be applied to the testing server first to ensure the
    safety of the upgrade
-   A same system update playbook is to be used both for the testing
    server and for the production server
-   Kernel upgrades or low level library updates that require a reboot
    should not be made to the running system but be accumulated and
    scheduled for better time to minimize downtime

-   Distribution upgrades

    -   Are not done by default but are to be planned properly in
        the sprints.
-   System updates

    -   Are to be performed by the generic system update playbook using
        forgeadmin.csc.fi machine in the meeting
-   Application updates (which are not managed by CI)

    -   Can be made by the team members anytime
-   Security updates

    -   Are to be performed by the generic system update playbook using
        forgeadmin.csc.fi machine in the meeting
    -   Except critical security updates which are filed as a bug are to
        be updated by the team members anytime

Updating meeting
-----------------------------------------------------

Updatings are performed by Digile.Platform team twice a month even week
mondays at 13:30 in Pilvi starting 11.5.2015

Machines: All machines which visible in Nagios (except OpenStack) ...
support, auth2, nagios, git, forgeservicelab.fi, ci, analytics, grid
nodes (Note! requires a specific Firefox version. Firefox version is
pinned so the package will be held back.), drupal cluster

-   Check the need for updates of each machine and perform attended
    update
-   Update the test machine
-   Verify testing by using the test automation asset
-   Decide if it's safe to update production and then update production
-   Verify production by using the test automation asset

TBD
---------------------------

-   A generic playbook, that supports centos, debian and ubuntu to
    perform system update is needed
-   A generic playbook should disable auto updates as defined in the
    policy
-   To be investigate how to automatize security updates
-   Nice to have: A playbook to check the deviation from the mainline
    distro for team to understand the diff and help decision making in
    wether to make an update or not


Authentication and authorization infrastructure
====================================================================================================================================================

Big picture
----------------------------------------------------------------------------

Below is an illustrative example of authentication and authorization
infrastructure

![Authentication and authorization
infrastructure](/files/aai.png "Authentication and authorization infrastructure")

Access to Virtu test servers
--------------------------------------------------------------------------------------------------------------

Test server information:
<https://confluence.csc.fi/display/VIRTU/Virtu-testipalvelimet>
 In practice you need to first install and setup your own SAML2 servers.
Then you can start testing them with our test servers.
 Moreinfo: CSC

References
--------------------------------------------------------------------------

<http://www.vm.fi/vm/fi/04_julkaisut_ja_asiakirjat/03_muut_asiakirjat/20070625Virkam/02_virtu_loppuraportti_1_0.pdf>

<http://www.vm.fi/vm/fi/04_julkaisut_ja_asiakirjat/03_muut_asiakirjat/20080421Virtul/03_suunnitteluohje-20080412.pdf>

<http://www.vm.fi/vm/fi/04_julkaisut_ja_asiakirjat/01_julkaisut/05_valtionhallinnon_tietoturvallisuus/20061204Tunnis/Vahti_12_06.pdf>

Docker
=========================

What
---------------------

Docker is a tool to automate deployment of containers in Linux. It
consists of two components:

**The Docker Engine** is a wrapper around Linux cgroups (a Linux kernel
feature to isolate, account and limit resource usage).

**The Docker Hub** is an online repository of container images.

Try it out
---------------------------------

Docker is installed in barebone.forgeservicelab.fi, accessible only from
Digile VPN. Your key should be installed under your username.

    $ ssh -i privatekey.pem <USERNAME>@barebone.forgeservicelab.fi

Maniupulating containers at the moment needs root. You have sudo rights,
so I recommend handling docker as root in an interactive shell. I
installed zsh and oh-my-zsh docker plugin for root, so you can write
docker and then &lt;Tab&gt; and it will show:

    » sudo -i
    root@barebone ~ # docker <Tab>
    attach   -- Attach to a running container
    build    -- Build a container from a Dockerfile
    commit   -- Create a new image from a container's changes
    cp       -- Copy files/folders from the containers filesystem to the host path
    diff     -- Inspect changes on a container's filesystem
    events   -- Get real time events from the server
    export   -- Stream the contents of a container as a tar archive
    history  -- Show the history of an image
    images   -- List images
    import   -- Create a new filesystem image from the contents of a tarball
    info     -- Display system-wide information
    insert   -- Insert a file in an image
    inspect  -- Return low-level information on a container
    kill     -- Kill a running container
    load     -- Load an image from a tar archive
    login    -- Register or Login to the docker registry server
    logs     -- Fetch the logs of a container
    port     -- Lookup the public-facing port which is NAT-ed to PRIVATE_PORT
    ps       -- List containers
    pull     -- Pull an image or a repository from the docker registry server
    push     -- Push an image or a repository to the docker registry server
    restart  -- Restart a running container
    rm       -- Remove one or more containers
    rmi      -- Remove one or more images
    run      -- Run a command in a new container
    save     -- Save an image to a tar archive
    search   -- Search for an image in the docker index
    start    -- Start a stopped container
    stop     -- Stop a running container
    tag      -- Tag an image into a repository
    top      -- Lookup the running processes of a container
    version  -- Show the docker version information
    wait     -- Block until a container stops, then print its exit code

Similarly, the plugin is smart enough to lists available containers on
&lt;Tab&gt;:

    root@barebone ~ # docker inspect <Tab>
    3d57b0e29a10      -- [CON(3d57b0e29a10)training/webapp:latest(python)]
    75eab32e7544      -- [CON(75eab32e7544)training/webapp:latest(python)]
    <none>            t0mk/sinatrav2    training/webapp                   
    t0mk/sinatra      training/sinatra  ubunt

Drupal-Insightly integration
===========================================================================================

Categories and pipelines
===================================================================================

Following project categories and pipelines are now defined in FORGE
instance of insightly. Note! The naming convention is inherited straight
from the names of different agreements.

The devel instance of insightly should have the same structure.

Project categories
=======================================================================

	SDA = Service Development Agreement
	FPA = FORGE Partner Agreement
	FPA (CRA) = FORGE Partner Computing Resource Allocation (CRA) Addendum

Project pipelines
=====================================================================

	SDA = Service Development Agreement
	FPA = FORGE Partner Agreement
	FPA (CRA) = FORGE Partner Computing Resource Allocation (CRA) Addendum

SDA pipeline
-----------------------------------------------------------

SDA pipeline is defined as follows.

1.  Preparation stage
2.  Contract creation
3.  Contract approval
4.  CRA creation
5.  Project execution
6.  Project ending
7.  CRA removal

FPA pipeline
-----------------------------------------------------------

Initial pipeline for FPA is defined as follows.

1.  Preparation stage
2.  Contract approved
3.  Partner activities enabled
4.  Contract renewal
5.  Contract ending

FPA (CRA) pipeline
---------------------------------------------------------------------

Initial pipeline for FPA (CRA) is defined as follows.

1.  Preparation stage
2.  Contract approved
3.  CRA creation
4.  Partner activities enabled
5.  Contract renewal
6.  Contract ending
7.  CRA removal

**NOTE**
 As shown above, the pipelines for SDA and FPA (CRA) have the same
stages; unless there is a change to this there may be no reason to
create separate pipelines, except if we are using the pipeline to
identify the contract type.

Drupal usage of pipelines, categories and stages
==================================================================================================================================

Then when Drupal pushes contract creation content to insightly, the
contacts and organization should be created and then a new project
should be created with following category, pipeline and stage setting
depending on the appropriate scenario:

Potential Customer
-----------------------------------------------------------------------

A potential partner or service developer begins to fill in information
on the registration forms, but does not follow through. This should be
handled by carefully planned ajax calls, potentially triggered by form
field focus changes.

	Category    Pipeline    Stage
	----------- ----------- -----------------------
	SDA         SDA         1. Preparation stage
	FPA         FPA         1. Preparation stage
	FPA (CRA)   FPA (CRA)   1. Preparation stage

Customer Data Gathering
---------------------------------------------------------------------------------

A potential partner or service developer fills in the information on the
registration forms and submits them.

	Category    Pipeline    Stage
	----------- ----------- -----------------------
	SDA         SDA         2. Contract creation
	FPA         FPA         2. Contract creation
	FPA (CRA)   FPA (CRA)   2. Contract creation

Contract signature
-----------------------------------------------------------------------

The contract with a partner or service developer comes back from the
signature platform correctly signed by all involved parties.

	Category    Pipeline    Stage
	----------- ----------- -----------------------
	SDA         SDA         3. Contract approval
	FPA         FPA         3. Contract approval
	FPA (CRA)   FPA (CRA)   3. Contract approval

E-Commerce
====================================

1 Drupal Commerce <https://www.drupal.org/project/commerce>

-   Integrations to finnish bank payments exist, are done by people from
    Druid and can be at least partially used on digital signature
    <https://www.drupal.org/project/commerce_suomenverkkomaksut>
-   Well supported, lot of developers working to make Commerce better
-   Might be a bit overkill, depending on what we want
-   FORGE Theme can be applied easily
-   Basic tools (shopping-cart, payments, vat-handling, modifications to
    content types) roughly in 1-2 sprints
-   Restricted views should be easily done with existing tools
-   Few existing open-source tools for SAML-identification. Druid has
    handled Shibboleth (SAML 2.0) authentications for f.ex. University
    of Helsinki and Hanken.
-   * <https://www.drupal.org/project/shib_auth>
-   * <https://www.drupal.org/project/simplesamlphp_auth>
-   Integrations to major Finnish, European and Asian banking systems
    exist
-   No difference to current setup. All needed things can be added as
    plugins (=contrib modules in Drupal language)
-   Current content can be used as part of products

2 Drupal Übercart <https://www.drupal.org/project/ubercart>

-   Integrations to finnish bank payments does not exist
-   Not so well supported as Commerce, only few active developers
-   Maybe better scale for our project than in Commerce, of course
    depending on what we really want to do
-   FORGE Theme can be applied easily
-   Basic tools (shopping-cart, payments, vat-handling, modifications to
    content types) roughly in 1-2 sprints
-   Restricted views should be easily done with existing tools
-   Few existing open-source tools for SAML-identification. Druid has
    handled Shibboleth (SAML 2.0) authentications for f.ex. University
    of Helsinki and Hanken.
-   * <https://www.drupal.org/project/shib_auth>
-   * <https://www.drupal.org/project/simplesamlphp_auth>
-   Integrations to major European and Asian banking systems exist
-   No difference to current setup. All needed things can be added as
    plugins (=contrib modules in Drupal language)
-   Current content can be used as part of products

3 Magento <https://www.magento.com/>

-   Integrations to finnish bank payment systems exist
-   Completely different installation to Drupal
-   Integration tool for Drupal exist
-   A bit old technique, former proprietary CMS rewritten in Zend.
    Looking a bit harsh and even ugly
-   Integration to Drupal could cost some money
-   FORGE Theme must be written from start
-   Basic tools (magento-installation, theme, shopping-cart, payments,
    vat-handling, modifications to content types) roughly in 2-4 sprints
-   REST APIs to handle moving content roughly 1-2 sprints.
-   Restricted views should be easily done with existing tools
-   Possible to handle SAML-identification with SimpleSAMLPHP, but
    needs customizing.
-   Integrations to major Finnish, European and Asian banking systems
    exist
-   No changes needed to current Drupal installation as it would be
    completely separate installation. Relevant content should be moved
    via REST APIs between Drupal and Magento
-   Current content can be used as part of products

4 Custom Talked with Fraktio

-   Integrations to finnish bank payment systems exist
-   Fully custom
-   Could cost a lot of money because of fully custom
-   Integrations to Drupal via REST APIs (=good)
-   FORGE Theme must be written from start
-   Basic tools (custom-coding, theme, shopping-cart, payments,
    vat-handling, modifications to content types) roughly in 3+ sprints
-   REST APIs to handle content roughly 1-2 sprints.
-   Restricted views should be easily done with existing tools
-   Possible to handle SAML-identification with SimpleSAMLPHP, but
    needs customizing.
-   Integrations to major Finnish, European and Asian banking systems
    exist
-   No changes needed to current Drupal installation as it would be
    completely separate installation. Relevant content should be moved
    via REST APIs between Drupal and Magento
-   Current content can be used as part of products

** THIS IS NOT COMPLETED

List of Requirements/things that may affect platform choise:
--------------------------------------------------------------------------------------------------------------------------------------

Multivendor support availability, vendor management features in
multivendor environment, available analytics for vendors
 +Restricted views functionality (e.g. sign in to see prices)
 Item description flexibility - can we use current content fields for
product/service/organization descriptions
 +Integration to Finnish and major European banking/credit card systems
 +Integration to public sector identity management system (SAML2.0?)
 + Effect on sw development and system integration compared to current
HA Drupal setup
 +Applying the Forge theme
 +Rough estimate of amount of work required to move to new platform
 Activeness of the developer community/likely future development of the
platform/newness of technology

Hadoop
=========================

Hadoop data input
-----------------------------------------------

Options:

-   WebHDFS (REST) API
    <http://hadoop.apache.org/docs/r1.0.4/webhdfs.html>
-   Copy (scp) files to the virtual machine, then use CLI tools to copy
    from local FS to HDFS
-   Pipe data from local machine over ssh into Hadoop put command
    reading from stdin
    -   `cat foo | ssh user@host "hadoop fs -put - bar"`
-   Install the Hadoop tools to local machine and configure to
    communicate directly with the Hadoop instance
    -   Mainly, set the `fs.default.name` in `hadoop-site.xml`

HDFS CLI
-----------------------------

List files.
 ` hadoop fs -ls .`

Copy files to/from local filesystem to/from HDFS.
 ` hadoop fs -put /home/<USERNAME>/hugefile.txt /user/<USERNAME>/hugefile.txt`

Copy multiple files from source directory, concatenated into single
file.

` hadoop fs -getmerge hdfs://localhost:9000/user/<USERNAME>/lots-of-huge-files/ file:///<USERNAME>/merged-files.txt`

Create directory.
 ` hadoop fs -mkdir /user/<USERNAME>/garbage`

Remove directory.
 ` hadoop fs -rmr /user/<USERNAME>/garbage`

Run jar file against source and target directories in HDFS tree.

` hadoop jar hadoop-examples-1.2.1.jar wordcount /user/<USERNAME>/lots-of-books /user/<USERNAME>/lots-of-books-output`

View HDFS file contents.
 ` hadoop fs -cat /user/<USERNAME>/lots-of-books-output/part-r-00000`

Heatmap
============================

Architecture draft for data gathering and processing
----------------------------------------------------------------------------------------------------------------------

### Software

-   Mouse movement tracking SW
    -   heatmap.js ( <http://www.patrick-wied.at/static/heatmapjs/> )
-   Web server to send mouse position values to
    -   Use existing Drupal/Apache2
-   Intermediate storage for values
    -   redis ( <http://redis.io/> )
-   SW for processing intermediate values
    -   Hadoop ( <http://hadoop.apache.org/> )
-   Storage for accumulated values
    -   Hadoop ( <http://hadoop.apache.org/> )
-   Heatmap drawing SW
    -   heatmap.js ( <http://www.patrick-wied.at/static/heatmapjs/> )
-   Web server to draw and present results on
    -   Use existing Drupal/Apache2? Or dedicated location on
        analytics.forgeservicelab.fi?

### Architecture description

The following depicts the general flow of data in the heatmap data
gathering and processing architecture.

![Architecture
diagram](/files/path3149.png)

**Phase 1**

Tracking software captures user's mouse movements and sends them to web
server when browsing session ends, timeouts or the size of tracked data
exceeds a threshold. Each page to be tracked needs to have a
&lt;canvas&gt; element that encapsulates desired tracking area. By
default, the tracking area is the whole page. On window resize, capture
is stopped, optionally followed by canvas size readjusted with
JavaScript and restart of capture.

Data is sent inside a HTTP POST request which contains at least:

-   URL of the page the data was tracked from
-   Size of the canvas element at the time of capture
-   Array of actual tracking data in JSON format

Data should be sent over via HTTPS, especially if additional,
user-identifying attributes (timestamp, source IP) are considered for
capture.

**Phase 2**

Web Server is configured with a dedicated Location for handling the POST
request. The handler program will subsequently insert the data into a
Value Store. The JSON array from original capture is augmented so that
data to be inserted is in following (list) format:

` URL, canvas size, cursor position on X axis, cursor position on Y axis, weight`

**Phase 3**

When using hadoop, it's beneficial to transfer data in bigger chunks
over single connection vs. small chunks over many connections. Thus the
Value Store will run a program that periodically transfers content from
value store to HDFS. Transfer is done via WebHDFS. Successfully
transferred data is deleted from the Value Store. Value store can run on
a dedicated host, or on the same server as the Web Server.

Data will initially be uploaded into temporary files of format
`movement.TIMESTAMP` where TIMESTAMP is the transmission UNIX timestamp,
generated in Value Store.

Data is stored into HDFS in a structure similar to that of the original
site. For example root of forgeservicelab.fi site will generate files of
format `/user/heatmap/forgeservicelab.fi/movement.1426085150`

**Phase 4**

JobTracker periodically executes a MapReduce job (Java or JaQL) whose
target is to scan result directories for temporary files and aggregate
the results into a master file. The master file of each directory is of
the format `movement.master`, e.g.
`/user/heatmap/forgeservicelab.fi/movement.master`.

By default the MapReduce job will perform purely linear addition. So if
a certain x/y coordinate has existing weight of 3 and an incoming
temporary file has weight 7 for the same x/y coordinate, net result will
be weight 10. If a (globally specified) weight maximum is met, the
weight will not be incremented further.

An additional tool will most likely be needed to perform the following
maintenance tasks:

-   Reset of weight data for a single page or all pages
-   Readjust of weight maximum.

**Phase 5**

Heatmap Server will periodically scan HDFS for master files, and when
found, perform following actions:

-   Download corresponding pages' content
-   Inject Heatmap JavaScript into page
-   Render page with e.g. headless WebKit software
    -   Insert Heatmap data from master file into Heatmap instance
    -   Use single, predefined resolution/viewport size
    -   Data whose canvas size is different than selected resolution
        will be scaled
-   Save result as movement.JPG into Heatmap Server with similar
    directory structure as in HDFS.

Feasibility Study
------------------------------------------------

Following presents results from feasibility study between 3 different
OSS software for producing website heatmap data.

-   <http://www.patrick-wied.at/static/heatmapjs/> (Capture, draw)

    -   Latest release: Aug 2014
    -   License: MIT
    -   Browser support: Anything that understands HTML5 canvas
    -   Server-side requirements: DIY
        -   For example ...
        -   Track with Heatmap.js, store & aggregate in MySQL, draw with
            Heatmap.js
        -   Track with smt (simple mouse tracking), store aggregate in
            MySQL, draw with Heatmap.js
        -   Track with Lil Brother, aggregate with Solr, draw with
            Heatmap.js
    -   Data exportable as JSON object or base64 encoded image/png
    -   Nice demo by HSL at <http://hslheatmap.ampli.fi/>
-   <http://www.labsmedia.com/clickheat/index.html> (Capture,
    store, draw)

    -   Latest release: 2011
    -   License: GPL
    -   Browser support: Any browser with Javascript
    -   Server side requirements: Apache/Lighttpd + PHP + GD2
    -   Unofficial Piwik plugin exists
        <http://www.labsmedia.com/clickheat/piwik/piwik-clickheat.tar.gz>
        -   "We tried ClickHeat in 2011 and it worked fine for a while
            but didn't scale. ClickHeat attempts to store its log files
            in directories under a common directory. Unfortunately, when
            the number of pages is large, this flat structure exceeds
            the Linux OS's limit of 32k items per directory."
        -   Workaround to this issue exists by using page groups
    -   Their own demo at
        <http://www.labsmedia.com/admin/clickheat/index.php> is not
        working ...
-   <http://www.openwebanalytics.com/> (Capture, store, draw)

    -   Latest (maintenance) release: Feb 2014
    -   License: GPL
    -   Browser support: "All major versions of most web browsers"
    -   Server side requirements: MySQL, PHP
    -   Provides much more than just heatmaps (e.g. Piwik competitor)
    -   Overkill to deploy alongside Piwik for only mouse/click tracking
        and heatmaps

One thing to consider is can Piwik, which Forge already has in place,
perform some or all of the functionality required from heatmaps.

-   What about Piwik?
    -   No official support for heatmap as native functionality or
        plugin
    -   No roadmap plans for heatmap
    -   Does Piwik "overlay" offer some of the functionality of
        heatmaps?
        -   <http://piwik.org/docs/page-overlay/>
    -   Does Piwik "content tracking" offer some of the functionality of
        heatmaps?
        -   <http://piwik.org/docs/content-tracking/>

Architecture for KaPA compatible development
===========================================================================================================================================

The following picture is divided into two parts. The upper part depicts
what is considered feasible to compelete during FORGE Release_2015-06. The
lower part describes future development items.

![](/files/kapa.png)

1) Direct host-to-host communication
--------------------------------------------------------------------------------------------------------------------------

This we can support immediately after FORGE example test service has
been installed into permanent location and sufficient processes and
documentation (e.g. for WSDL descriptions) have been written.

Service developers are segregated by manual Security Group entries.

Communication is SOAP/HTTP or SOAP/HTTPS with no central party to sign
certificates.

2) Communication via Facsimile Secure Server
------------------------------------------------------------------------------------------------------------------------------------------

This requires development of software that at bare minimum keeps track
of Organization and Subsystem identifiers, and entry points for each
Service Developer. Service description WSDLs are provided by a URI.
Potentially all this information could be retrieved from the URI.

Service developers are segregated by service-subsystem mapping, or
alternatively a simpler subsystem-subsystem mapping. Additionally,
Security Group entries are manually opened from SD development host to
FSS.

Communication is SOAP/HTTP or SOAP/HTTPS with no central party to sign
certificates.

3) Communication via KaPA Secure Server
--------------------------------------------------------------------------------------------------------------------------------

This requires development of processes for Organization and Subsystem
registration where DIGILE acts as broker. Potentially also forms/service
portal.

Service developers are segregated by X-Road builtin subsystem &lt;-&gt;
client SSL certificate mapping. Additional segregation is done by
Security Groups (unless it is decided that SOAP transport ports are open
from all hosts to all hosts within FORGE environment).

Communication is SOAP/HTTP or SOAP/HTTPS. VRK signs Secure Server to
KaPA facing certs. FORGE environment certs are either self signed or
DIGILE signed.

4) Enterprise Service Bus as fallback option to KaPA
----------------------------------------------------------------------------------------------------------------------------------------------------------

This requires developing an ESB solution with features corresponding to
KaPA. (Authentication, message transport, PKI, supporting organization)

Service developers are segregated by existing multi-tenancy
functionality provided by the ESB solution or homegrown multi-tenancy
solution.

Communication can be based on SOAP or any other protocol readily
supported by the ESB solution or for which it is desireable to develop
support.

KaPA ESB Feasiblity
=================================================================

Big picture
-------------------------------------------------

Assumption is that public sector doesn't have plans to create an
ecosystem for private companies to use KaPA. In order to have
foundations for such an ecosystem, private companies need an easy,
trusted and supported way to connect to KaPA. The licencing terms of
connecting services and utilizing KaPA are not clear, therefore there
could be a "gateway" that would provide clear licencing terms.

Objective
---------------------------------------------

The objective is to study how a simple digital service (ESB-KAPA App)
could use ESB to talk to existing service (KaPA Service) that is
connected directly to KaPA. Therefore the study is two fold. First it
should be studied how a simple digital service (KaPA App) can be
connected to KaPA so that it's capable of talking to another service
connected to KaPA. Then it should be studied how an ESB (ESBGW) can be
connected to KaPA so that it offers an ESB gateway for simple digital
service (ESB-KAPA App) to KaPA.

![](/files/xroadesb.png)

Plan
-----------------------------------

1.  Connect a simple digital demo service to KaPA and make it talk to
    another service connected to KaPA e.g. echo service (assuming it
    exists on KaPA). Demonstrate, create an example and documentation.
2.  Connect ESB to KaPA. Demonstrate, create an example
    and documentation.
3.  Connect a simple digital service to ESB and make it talk to another
    service connected to KaPA. Demonstrate, create an example
    and documentation.

Test environment
-----------------------------------------------------------

The KaPA test environment consists initially of two Secure Server hosts
running Ubuntu 14.04:

-   forgess00.forgeservicelab.fi
    -   WebUI username: (USERNAME REMOVED)
    -   Password: (PASSWORD)
    -   Softtoken PIN: 12456789
-   forgess00-test.forgeservicelab.fi
    -   WebUI username: (USERNAME REMOVED)
    -   Password: (PASSWORD)
    -   Softtoken PIN: 12456789

The hostnames contain the word "forge" due to VRK rules. Development is
initially done on the 2nd system and completed increments are rolled out
to the 1st system. Currently, subsystems are registered to forges00-test
only.

### Secure server installation

The following procedure is/was used to install the Secure Server:

1.  Install base OS (Ubuntu 14.04)
2.  Run Ansible playbook `kapa-secureserver` (
    <https://git.forgeservicelab.fi/ansible/kapa-secureserver> ) against
    target host. Please note that it's important to use FQDN in Ansible
    inventory file to get the self-signed cert generated per that FQDN
3.  After playbook has finished, wait a couple of minutes to allow
    software to start
4.  Log in to https://server:4000/
5.  Upload configuration anchor provided by VRK (with accompanying
    parameters - paying close attention that hostname part in Security
    Server Code matches the hostname of the server)
6.  Configure timestamping service
7.  Create Certificate Signing Requests for VRK
8.  Upload certificates provided by VRK.

It is to be investigated can the CSR be generated externally e.g. with
OpenSSL, and can a non-VRK signed certificate be used for the Web UI.

### Service registration

The following procedure is used to attach services to a Secure Server:

1.  Send subsystem addition request to <palveluvayla@palveluvayla.fi>
    with following information:
    -   Organization name: Digile
    -   FQDN of Secure Server hosting subsystem e.g.
        forgess00.forgeservicelab.fi
    -   Name of subsystem to add e.g. FORGEDemo
    -   Purpose of subsystem e.g. development, public database, etc.

2.  Wait at maximum one business day for the system to get added to
    global list
3.  Navigate to Security Server Clients -&gt; "ADD CLIENT"
4.  Select "SELECT CLIENT FROM GLOBAL LIST"
5.  Perform search with empty input
6.  Select subsystem from list
7.  Confirm subsystem registration request - client icon should change
    from hollow yellow dot to filled yellow dot
8.  Once registration has been accepted, client icon changes to
    green dot.

### Phase 1 - Example request

Once organization and subsystem have been successfully registered to
Secure Server, requests can be transmitted between the client and a test
service. The following contains instructions for making a test request
to DIGILE's Test Service with a dedicated playbook.

1.  Retrieve test playbook from
    <https://git.forgeservicelab.fi/ansible/kapa-testapp>
2.  Modify the group_vars/all.yml file so it contains your organization
    and subsystem identifiers (these can also be provided via -e
    extra_vars from CLI)
3.  Run playbook with:

		ansible-playbook -i inventory.txt kapa-testapp.yml 

The ansible ssh username is inserted to the body of the request. If the
reply doesn't contain said username, the playbook will report failure.

### Phase 2

Notes:

Test instance admin password is (PASSWORD)

References
-----------------------------------------------

1.  KaPA: Kansallinen palveluväylä
    <https://confluence.csc.fi/pages/viewpage.action?pageId=37816865>
2.  ESB: Zato ESB <https://zato.io/>

Test service transition to KaPA
=======================================================================================================

A test service can be attached to a KaPA Security Server at any time.

Requirements
-----------------------------------------------------------------

-   Service Developer Organization ID added into KaPA central directory
-   Service Developer Subsystem ID for test service added into KaPA
    central directory
-   Linux host for running the test service
-   Linux host for testing the test service

**TBD** How identifiers are registered (Digile vs. KaPA).

Publishing the service description
-------------------------------------------------------------------------------------------------------------

As part of creating the test service, a service URL was defined. The
WSDL description of the service is accessible by adding a `?wsdl` suffix
to the URL, resulting in something similar to
`http://testservice.forgeservicelab.fi:8080/TestService/Endpoint?wsdl`.
Once this URL has been associated to a particular Subsystem and Clients
in the KaPA Secure Server, requests coming from the KaPA bus can be
relayed to the service.

**TBD** Will Service Developer provide WSDL to DIGILE who then adds them
to SS? Or can this be scripted and provided via form/portal? Or will
later versions of X-Road software allow self-service?

Ensuring connectivity
-----------------------------------------------------------------------------------

Once the WSDL has been added to the secure server and allowed Clients
defined, the last step is to verify that the relevant ports 5500 and
5577 are open from the FORGE Secure Server towards the Secure Server
which is hosting the Test Client. Requests made in the boundaries of the
FORGE environment should traverse without additional configuration
changes, but for external clients opening the firewall may be necessary.

**TBD** Process of client requesting externall SS access to a service
behind FORGE SS.

Testing service
-----------------------------------------------------------------------

Once the service has been properly registered to the secure server, the
Test Application can be used to verify the end-to-end path from client to secure server
to service. The main difference is that the request is made to the
secure server instead of the test service directly. This may require the
use of client-side certificates in future versions of KaPA. The example
here is based on self-signed certificate on the server side, which the
test app ignores (python request is POSTed with a verify=False flag).

    $ python files/kapa-testapp.py -i FI-DEV -l COM -c 0785944-0 -s FORGEDemo -t https://forgess00.forgeservicelab.fi 
                                   -m COM -e 0785944-0 -y TestService -n http://forge-test.x-road.fi/producer
    Received response: Hello test_string! Greetings from adapter server!
    $ 

KaPA Use cases
==================================

KaPA real (REJECTED)
======================================================

ServiceDeveloper wants to easily connect KaPA trough FORGE ServiceLab so
that he doesn't have to install and maintain his own Secure Server.
Realistic use case based on current understanding.

![](/files/uc-kapa-real.png)

KaPA easy (REJECTED)
======================================================

ServiceDeveloper wants to easily connect KaPA trough FORGE ServiceLab so
that he doesn't have to install and maintain his own Secure Server.
Dream use case which makes multi-tenancy easy.

![](/files/uc-kapa-easy.png)

ESB (REJECTED)
==========================================

ServiceDevelopers should be able to benefit and develop on ESB even if
KaPA is not working or not taking off.

ESB-KaPA (REJECTED)
====================================================

ServiceDevelopers should be able to benefit and develop and use KaPA
trough ESB even if KaPA is not working or not taking off.

KaPA compliant messaging (SELECTED)
====================================================================================

ServiceDevelopers should be able to develop services that can talk to
each other using KaPA compliant messaging (possibly excluding security
checks)

![](/files/uc-kapa-messaging.png)

Digital-signature
==========================================================

Digital Signature study was made by comparing two online digital
signature services
 1. Onnistuu.fi
 2. Signicat

Onnistuu.fi
---------------------------------------------

Onnistuu.fi is finnish digital signature service. Their API is easy to
use. Onnistu.fi doesn't have that much functionality on their service
but as an finnish person there's everything needed to share documents in
easy to people where only information you must have about them is an
email-address. Onnistuu.fi currently supports only Tupas authentication.
According to their sales they're getting estonian payment methods to
their service this year.

Onnistuu.fi customer service works well for us. Our opinion on
that might a bit biased compared as we can just walk to meet the lead
developer of service and ask what's going on. Still, I've understood
that their response time via email is on reasonable level for everyone.

Signicat
----------------------------------------

Signicat is norwegian digital signature service. Their API is quite
complex and hard to use. Their documentation is also relatively hard to
read and we've found some bugs from it. Signicats service allows people
to do a lot more than onnistuu.fi. With Signicat it's also possible to
create a dumb form with email-field or several email-fields to share the
document to be signed to a people or group of people. Meaning only
information of signer you need is an email address.

Signicat customer service has been good but a bit slow. Our usual
development day with Signicat has worked like we develop something for
few hours, we mail them to ask information, we wait for few days for an
answer and then back to development table for few hours. I don't think
this is making Signicat as expensive to develop after all. Once the
module for the service has been created the module should be very
stable. I'm not expecting Signicat to change their API in any way in
near future and that's also a message we've got from their sales and
development team.

Signicat has coverage for sign-in methods in all over the world. While
writing this documentation support.signicat.com was down so I couldn't
get a complete list but I'll try to add it afterwards.

There is no possibilities to use Signicat archive with TUPAS
(authentication method created by the Federation of Finnish Financial
Services and used by all major Finnish banks) in testing environment. If
we need to test it we need to to use example Norwegian bank
authentication method.

### Pros and cons in short

Onnistuu.fi

  * +Easy do develop
  * +Cheap do develop
  * +Must have access to document being signed. On FORGE we're limiting the
documents currently by user and we had to open all contract PDF's to
onnistuu.fis IP-address. It's not anything bad, but in the end of the
day it's a potential security thread anyways.
  * -Not much functionalities. No idea what it would cost if we want to do
something that can't be done with onnistuu.fi out of the box.
  * -Only finnish authentication methods

Signicat


  * +Easy to develop
  * +A lot of options around. I tried to created different kind of
scenarios in my head and every single one of these could be handled with
Signicat.
  * +A lot of options how documentation can be signed from all over the
  world
  * -Customer service is a bit slow
  * -We haven't been able to actually test all services needed, because the
current test account Signicat has provided to us does not have
possibility to tupas-authenticate itself to a Signicat service called
Document Archive. Document Archive is a place where the final document
with all signatures is being placed. We've asked access to document
archive on 25.09.2014 but by morning of 03.10.2014 we don't have the
access.

Signup process
=================================================

Background
-----------------------------------------

-   CRM tool is used to manage opportunities, people and their
    organizations belonging to those opportunities
-   LDAP is used to provide data for authentication and authorization
    and tenants
-   Drupal provides means for signees to complete signup and contract
    creation
-   Signing service helps Drupal to provide means for signees to
    digitally sign the contract
-   Notification messages are defined in and coming from the signing
    service

Sequence diagram (NEW)
---------------------------------------------------------------

Sequence diagram (OBSOLETE)
-------------------------------------------------------------------------

![](/files/signup.png)

Documenting
========================================

Wiki
--------------------------

Redmine/FORGE Support - Public wiki for service developers
Redmine/FORGE - FORGE project's internal wiki

Videoediting on Windows
----------------------------------------------------------------

### Videorecording tools

On Windows the selected tool is Microsoft Expression Encoder 4 due to
its quality.
 For Audio recording, the default tools that most operating systems pack
are good enough.
 In any case, as long as quality AVI video and WAV audio is produced,
there is no strict rule on the tools to use.

-   Microsoft Expression Encoder 4 (Windows) - ability to create 10min
    captures only with the free version)
-   CamStudio (Windows) - might create choppy videos that are uneditable

### Desktop video editing tools

-   Cyberlink PowerDirector 12 (99€)
-   Lightworks (Windows, Linux, Mac) is very picky about the codecs used
    in the source material. LW might create choppy videos, and the root
    cause is unknown.
-   In any other scenarios, anything that can produce AVI video and/or
    WAV audio.

### Audio tools

-   Use DIGILE's audio recorder appliance to record audio clips
-   Default tools for audio and Audacity for more sophisticated audio
    construction

### Source format

-   Same than output format (Microsoft Expression Encoder can produce
    WMV files only, but they are editable with most video editors)

### Instructions

-   Create a bunch of scene specific source video clips (with Microsoft
    Expression Encoder) rather than just one long shot. It's then lot
    easier and faster to edit videos and combine scenes correctly.
-   The descriptive naming of the scenes is important so that the editor
    knows what scene belongs to what narration. E.g. have the recording
    name "01_entering_to_forge_web.mp4" rather than "file1.mp4"
-   Create a bunch of audio clips (with DIGILE audio recorder appliance)
    rather than one long shot. It's easy to cut and tune audio clips
    with Audacity and then place them in order with the video editor
-   Import media files to the video editor (Cyberlink PowerDirector),
    edit the video and export it to output format

### Output format

-   720p, 1280x720, H.264, 16:9, 25fps, mp4 or m4v (Youtube HD format)

Videoediting on Linux
------------------------------------------------------------

### Videorecording tools

Selected Kazam Screencaster on linux, since it is the only option that
consistently captures quality videos without glitches. It integrates
with OpenShot for instant editing after capture, this is Kazam pipes the
raw video capture to OpenShot after finishing the recording. This step
is recommended to generate the required AVI source videos for later
edition.
 For Audio recording, the default tools that most operating systems pack
are good enough.
 In any case, as long as quality AVI video and WAV audio is produced,
there is no strict rule on the tools to use.

-   Kazam Screencaster

### Desktop video editing tools

-   OpenShot (Linux)
-   In any other scenarios, anything that can produce AVI video and/or
    WAV audio.

### Audio tools

-   Use DIGILE's audio recorder appliance to record audio clips
-   Default tools for audio and Audacity for more sophisticated audio
    construction

### Source format

-   Same than output format
-   It's a good idea to have a sources as bunch of scene specific
    recordings rather than just one long shot. It's then lot easier and
    faster to edit videos and combine scenes correctly.
-   The descriptive naming of the scenes is important so that the editor
    knows what scene belongs to what narration. E.g. have the recording
    name "01_entering_to_forge_web.mp4" rather than "file1.mp4"

### Output format

-   720p, 1280x720, H.264, 16:9, 25fps, mp4 or m4v (Youtube HD format)

### Instructions

-   Create a bunch of scene specific source video clips (with Kazam)
    rather than just one long shot. It's then lot easier and faster to
    edit videos and combine scenes correctly.
-   The descriptive naming of the scenes is important so that the editor
    knows what scene belongs to what narration. E.g. have the recording
    name "01_entering_to_forge_web.mp4" rather than "file1.mp4"
-   Create a bunch of audio clips (with DIGILE audio recorder appliance)
    rather than one long shot. It's easy to cut and tune audio clips
    with Audacity and then place them in order with the video editor
-   Import media files to the video editor (OpenShot), edit the video
    and export to output format

Service breaks and announcements
=======================================================================================================

-   The purpose of the announcement is **to inform FORGE Service Lab
    users** about planned and surprise breaks in service use and to
    inform about changes in FORGE Service Lab.
-   The [Incident Management
    process](#incident-management)

Policy
---------------------------------------------------

-   To announce about planned breaks and surprise breaks in service
-   Surprise breaks should be announced without delay
-   Service break announcements about **planned** breaks must be given
    **5 days** in advance
-   Breaks should be planned off working or so that there is the least
    amount of impact for users
-   See the communications matrix below to check if the announcements
    requires an approval before sending
-   **CSC** makes all the announcements related to **IaaS** (OpenStack)

Tools and methods
-------------------------------------------------------------------------

-   FORGE Service Lab - **News**

    -   Redmine is patched so that everybody will receive email regardless of their "My
    account" setting.
    -   [Add
        news](https://support.forgeservicelab.fi/projects/forums/news/new)

-   FORGE Service Lab - **Forums** to be used for collaboration and
    dicussions

    -   To be used for collaboration and communication trough forums
    -   [Forums](https://support.forgeservicelab.fi/projects/forums/boards)

Access to resources
-----------------------------------------------------------------------------

Different Affiliate roles have different access to FORGE services. The
access is described in [Access_to_resources](#access-to-resources)

Communications matrix
---------------------------------------------------------------------------------

| project | members | who can join | purpose | who can post | approval |
| ----- | ---- | -----   | -----   | ----- | -------- | -----   |
| FORGE Support - wiki | digile,csc,ke,druid,servicedevelopers | Technical contacts and service developers from LDAP | wiki | digile, csc, ke, druid |  |
| FORGE Service Lab - news | All | All affiliate roles and users from LDAP | Service breaks and FORGE announcements | (USERNAMES REMOVED)| (USERNAMES REMOVED) |
| FORGE Service Lab - forums | All | All affiliate roles and users from LDAP | Collaboration and dicussion using forums | All |  |


Service break announcement template
-------------------------------------------------------------------------------------------------------------

    Subject: Maintenance break on Monday 2014-02-10

    Dear FORGE Service Lab user,

    This announcement concerns FORGE Service Lab IaaS users only. [Please indicate here if the news concerns IaaS users only. Otherwise, if it concerns everybody, then remove this row]

    We wanted to inform you about maintenance that may cause periodic breaks in the availability of the services.
    The maintenance will take place between 2014-02-03 08.00 and 2014-02-04 24.00 UTC+2 (Helsinki)
    The virtual machines may be suspended and may become inaccessible during the break.
    This maintenance break requires no action from you.

    We apologize for the possible inconvenience and will do our best to ensure smooth operation of the service as soon as possible. We will keep you informed.


    Best regards,
    FORGE Service Lab Support
    support@forgeservicelab.fi

Note!

-   UTC+2 Winter time
-   UTC+3 Summer time. The last Sunday of March - the last Sunday of
    October
-   All news are received by all affiliate roles. Since partners are not
    interested in IaaS announcements we should indicate if the
    announcement doesn't concern them. So, please add it to the
    announcement if the announcement concerns IaaS users only.

Examples
-------------------------------------------------------

### Planned breaks in IaaS service use (CSC announces)

-   If the IaaS service break can be planned in advance, the users must
    be given reasonable amount of time to prepare for the break. Also,
    the timing of the break should be planned to be at the time when
    there are least amount of use in service. The users must also be
    informed when the break is over.
-   Method: FORGE Service Lab - **news**

### Planned breaks in Redmine, Git, xmpp or Auth service use (DIGILE or KE announces)

-   If the service break can be planned in advance, the users must be
    given reasonable amount of time to prepare for the break. Also, the
    timing of the break should be planned to be at the time when there
    are least amount of use in service. The users must also be informed
    when the break is over.
-   Method: FORGE Service Lab - **news**

### Surprise breaks in IaaS service use when the impact is visible also in public FORGE WEB, Plaza or Dashboard (CSC announces)

-   If there is ongoing unplanned surprise break in the service, then
    the users must be informed ASAP. The users must also be informed
    when the break is over.
-   Method: FORGE Service Lab - **news**

### Surprise breaks in IaaS service use (CSC announces)

-   If there is ongoing unplanned surprise break in the service, then
    the users must be informed ASAP. The users must also be informed
    when the break is over.
-   Method: FORGE Service Lab - **news**

### Minor issue which impacts on users (DIGILE or CSC announces)

-   If there changes in forge functionality that potentially have an
    impact on forge users (e.g. change in api...) but which don't cause
    service downtime, then the announcement is to be made using news.
-   Method: **FORGE Service Lab - news**

### Significant announcement (DIGILE announces)

-   If there changes in forge functionality that is significant for
    forge users (e.g. significant change), then the announcement is to
    be made using news.
-   Method: FORGE Service Lab - **news**

### Minor announcement or minor issue, which does not impact on users (DIGILE or CSC announces)

-   If there are minor announcements or minor changes in forge
    functionality that don't have an impact on forge users (e.g.
    new features) and which don't cause service downtime, then the
    announcement is to be made using forums.
-   Method: FORGE Service Lab - **forums**

Training solution
==========================================================

Training request
--------------------------------------------------------

1.  Technical contact may submit a training request as a support ticket
    in Redmine
2.  FAP checks that the ticket was originated by the technical contact
    and if yes then re-associates the training request issue to whole
    digile team. Otherwise if the ticket didn't come from the technical
    contact, then FAP responds according to normal procedure.
3.  Digile team associates the training request issue in Redmine to the
    responsible person (trainer) who then organizes the the training
    according to the diagram

Organizing the training
----------------------------------------------------------------------

1.  The trainer contacts the one who requested the training and agrees
    upon the participants, content, setup, timing and
    other practicalities. Note! the list of participants' emails so that
    enrollment info can be provided
2.  The trainer books the facilities (showroom or external facilities)
    and orders snacks, fruits, coffee and tea depending on the agreed
    setup
3.  The trainer creates a registration form as follows
    -   Make a copy of the desired training registration template.
    -   Rename the copy so that it has a date in iso format as prefix in
        the title. E.g. "2014-10-31 FORGE CLI training", move it to the
        same folder where templates are and then modify the start time
        and end time in the details section
    -   When the form is ready, click "Send form" and add the
        participants emails

4.  The trainer resolves the training request issue in Redmine by
    putting the link to the registration form as part of the issue and
    then marks the issue as resolved

Training
----------------------------------------

1.  One day prior to training or when the seats are full the trainer
    closes the registration by marking the form to "Not accepting
    responses" from the "Responses" menu
2.  The trainer fetches the enrollment information from the registration
    form he created
3.  The trainer sets up the environment if such is needed (at least
    OpenStack CLI training needs the environment)
4.  The trainer is waiting for the trainees in the Technopolis lobby and
    then hosts the training

After the training
------------------------------------------------------------

1.  The trainer sends the feedback form
    to the registered training participants and then learns from the
    feedback
2.  The trainer closes the training request issue in Redmine

Sequence diagram
--------------------------------------------------------

The training solution is illustrated in the attached sequence diagram
![](/files/training_solution.png)

Deployment pipeline
================================================================

Deployment pipeline illustrated
----------------------------------------------------------------------------------------

![Deployment
pipeline](/files/deploymentpipeline.png "Deployment pipeline")

Principles
----------------------------------------------

### Product backlog items

-   User stories, bugs and all must appear as backlog items
    -   If a feature is not written as a user story then the test
        automation is not possible and QA doesn't have information about
        what to test and eventually it's impossible to get the backlog
        item closed gracefully
-   The initial owner for the backlog items is Product Owner
    -   If the more appropriate destination for the bug is known, then
        the bug can be assigned to him
-   Critical bugs are the first priority for everybody
-   The next level priorities are indicated by the order of the items
    in backlog. Ordering of backlog items is the responsibility of PO.

### Testing

-   Acceptance testing is done against backlog items
-   Test automation should be used as much as possible both for the unit
    testing and acceptance testing
    -   If the testing of the product backlog item can be automated then
        it should be automated and added to the test asset
    -   If automation is not possible then resolved backlog items should
        contain information about how the issue was verified

### Deployment

-   Deployment may happen from the default branch anytime and even story
    by story
    -   So, it's important to keep default in a good shape always
-   If upstream code is used, then upstream code is cloned to gitlab as
    master branch
    -   No FORGE changes are being done into master branch but to FORGE
        branch instead (which is set as default)
    -   Later when both master and default have advanced they can be
        brought up to date by fetching master from upstream and merging
        to default while resolving merge conflicts
-   Don't have other remote branches unless there is a really good
    reason
-   Deployment to testing should be made automatic and to be triggered
    by push to default
-   Deployment to testing should revert back to previous in case
    deployment fails
-   Deployment to production is manual step (by PO) but deployment to
    production should revert back to previous in case deployment fails
-   Closing a story requires PO's acceptance
-   PO might decide to close untested story and PO should understand
    that the story might get reopened by QA

### Commits

-   Have small commits and preferrably just one commit per product
    backlog item
-   Commits messages should include a reference to a product backlog
    items in a form of \[R|r\]esolve\[s|d\] \#\\d+

### Documentation

-   All documentation, quidelines and such should go to wiki. Internal
    guidelines should go to FORGE wiki and external guidelines for FORGE
    service developers and affiliates should go to FORGE Support wiki.

### Setting up CI jobs

-   Use the separation of interest when defining build, deployment and
    testing jobs in Jenkins
-   E.g. have separate jobs for: Build, Deploy to Testing, Test, Deploy
    to Production

Introducing hotfixes
===================================================================

Hotfixes should be introduced via the usual deployment pipeline however,
it may be the case since we use the master branch for both testing (QA)
and production, that this branch has advanced beyond the point where a
deployment to production can be made via the usual channel without
introducing breaking changes. Let's study the case in point and how to
react to it.

Initial state
-----------------------------------------------------

![initial git tree](/files/Diagram1.png)

For this scenario, we're going to make a few assumptions on the diagram
above:

-   The second commit on the master branch is, as stated, deployed
    on production.
-   The production environment is in need of a hotfix patch.
-   The third commit on the master branch is in testing and not good
    for production.

In this situation we cannot apply the hotfix onto master's HEAD as would
be the normal practice because that would push the broken third commit
onto production. Here is what we'll do instead:

Branch-off the current master
-------------------------------------------------------------------------------------

![branched off master](/files/Diagram2.png)

Let's not worry about the `development` branch for the time being. To
introduce the hotfix and push it to production we need to branch off
`master` at two points in its history:

-   Branch off at `HEAD` into `master-defunct`, this branch will now
    contain the current history of `master`.
-   Branch off at `commit 2` into `hotfix`, this will be our working
    branch to introduce the hotfix.

At this point we are ready to apply all necessary patches on the
`hotfix` branch.

Reset master
---------------------------------------------------

![master reset](/files/Diagram3.png)

To apply the hotfix at the point in history that was deployed onto
production we need to reset the `master` branch to the deployed commit.
 Note that later history is preserved on the `master-defunct` branch.

Merge the hotfix
-----------------------------------------------------------

![merged hotfix](/files/Diagram4.png)

Once the hotfix patch is applied on the `hotfix` branch we are ready to
merge it into `master`. At this point the `master` branch will be at the
same point in history as the version deployed in production plus the
hotfix, which means that it can be deployed to production without
introducing other breaking changes.

Restore history
---------------------------------------------------------

![history restored](/files/Diagram5.png)

With the hotfix ready on the `master` branch and production patched, we
can now restore the ongoing work that was under testing before
hotfixing; to do that, we merge the `master-defunct` branch back into
`master`. Note how `master` is now at a point where it contains the
latest `development` merge from before the hotfix plus the hotfix patch
itself.

Branch off development
-----------------------------------------------------------------------

![devel branchoff](/files/Diagram6.png)

Coming back to the `development` branch, if it has evolved past the
commit where it was last merged into `master`, as shown in the diagram,
we'll branch it off at `HEAD` into `development-defunct` to preserve its
history.

Reset development
-------------------------------------------------------------

![reverted devel](/files/Diagram7.png)

After resetting `development` to the commit where it was last merged to
`master` we have the branches in a position where they are identical
except for the hotfix patch present in `master`.

Propagate the patch to development
-----------------------------------------------------------------------------------------------

![patched devel](/files/Diagram7a.png)

Since the branches are otherwise identical at this point, merging
`master` into `development` will introduce the hotfix patch into the
later. Note that the outstanding history from `development` is still
preserved in `development-defunct`.

Restore development history
---------------------------------------------------------------------------------

![devel restored](/files/Diagram8.png)

Merging the `development-defunct` branch into `development` will bring
back the commits that formerly put `development` ahead of `master`. At
this point both `master` and `development` are at the same point where
they used to be before the procedure but with the hotfix patch present
in both of them.

After verification, and if there are no other concerns, the following
work branches can be pruned:

-   `hotfix`
-   `master-defunct`
-   `development-defunct`

LoadTest Results
=======================================================

git.forgeservicelab.fi
-----------------------------------------------------------------

[Load Test Report for
git](/files/load_test_report_git.pdf)

PLAZA
---------------------------------

[Load Test Report for
testing.forgeservicelab.fi](/files/load_test_report_plaza_anonymous.pdf)

Redmine test env
=======================================================

<https://193.166.24.138:8443/>

You can access it with FORGE credentials

**Setup:**

-   Redmine 2.4
-   Mysql database (with production data updated in ~12/2013)
-   CentOS 6.4
-   LDAP (either Production through ssh-tunnels or own test
    LDAP instance)
-   redmine was installed by following these instructions:
    <http://www.redmine.org/projects/redmine/wiki/How_to_Install_Redmine_on_CentOS_%28Detailed%29>

**Get it up & running from snapshot**

-   Launch vm using
    *redmine_on_CentOS_6.4-x84_64_snap_update_v13* snapshot
    -   Apache should be started automatically with http (8080) and
        https (443 & 8443)
    -   Remember to add there ports to your **security group settings**
    -   **Default image uses LDAPproxy for authentication**
    -   Browse to https://yourvmip:8443

**If it does not work?**

-   You need to add your new VM ip to dbserver.forgeservicelab.fi
    /etc/postgresql/9.3/main/pg_hba.conf -file
-   After starting vm login with ~$ssh cloud-user@ip -i yourkey.pem
-   in vm console change to root user (with root environment)
    **(\~\$sudo su -)**
-   check that papache is up & running (\~\$netstat -tnlup |grep 8443)
-   Configure redmine to use correct LDAP (see below)
-   go to /var/www
    -   under *redmine2.4* is plain redmine installation
    -   under *redmine_production/redmine-2.2.4* is production like
        installation (except SSO is off & Look&Feel)
-   under wanted version of redmine start weBrick server by
    **\~\$RAILS_ENV=production bundle exec rackup -p 80**
    -   Now redmine should be open at port 80 on your VM

Update Snapshot
=====================================================

If you need to update CentOS snapshot here is a short todo list for vm:

	$ userdel cloud-user (It will be created with cloud-init script)
	$ rm -rf /home/cloud-user (or mv if needed after making snapshot)
	$ vim /etc/udev/rules.d/70-persistent-net.rules (remove/comment out eth interface configuration)
	$ mv /root/.ssh/authorized_keys /root/.ssh/authorized_keys.ORIG (after you have done the shapshot redo this vice versa)
	stop server processes (service xxx stop)

TestAccounts
===========================================

List of accounts & environment:

  --------------------------------------------------------------------------
| Environment  | URL                                       | Account role       | Account name    | Password 
|--------------|-------------------------------------------|--------------------|-----------------|---------
| Jenkins crypt | https://ci.forgeservicelab.fi             | encryption passwd  |                 | (PASSWORD)
| Test-Redmine | https://193.166.24.112:8443               | Production copy    | Production LDAP | N/A
| Test-Drupal  | https://testing.forgeservicelab.fi/ | Admin         | Digile/Druid users    |  N/A
| Test-Drupal  | https://testing.forgeservicelab.fi/ | Partner-admin         | (USERNAME REMOVED)    | (PASSWORD)
| Test-Drupal  | https://testing.forgeservicelab.fi/ | service devoper     | (USERNAME REMOVED)  | (PASSWORD)
| Test-Drupal  | https://testing.forgeservicelab.fi/ | regular partner        | (USERNAME REMOVED)     | (PASSWORD)
| Production LDAP and plaza test LDAP | all                                       | Service developer, ['technicalcontacts', 'developers', 'testservicedeveloperorg']  | (USERNAME REMOVED) | (PASSWORD)
| Production LDAP and plaza test LDAP | all                                       | Partner without OS, ['partners', 'testpartnerorg']  | (USERNAME REMOVED) | (PASSWORD)
| Production LDAP and plaza test LDAP | all                                       | Partner with OS, ['technicalcontacts', 'partnerscra', 'testpartnercraorg']   | (USERNAME REMOVED) | (PASSWORD)
| Production LDAP and plaza test LDAP | all                                       | JulkICT   | testjulkict | (PASSWORD)
| Jenkins CI | https://ci.forgeservicelab.fi | CI service | (USERNAME REMOVED) | (PASSWORD)

Test accounts in Redmine
-------------------------------------------------------------------

~~Please note that test accounts are from ldap and they belong to
Digile.Platform group. The accounts are marked as hidden in ldap and
therefore they are locked by default in Redmine. If the accounts are
needed in Redmine for testing purposes, one needs to enable a desired
locked account manually in Redmine under users setting. The enabled
account remains enabled as long as ldap sync script runs every 10mins
and disables the account again.~~

A servicedeveloper account is present in ldap and can be
used to check the Redmine project visibility and it should have access
to two Redmine projects: "FORGE Service Lab" and "FORGE Support". The
account is marked as hidden in ldap and locked by default by Redmine. An
account can be enabled manually in Redmine but will be automatically
disabled again in 10mins by ldap sync.

Role permissions on Drupal
-----------------------------------------------------------------------

Partner-admin, Partner/technical contact from LDAP point-of-view

 * Allowed to create organizations and offers
 * Allowed to edit own organizations and offers
   -   Not allowed to access Tutorial / Dashboard
   -   Not allowed to delete own content, just unpublish

Regular partner, Partner/non-tecnical contact

 * Allowed to see and comment all content on Plaza
 * Not allowed to create organizations and offers
 * Not allowed to edit own organizations content
 * Not allowed to access Tutorial / Dashboard

Service developer

 * Allowed to access Tutorial / Dashboard
 * Not allowed to create or edit any content

Accounts

 * testpartner = regular partner
 * testparnercra = Partner-admin
 * testservicedeveloper = service devoper


TestAutomation
=================================================

![Test
Automation](/files/test_automation.png)

------------------------------------------------------------------------

TestAutomation Asset
===================================================================

FORGE Servicelab test automation asset should increase in every sprint.
Every new story that is tested/verified manually should trigger actions
for automating those tests. Here is a steps for getting this done.

1.  QA manually tests story. In manual testing QA sees if test
    automation is reasonable.
2.  QA creates a new User Story to product backlog. This story contains
    information what tests should be automated.
3.  In next (or some other near future) sprint planning this story is
    taken in.
4.  QA will create test automation script for specified stories and add
    those scripts to jenkins Robot job.
5.  Tasks for creating test cases are assigned to PO/PM for validation.
    So that he/she can check that all necessary functionalities are
    added to regresion tests.

![FORGE Test automation asset sequence
diagram](/files/testautomation.png)

Custom flavor management
===============================================================================

**These operations can be performed on the admin server**

Creating new private flavor
-------------------------------------------------------------------------------------

    [you@admin:~] $ nova flavor-create --is-public false <flavor name> auto <RAM MB> <Disk GB> <vCPUs>

The flavor ID is a number from 1 to 255 and cannot contain special
characters or spaces. Auto means automatic ID and it generates uuid as
ID.
 Please make sure you use 1024MB = 1GB format when inputting RAM.

NOTE! All flavors need to have a tag. Currently this is either
"generic=true" for non-hadoop nodes or "hadoop=true" for hadoop nodes.
This is needed for working scheduling. This can be done with a command

    [you@admin:~] $ nova flavor-key m1.tiny set generic=true

If the command fails, use
<https://cloud.forgeservicelab.fi/dashboard/admin/flavors/> and click
More -&gt; View Extra Specs dropdown menu

Allowing access to private flavor
-------------------------------------------------------------------------------------------------

    [you@admin:~] $ nova flavor-access-add <flavor ID> <tenant name>

Flavor name is not enough, it needs to be the ID in order for this to
succeed.

Removing access to private flavor
-------------------------------------------------------------------------------------------------

    [you@admin:~] $ nova flavor-access-remove <flavor ID> <tenant name>

Listing access to private flavor
-----------------------------------------------------------------------------------------------

    [you@admin:~] $ nova flavor-access-list --flavor <flavor ID>

Listing all flavors
---------------------------------------------------------------------

    [you@admin:~] $ nova flavor-list --all

Deleting flavor
-------------------------------------------------------------

    [you@support:~] $ nova flavor-delete <flavor ID>


Quota editing
==============================================

Process for quota increase request is located
[here](#quota-increase-for-an-affiliate)

Requirements
--------------------------------------------

-   OpenStack RC File
-   Following python clients for all commands (all of these are
    installed on admin machine)
    -   python-novaclient installed
    -   python-neutronclient
    -   python-cinderclient
    -   python-swiftclient

**Ubuntu 12.04 users please note:**
 The version of the python-novaclient tools packaged with this version
of Ubuntu is no longer compatible with FORGE OpenStack.

Checking the current quota
------------------------------------------------------------------------

This shows the current quota tenant has.

-   nova quota-show --tenant kainuunetu
-   cinder quota-show kainuunetu
-   neutron quota-show --tenant_id kainuunetu

Updating quota
------------------------------------------------

**CPU and RAM are bound together (1 Core/2G RAM)**

Amount is what you want to update the value to. Use quota-show to check
if your update was successful.

**Nova (CPU, RAM, Ephemeral disk)**

-   nova quota-update TENANT --instances AMOUNT
-   nova quota-update TENANT --cores AMOUNT
-   nova quota-update TENANT --ram AMOUNT
-   nova quota-update TENANT --key-pairs AMOUNT
-   nova quota-update TENANT --security-groups AMOUNT
-   nova quota-update TENANT --security-group-rules AMOUNT

For example

    nova-quota-update kainuunetu --cores 32

**Neutron (Floating IPs, security groups)**
 Neutron can be updated with commands:

-   neutron quota-update --tenant_id kainuunetu --floatingip 10
-   neutron quota-update --tenant_id kainuunetu --security_group 20
-   neutron quota-update --tenant_id kainuunetu --port 100

**Cinder (Volumes)**

-   cinder quota-update --volumes AMOUNT TENANT
-   cinder quota-update --gigabytes AMOUNT TENANT

Default quota for a tenant
------------------------------------------------------------------------

Shows the default quota for a tenant.

-   nova quota-defaults
-   cinder quota-defaults TENANT

Swift (Object storage)
--------------------------------------------------------------

Swift does not have a default quota. You can set the quota using the
line below. Quotas do *not* affect admins.

-   swift --os-storage-url
    [https://cloud.forgeservicelab.fi:8081/v1/AUTH_[tenant_name]](https://cloud.forgeservicelab.fi:8081/v1/AUTH_%5Btenant_name%5D)
    post -m quota-bytes:1099511627776

Redmine project creation
===============================================================================

#### *Service Developer* project creation on redmine on demand basis

1.  Make sure the person who is requesting this is technical contact
2.  Start with copying the "Service Development Template Project"
    project on Redmine projects page page
3.  Name it same as the Service Development project
4.  Write the same in the identifier
5.  Make sure the example issues are copied to the new project
6.  Assign Technical contact as Project admin role for the project

Support process
====================================================

FORGE Support project managed by KE
--------------------------------------------------------------------------------------------

-   User submits the issue ticket
-   Somebody from KE replies to it.
-   Depending on if KE doesn't know how/can't resolve the issue, it gets
    raised to CSC/Digile by assigning the issue ticket to (USERNAME REMOVED)
    and marking (USERNAMES REMOVED) as
    watchers to the issue ticket
-   Comments made by CSC are made with PRIVATE NOTES checkbox selected
    so affiliate doesn't see them
-   After the possible fix, KE marks the ticket as resolved
-   After user confirmation of the fix, KE closes the ticket or after 7
    days of marking the ticket as closed

Support via email
--------------------------------------------------------

-   User sends an email to <support@forgeservicelab.fi>
-   Redmine checks the support inbox every 10 minutes and if there are
    new emails, it creates ticket automatically and emails the details
    of the ticket to the address where the email was sent
-   Rest of the process goes like defined above

Support via XMPP - Proposal
--------------------------------------------------------------------------

### Support via forge-support room

*Support account can be used for this, but there must be a notification
somewhere that support person might not be available all the time*

-   User joins the support room on our XMPP-server
-   User states the problem in the public room
-   If other users are present, they can help with the problem if they
    know the solution
-   Support person tries to solve the problem and creates a ticket in
    the Forge Support
-   Support person copy pastes the conversation log from public chat
    room in the ticket so it's visible and documents the solution in the
    ticket
-   Support adds the user as watcher to the ticket
-   Depending on if KE doesn't know how/can't resolve the issue, it gets
    raised to CSC/Digile by assigning the issue ticket to (USERNAME REMOVED)
    and marking (USERNAMES REMOVED)
    watchers to the issue ticket
-   Commends made by CSC are made with PRIVATE NOTES checkbox selected
    so affiliate doesn't see them
-   After the possible fix, KE marks the ticket as resolved
-   After user confirmation of the fix, KE closes the ticket or after 7
    days of marking the ticket as closed

### Support via IM

*Support account can be used for this, but there must be a notification
somewhere that support person might not be available all the time*

-   User states the problem in the IM
-   Support person tries to solve the problem and creates a ticket in
    the Forge Support
-   Support person copy pastes the conversation log from public chat
    room in the ticket so it's visible and documents the solution in the
    ticket
-   Support adds the user as watcher to the ticket
-   Depending on if KE doesn't know how/can't resolve the issue, it gets
    raised to CSC/Digile by assigning the issue ticket to (USERNAME REMOVED)
    and marking (USERNAMES REMOVED)
    watchers to the issue ticket
-   Commends made by CSC are made with PRIVATE NOTES checkbox selected
    so affiliate doesn't see them
-   After the possible fix, KE marks the ticket as resolved
-   After user confirmation of the fix, KE closes the ticket or after 7
    days of marking the ticket as closed

Project management
=============================================================

Definition of done
=============================================================

-   Architecture is documented in wiki and is reviewed
-   Design is documented in wiki and is reviewed
-   User document is in readme or wiki and is reviewed
-   Test results are available
-   User story is demonstrated in live system
-   Assets are in git
    -   Code
    -   Test cases (unit, functional, acceptance)
    -   Environment(s) provisioning playbooks or instructions
    -   Deployment playbooks
    -   Monitoring playbooks
-   Automation enabled for different phases
    -   Building
    -   Testing
    -   Deployment
    -   Monitoring
-   CI jobs for development and testing environments run green
    -   Development and testing environments provisioned
    -   CI jobs are triggered by git commits
    -   Build code
    -   Execute unit tests
    -   Deploy to development and testing environments
    -   Perform functional and acceptance tests
-   CI jobs for production environment run green
    -   Production environment provisioned
    -   CI jobs can be triggered manually
    -   Deploy to production environment
    -   Execute acceptance tests

Incident management
================================================================

An *incident* is a case where
 - hardware or other system malfunction has affected affiliates'
resources or OpenStack Service
 - the virtual machine running in FORGE OpenStack is compromised and may
potentially impact to the availability of OpenStack and other VMs.

In case of and incident is detected either manually or by automated
tool, then the following procedure applies.
 - For example in hardware break the most likely ticket creator is CSC.
 - In major **IaaS service availability** incidents CSC also makes the
(customer news
bullet)[[#Service_breaks_and_announcements]]

1.  [new
    incident](https://support.forgeservicelab.fi/projects/forge-support/issues/new)
    with following details should be filed (ANYBODY)
  - Project is Support
  - Tracker is Incident
  - Issue category is set as INCIDENT (csc group then becomes
	automatically the default assignee)
  - Everybody in CSC group receives incident email
  - Following watchers are added to the incident: (UESRNAMES)
  - Set the incident status as **NEW**
2.  Analyse the incident (CSC)
  - CSC adds instance name, IP address, project name, VM state
	information, other relevant information
  - CSC sets the incident status to **IN PROGRESS**
  - CSC verifies that the incident is valid and documents the
	results of the verification
  - If the incident is not valid, then CSC sets the status to
	**REJECTED** Otherwise re-associates the incident to DIGILE
	group
  - In case of security incident: CSC may suspend the VM and/or
	router in question if necessary and document the potential VM
	suspension in the incident. CSC notifies <security@csc.fi> if
	incident can affect CSC security and or reputation.
3.  Customer communication or internal resolving
  - If DIGILE receives the incident which is **IN PROGRESS** state
    and concerns a customer, then DIGILE should contact the
    Affiliate in question and agree upon corrective actions. Note!
    DIGILE may reassociate these issues to KE for contacting
    a customer.
  - If DIGILE receives the incident that concerns DIGILE's own
    services, then incident is handled according to normal issue
    mgmt process.
  - The technical contact of the project is set as ticket assignee
    and the person who created the VM is set as watcher
  - The corrective actions should be agreed upon, executed and
    documented
  - The assignee sets the incident status as **RESOLVED** and
    re-associate the incident to back to incident reporter for
    verification who CLOSEs the ticket.

Notice:

 - The ticket is by default private, but technically it is possible to
send a specific message inside the ticket to Affiliate (Technical
Contact person) by unchecking the "private" checkbox of the comment to
be submitted.

Issues management
==========================================================

FORGE project and all its subprojects can have following issue types:
Epic, User stories, Bugs, Tasks, Risks, Changes and Incidents. Target is
to have a similar workflow for all issue types.

Issue workflow
----------------------------------------------------

-   Anybody can create a new issue. Issue creator sets the issue type,
    category and project (DIGILE, CSC, KE, DRUID, SERVICEDESIGN) and
    assignee (DIGILE, CSC, KE, DRUID or SERVICEDESIGN group) accordingly
-   Product owner ensures issues are ordered in the release backlogs
-   Team members may assign and reassign issues to themselves
-   Scrum master (or project's QA if it exists) ensures all issues are
    assigned
-   Assignee sets the issue status as **IN PROGRESS**
-   Assignee **RESOLVES** or **REJECTS** issues that are not closed nor
    rejected, updates remaining hours estimate and then reassociates the
    **RESOLVED** issue to Project's QA for verification
-   Assignee may **REJECT** invalid issues and reassociate them back to
    where it come from
-   Project QA verifies the resolution of issues which were reassociated
    him and then **CLOSES** or **REOPENS** issues
-   Product owner sets user stories, risks and changes to **REVIEWED**
    state then when they are ready to be worked on
-   Team may return user stories back to product owner by setting the
    state to **REOPENED** and by returning it to back to release backlog
-   The lifecycle for the epics and stories is: Product backlogs (bulk
    of stories) --&gt; Release backlog (priority order, story points)
    --&gt; sprint (stories planned, tasked and estimated)

### The goal of the workflow

-   Product backlog has the bulk of stories not necessarily in the
    priority order but to be worked on in the future
-   Release backlogs are common for all projects and have stories which
    match the business targets in priority order. These stories serve as
    an input for team’s sprint planning
-   Sprint backlog is project's own backlog and it has stories and tasks
    which the team has planned in details and committed to

![FORGE issue management sequence
diagram](/files/issuemanagement.png)
 **Issue workflow illustrated**

Roles
----------------------------------

### Product Owner

Product owner creates and maintains stories in the product backlog and
in the release backlogs in priority order and ensures the quality of
stories so that each story is properly described, verifiable and that
definition of done for the story is clear. Therefore product owner is
responsible of organizing the backlog grooming in her project. When the
story is ready to be worked on from the product owner's point of view he
sets the story state as **REVIEWED**. Targets are begin set and agreed
upon in the release planning meeting where relevant stories are moved
from release backlogs to the release backlog.

### Scrum Master

Scrum Master facilitates Scrum methodology and helps team in planning
and executing sprints. Scrum Master estimates the complexity of the
stories in backlogs by providing story points with the help from the
team. The story points which are available as enumerated fibbonacci
numbers illustrate the size of the story. During sprint planning the
team selects one baseline story and compares it with other stories and
then comes up with story points for each. So, eventually story points
indicate the size of stories relative to the baseline story. If the
story is too vague and cannot be planned, the story can be returned to
the product owner by setting the state of the story to **REOPENED**.

### Team Member

Team Members and Scrum Master take stories in the priority order from
the release backlog to it’s sprint in it’s sprint planning meeting. Then
the team plans the sprint in details by creating tasks for each story
that is in the sprint. The task board module of Redmine helps team in
sprint planning. Impediments are considered as tasks by Redmine. It’s
easy to add impediments and tasks in the task board module during the
sprint planning or anytime during the sprint. The detailed sprint
planning happens in each team’s own sprint planning meeting. If the
story is too vague and cannot be planned, the story can be returned to
the product owner by setting the state of the story to **REOPENED**.

### Assignee

Assignee can be anybody and assignee **RESOLVE**s issues.

### QA

QA verifies and **CLOSE**s issues that are resolved by assignee. QA
ensures the quality.

Issues
------------------------------------

### Epic

Epic can be considered as a high level feature which contains the set of
detailed and related features (user stories). The Epic won't have
storypoints because it is used only to indicate the related users
stories. Typically one large user story might have to be split into
multiple smaller and related user stories and then the original user
story should be changed to Epic. **Don't use subtasks when linking
issues!** Usage of subtasks may change the original issue type. Instead
use "Related Issue" indicating the issue relations.

### Story

User story can be considered as a detailed feature which describes
single desired functionality. Product owner creates new stories in the
Product backlog and ensures that they belong to correct Epic. When the
story is ready to be worked on from the product owner's point of view,
product owner sets the state to **REVIEWED**. The team may return
stories back to the product owner by setting them to **REOPENED**.
Product owner also maintains stories in the priority order in all
backlogs except sprint backlog. Scrum master may want to have “generic”
stories for bugfixing or for risks. It’s recommended that the estimated
length of each story is no longer than the length of the sprint. It
should always be possible to complete stories during the sprint. If it
looks like a story spans across multiple sprints, then the story should
be splitted into smaller stories. Stories should be written in the
following way: “As a ROLE, I want GOAL/DESIRE so that BENEFIT”.

Example story: As a user closing the application, I want to be prompted
to save anything that has changed since the last save so that I can
preserve useful work and discard erroneous work.

### Incident

Incidents are severe intrusions to the VMs and incidents are managed
according to [Incident_management](#incident-management)

### Bug

Bugs may depend on each others and can relate to each others. Individual
bugs can be managed in the sprint planning and bugs are visible in the
product backlog similarly to stories.

Before issue is submitted, it it the responsibility of the submitter to
check for existing issues for potential duplicates so that same thing
doesn't get reported many times.

If it is clear to which project the bug belongs to

-   new CSC issue
    can be filed against CSC project and a

-   new KE issue
    can be filed against KE project and a

-   new DIGILE issue
    can be filed against DIGILE project.

-   new DRUID issue
    can be filed against DRUID project.

-   new SERVICEDESIGN issue
    can be filed against SERVICEDESIGN project.

If it is not clear which project the newcoming issue belongs to then a

-   new DIGILE issue
    should be filed against DIGILE project

The issue author should also select the correct category and assignee
group for the issues if he knows them

Bugs are visible in the backlogs and can be managed similarly to other
issues in Redmine and they can be planned in Sprints.

![Bug life cycle](/files/bug_lifecycle_flow.png)

**1. New bug**

-   Anyone can file a bug. It appears as “New” issue on redmine.
-   Bug should be assigned to team who is responsible for fixing it. If
    not know to which team assign it should be assigned to QA/Digile
    group
-   Bugs priority is set by submitter and it should be considered as a
    input for team work queue

**2. In progress**

-   Assignee takes bug for fixing. Bug is handled as a task in scrum

**3. Resolved**

-   Assignee Resolves the bug and assign bug to QA

**4. Closed**

-   End state of bug
-   After bug verification QA changes the bug to “Closed” state.

**5. Rejected**

-   End State of bug (unless reopened by submitter See 6.)
-   QA changes the status to “Rejected”

**6. Reopened**

-   If bug can be reproduced QA will put it to “Reopened” state
-   Rejected bug can be reopened if bug submitter disagree with
    rejection reason. Bug submitter must update bug with updated
    information why it should not be rejected.

### Risk

Risks are items, that potentially cause harm to the project schedule,
budget or quality. Risks require tasks to mitigate the risk or to plan
for a contingency. Therefore each risk should contain stories or tasks.
Risks can be managed in the Sprint planning and risks are visible in the
Product backlog.

Risks are managed similarly to other issues.

### Impediment

The team can create impediments in the task board as part of ordinary
sprint planning and sprint execution. Redmine considers impediments
similar items to tasks.

### Change

Changes are requests to change existing functionality in FORGE. Change
author ensures that the change gets communicated, decided, implemented
and closed.

Changes can be managed similarly to other issue types. The change
itself, reasons for a change and impacts should be described in the
change proposal. Also, the creator of the proposal should add relevant
stakeholders (those who the change might have an impact on) as
“watchers” for the change so that they get notified automatically. The
change author follows up that the change gets managed (communication,
decision, implementation, verification) properly.

### Task

Tasks are elements of work, the team needs to perform in order to
complete the story or other issue type. It’s recommended to use binary
metrics for task monitoring. In practice it means that the length of the
task was no longer than the time between task tracking meetings.
Therefore the task would be either open (new, in progress, reviewed,
resolved) or closed (closed, rejected) but nothing between. For tasks,
the remaining hours estimate is reported when the task been worked on.

Issue parameters
--------------------------------------------------------

### Reporting area

Reporting area is used as a container for the collection of related user
stories according to ministry reporting style. In FORGE project this
field is mandatory and should be selected for each issue type other than
task.

|	Reporting area	|	Description	|
|	------------------	|	------------------	|
|	System development	|	System development contains all work that needs to be done to implement FORGE Service Lab infrastructure.	|
|	Support for operations	|	All work needed to support both the FORGE Service Lab building and the "users"/"service developers" of FORGE when it is ready for the volume operations.	|
|	Technical support for service development	|	All technical planning and design work needed to support FORGE serviced developers in the creation of technical service infrastructure.	|
|	Service design support	|	All work needed to support the service design activities of FORGE affiliates.	|
|	Stakeholder & Community dialogue	|	All work and activities needed in the dialog with FORGE Service Lab stakeholders and communities.	|
|	Documentation	|	All work needed to created FORGE Service Lab documentation for FORGE Affiliates.	|
|	Training	|		|
|	JulkICT Lab implementation	|	Sandbox/prototyping environment for Ministry of Finance.	|
|	Support for Open Data IaaS service	|	All work needed to support the Open Data efforts of Ministry of Transport and Communications.	|
|	Contracts & Legal support	|	All work that is needed to create contracts and provide legal support for the building of FORGE Service Lab.	|
|	Project management	|	All project management activities related to the building of FORGE Service Lab.	|
|	Planning of phases 1,2,3, 4	|		|
|	Pilot projects	|		|
|	Product Backlog	|		|

### Categories and types

Product owner and scrum master may benefit from setting up issue
categories. Categories can be defined per project basis and they can be
used to automatically assign certain category issues to a specific
person. E.g. all incidents that are filed in CSC project are
automatically assigned to CSC group so that everybody in that group gets
notified.

Project management tool
============================================================================

Redmine
--------------------------------------------

[Redmine](http://www.redmine.org) with
[Redminebacklogs](http://www.redminebacklogs.net/) plugin is used as a
tool to manage FORGE projects. Also there are several plugins, a FORGE
theme and some patches installed into FORGE Redmine.

### Plugins

	redmine_anonymous_watchers
	redmine_backlogs
	redmine_canned_responses
	redmine_email_notification_content_filter
	redmine_extended_watchers
	redmine_impasse
	redmine_ldap_sync
	redmine_my_page_queries
	redmine_redcarpet_formatter
	redmine_rubycas
	redmine_watcher_groups
	redmine_wiki_extensions

### Theme

-   <https://git.forgeservicelab.fi/forge/redmine-forge-theme>

Projects
----------------------------------------------

-   FORGE Support contains Service Developers only
    -   Wiki documentation and helpdesk for Service developers
-   FORGE Announce contains Service developers and partners with CRA
    -   News for Service developers and partners
-   FORGE Forums members contains all affiliates (Service developer,
    Partner and Partner with CRA)
    -   Forums for discussion and collaboration

Roles
----------------------------------------

-   **Project admin** role provides edit access to project settings and
    capability to add sub projects. This role is suitable for scrum
    masters and product owners who have to edit releases and sprints in
    addition to managing product backlogs
-   **Team member** role provides edit access to issues and
    product backlogs. This role can be used to provide access for
    project members, product owners and scrum masters who manage product
    backlogs
-   **Stakeholder** role provides edit access to issues. This role can
    be used to provide project external (temporary) stakeholders edit
    access to the projects issues. Stakeholder can also create
    new issues. This role can not edit backlogs so it's not suitable for
    scrum masters nor product owners.
-   **QA** role is similar to Team member role and provides edit access
    to issues and product backlogs.
-   **Watcher** role provides read and comment access to the project's
    selected issues. This role can be used to provide an external party
    a read only access to the project's selected issues with right to
    comment on them. If you want to provide a issue update notification
    for the user who is in watcher role, then set the user as a watcher
    for the issue. The user will be able to list all the issues he is
    watching when he selects "issues" tab, but he won't see other issues
    which he is not watching.

Setting up Redmine's 'My Page' to show review requests
---------------------------------------------------------------------------------------------------------------------------------------------

Redmine has a plugin that allows custom search queries to show up on the
'My Page' portal. To get them there it is necessary to first make an
issue search query and save it. Here are the steps to show the issues
for which you are the reviewer.

1.  Select the project from which you need to find the issues, e.g.
    FORGE
2.  Select the 'Issues' tab
3.  Untick the pre-selected status filter
4.  From the 'Add filter' dropdown select 'Reviewer'
5.  The default options for this filter should already be `'is'` and
    `'<< me >>'`
6.  Click apply to verify that the results show as expected
7.  Click save and give the query an appropriate name, optionally,
    select any extra configurations that you find necessary
8.  Head over to the 'My Page' portal and click on the 'Personalize this
    page' link at the top right corner
9.  The 'My page block' dropdown menu should now show your saved query,
    select it and click 'Add'

Now you will be able to see a new block with the results of the reviewer
query. Any saved queries will show up on the dropdown menu so this can
be used to add any arbitrary queries as a block on the 'My Page' portal.

Project planning
=======================================================

Projects
---------------------------------------

FORGE uses [Scrum
framework](http://www.amazon.com/Essential-Scrum-Practical-Addison-Wesley-Signature-ebook/dp/B008NAKA5O/ref=sr_1_1?s=digital-text&ie=UTF8&qid=1421222010&sr=1-1&keywords=essential+scrum&pebp=1421222011543&peasin=B008NAKA5O)
(see [Scrum-Guide-US.pdf](/files/Scrum-Guide-US.pdf))
in managing projects and uses [Redmine](http://www.redmine.org) with
[Redminebacklogs](http://www.redminebacklogs.net/) plugin as project
management tools. Scrum masters, product owners and team members will
find [Redminebacklogs](http://www.redminebacklogs.net/) plugin
documentation useful in terms of how projects are being managed in
FORGE. Depending on you accessrights you are able to access some of the
following projects

-   FORGE is the
    FORGE platform development internal project managed by Digile. The
    project is a container for all FORGE work. This project defines
    releases
    -   DIGILE is
        FORGE platform development internal project managed by Digile.
        The project manages and operates FORGE platform and carries out
        the FORGE platform development activities
    -   CSC is FORGE
        platform development internal project managed by CSC. The
        project implements and operates FORGE IaaS
    -   DRUID is
        FORGE platform development internal project which Druid manages
        and implements FORGE WEB, Plaza and Dashboard related activities
    -   KE is FORGE
        platform development internal project managed by Kainuunetu. The
        project implements and operates FORGE helpdesk (FAP) development
        activities
    -   SERVICEDESIGN
        is FORGE platform development internal project managed by JAMK.
        The project implements and operates Service Design related
        activities
    -   DEPLOYMENT
        is FORGE platform development internal project managed by Weego.
        The project examines the deployment to commercial production
        IaaS clouds. This project is completed and not active anymore.
-   FORGE Support
    is an external project accessible by FORGE Service Developers. The
    project is used to support Service Developers in terms of
    documentation and support tickets
-   FORGE Service Lab is an
    external project accessbile by all FORGE Affiliates. The project is
    used by Affiliates to collaborate using forums

Planning and execution
-------------------------------------------------------------------

All items are called issues in Redmine. Backlogs consists of product
backlog items (PBI) which are then planned down into zero or more tasks.

FORGE project and sub-project backlogs can have following PBI types:
Epic, User story, Bug, Risk, Change, Incident
 FORGE Support project can have following issue type: Support

-   Release planning is a high level planning event every two months to
    set common business targets
-   Sprint planning is detailed planning event every two weeks where
    selected release plan items are planned down into tasks
    -   Projects move user stories from the release backlog to their
        sprint backlogs for detailed planning
    -   Projects estimate the size of the user stories and create
        detailed sprint plan by creating tasks
-   Sprint execution produces substance for the user stories
    -   Projects RESOLVE issues and update remaining hours for issues
        which are being worked on
    -   RESOLVED issues are CLOSED by a verifier

Reports
-------------------------------------

Project status is visible in Redmine both on sprint basis and on release
basis. The content and status of that release becomes visible when one
selects desired release from the sidebar menu.

Project statistic reports are available in experimental BIRT service.

Scrum framework
-----------------------------------------------------

FORGE cross project planning and tool usage is explained in the
[forge_planning_03.pdf](/files/forge_planning_03.pdf)
attachment

FORGE project aims at following Scrum framework and uses sprints for
detailed planning. Release backlogs provide a content for sprints and
each sub-project plans, executes and closes its sprints individually.
Projects' sprints have two week cadence. Releases are planned in
co-operation with all sub-projects and releases have about 2 month
cadence.

FORGE project contains common elements for all projects. Release targets
and user stories are shared among all projects and serve as an input for
sub-projects’ sprint planning. FORGE release backlog
contains prioritized list of user stories for all projects for next
release period.

Release
-------------------------------------

A release is a program-wide high level plan under FORGE project which
is shared among all sub-projects and is to be implemented across
sub-projects within about two months time. One release is planned at the
time. Release content is may change during the release progresses since
new information accumulates by the time being. Each project and it's
product owner may modify projects's own content in the release backlogs
and ensures that the backlog meets the target setting.

See the [Releases](6_Releases.md).

Sub-projects use FORGE’s release backlog when planning their sprints.
FORGE's shared release backlogs are visible in sub-projects' own
backlogs tab. PBIs are taken from FORGE release backlog to
projects' own sprints for planning, execution, followup and closing.
Each project creates and plans its own sprints by creating tasks for
PBIs. Projects may plan one sprint at the time by taking just right
amount of storypoints into its sprint.

### Release planning

FORGE project takes care of the release planning.

-   Targets are set for the release and described in the wiki
-   There is a common agreement about the targets
-   Release backlog is created
-   Target matching user stories are taken into the release backlog
-   Release content is prioritized

![Project
planning](/files/forge_projectmgmt_sequence_diagram.png)
 **Planning illustrated**

Sprint
-----------------------------------

A sprint contains a detailed plan with issues in it for a sub-project to
be implemented within two weeks. Each sub-project plans, executes,
follows and closes their own sprints. Each project plans its own sprints
by taking PBIs from the FORGE project's release backlog, that is common
to all projects, to their sprints.

### Sprint planning

Each project takes care of its own sprint planning.

-   Ensure that previous sprint is closed and there are no leftover PBIs
    nor other issues in the sprint backlog
-   Ensure PBIs have storypoints set
-   Create a new sprint backlog
-   Review release targets so that whole team is aware of them
-   Plan story
    -   Take the topmost PBI from the release backlog to the sprint.
        Assumption is that the release backlog is prioritized. The
        **REVIEWED** state for stories indicates that the story is ready
        to be worked on from the product owner's point of view
    -   Discuss and split the story if needed
    -   Create tasks and associate them according to team members
        volunteer to take them
    -   The PBI can be returned back to product owner by setting it to
        **REOPENED** state e.g. in case the story is too vague and
        cannot be planned
    -   Iterate planning as long as there are right amount of PBIs in
        the sprint
-   Review the developed sprint backlog with product owner and start the
    work

### Projects' sprint execution

-   Team will arrange it's own QA
-   Team members can click "My page" in Redmine to list his own issues
-   Team members should update remaining hours for the issue whenever he
    works on it
-   Team members should identify and resolve impediments if any and
    bring them up in daily scrum meetings
-   Scrum master will help the team and facilitate Scrum
-   Team members mark issue as RESOLVED when it's done according to the
    definition of done and then reassociates it for verification
-   Verifier verifies the issue and then CLOSES it and reassociates it
    back to the resolver
-   PBIs can be CLOSED by the decision from PO (Product Owner)
-   FORGE QA may reopen already CLOSED PBIs or issues if e.g.
    verification fails

Sub-projects start to get velocity data (Burndown) then when the
"remaining hours" of issues gets updated. Scrum recommends using daily
scrum meetings and it’s a team members' issues to ensure that "remaining
hours" and issues' status get updated and impediments gets resolved.
Burndown is available in the Backlogs tab's drop down menu.

### After the sprint is completed

After the sprint is completed and PBIs and issues are resolved, verified
and closed, Scrum Master may close the sprint from the Settings/Versions
menu. In case of PBIs that were not completed, the team typically moves
them back to release backlog and then replans them better when they are
addressed next in the later sprint plannings.

![FORGE issue management sequence
diagram](/files/issuemanagement.png)
 **Sprint planning illustrated**

Technical project collaboration
====================================================================================================

Cross project technical decisions are made and discussions held at
weekly Technical Project Meeting. The meeting occurs on Monday's at
13.00 o'clock and will be invited by (USERNAME REMOVED). 

Access to resources
================================================================

Different Affiliate roles have different access to FORGE resources. The
resource availability matrix is as follows.

### FORGE IaaS and SaaS roles

| Service                          | developers<br>(LDAP) | partners<br>(LDAP) | partners_cra<br>(LDAP) | Anyone | Purpose | 
| --------                         | -----------| -------  | -------------| ------ | ------- | 
| OpenStack - Project's own tenant | x          |          | x            |        |  Service development |
| Git - Internal projects          | x          |          |              | x (Public projects) | Service development |
| XMPP - forge-devel               | x          | x        | x            |        | Collaboration between all |
| Drupal - Plaza                   | x          | x        | x            | x (Public information)|  Service development partners |
| Redmine - FORGE Support          | x          |          |              |        | Support, wiki documents, projectmgmt for service developers |
| Redmine - FORGE Service Lab      | x          | x        | x            |        |  Collaboration (forums) and announcements (news) for all |

### Drupal - Landing pages for each role

| Role                 | Page |
| -----------------    | ---- |
| Anonymous            | Public www (https://forgeservicelab.fi) | 
| developers (LDAP)    | Dashboard (https://forgeservicelab.fi/en/welcome-forge) | 
| partners (LDAP)      | Public www (https://forgeservicelab.fi/en/plaza) | 
| partners_cra (LDAP)  | Plaza (https://forgeservicelab.fi/en/plaza) | 
| JulkICT (DRUPAL)     | Dashboard (https://forgeservicelab.fi/en/welcome-forge) |


Communication policy and instructions is described in
[Communicating_announcements](#service-breaks-and-announcements)

### Drupal - Finegrained access

| Service  | developers<br>(LDAP) | technical_contacts<br>(LDAP) | partners<br>(LDAP) | partners_cra<br>(LDAP) | JulkICT<br>(DRUPAL) | Anyone | Purpose | 
| -------- | ----------------- | ----------------- | ------- | ---------------- | ------- | ------ | ------- | 
| Drupal - Add JulkICT  offers       |   |   |   | |x|                    | Service development |
| Drupal - View JulkICT  offers      |   |   |   | | |x                   | Service development |
| <del>Drupal - Add Bulletin Board</del>        |x  |x  |x  |x|x|                    | Service development |
| <del>Drupal - View Bulletin Board</del>       |   |   |   | | |x                   | Service development |
| Drupal - View Dashboard            | x |   |   | | |                    | Service development |
| Drupal - Add Service offers        |   | x |   | | |                    | Service development |
| Drupal - Add product offers        |   | x |   | | |                    | Service development |
| <del>Drupal - Vote on offers</del>            |   |   |   | | |x                   | Service development |


Changing data of a user
========================================================================

Changing email
------------------------------------------------------

Email is a critical attribute as we use it to provide users with link to
password change. It has to be changed in LDAP and then probably also in
Redmine and Gitlab. It will get propagated to Redmine in 10 minutes, but
it will not get propagated to Gitlab.

New affiliate
==============================================

Affiliates must have a signed contract in place in order to get access
and in order to use FORGE Service Lab services. After the contract and
payment are checked, the checker can initiate the creation of the new
project by submitting a "New creation request" ticket. After the ticket
has been handled, the affiliate will receive necessary instruction via
email so that he can start using the services.

### New creation request

The DIGILE staff submits the new creation request and the submitter is
responsible of checking the contract and the payment before creating a
ticket. There are templates available for new project creation, for new
tenant creation and for new account creation. The templates are
available under **Insert canned response** menu after you click "Create
a new support ticket".

The new support ticket should contain following details

-   Title for the ticket: e.g. New creation request - Project
-   Details for the request: Select and fill the suitable template.
    Templates are available under **Insert canned response** menu
-   Note! Email address must be unique, so one email can be used by one
    account only

Resource Allocation Process
========================================================================================

Affiliates must have a signed contract in place in order to get access
and in order to use FORGE Service Lab services. After the contract and
payment are checked, the checker can initiate the account creation. In
practice DIGILE always initiates an account creation which KE then
implements. After KE has implemented the account creation, the Affiliate
will receive necessary instruction via email so that he can start using
the services.

Affiliate creation
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Initiation by DIGILE

Affiliate creation is initiated by DIGILE after the contract and payment
are checked. Initiation happens by creating a support ticket for KE. The
ticket creator is responsible of checking the contract and the payment
before creating a ticket. There are templates available for new project
creation, for new tenant creation and for new account creation. The
templates are available under "Insert canned response" menu after you
click "Create a new support ticket".

The new support ticket should contain following details

-   **Title for the ticket**: e.g. New creation request - Project
-   **Details for the request**: Select and fill the suitable template.
    Templates are available under *Insert canned response* menu
-   **Note! Email address must be unique**, so one email can be used by
    one account only
-   The admin machine is **temporarily** forgeadmin.csc.fi
-   Account creation is done on Insightly
    (<https://forgeservicelab.insight.ly/home>)

### The procedure by KE

#### 0. Verification

KE receives the new account creation ticket and verifies if as follows.

-   The ticket creator is in digile group

    -   if the ticket creator is not in digile group, then KE closes the
        ticket as invalid with the message "Please contact Digile staff
        to create new accounts."

KE gets the approval for the account account creation ticket

-   The ticket is approved (or sent) by FORGE concept owner (USERNAME REMOVED)

    -   if the ticket doesn't get approved, then KE closes the ticket as
        invalid with the message "Please contact (USERNAME REMOVED) to create
        new accounts."

#### 1. Creating the affiliate account

**Assign ticket to yourself!**

-   Make sure there isn't already an account for this person by
    searching Insightly
-   Click the + button and select "Add new contact" or click this link
    <https://forgeservicelab.insight.ly/contacts/create>
-   Add all information and save the contact

#### 2. Creating the organization

-   Make sure there isn't already an organization for this company by
    searching Insightly
-   Click the + button and select "Add new organization" or click this
    link <https://forgeservicelab.insight.ly/organisations/create>
-   Add all information and save the organization
-   Add the person to organization in the links section

#### 3. Creating the project

-   Make sure there isn't already aproject by this name by searching
    Insightly
-   Click the + button and select "Add new project" or click this link
    <https://forgeservicelab.insight.ly/projects/create>
-   Fill in the details
-   Responsible persons are: (USERNAME REMOVED) for FPA/FPA (CRA) and
    (USERNAME REMOVED) for SDA projects
-   Set project pipeline as: project execution and stage to: project
    execution
-   Select the right quota for the project
-   Save the project

-   Add technical and admin contacts: Make sure to follow naming scheme:
    "Technical Contact"/"Admin Contact"

-   Link the project to the organization

Tenant in Openstack is created automatically if project is SDA/FPA (CRA)

#### 3.1. Creating the tenant

In a case where there is a need for new tenant only under existing
project.

-   Click the + button and select "Add new project" or click this link
    <https://forgeservicelab.insight.ly/projects/create>
-   Fill in the details
-   Category: Openstack tenant
-   Responsible persons are: (USERNAME REMOVED) for FPA/FPA (CRA) and
    (USERNAME REMOVED) for SDA projects
-   Project pipeline and stage: Nothing selected
-   Select the right quota for the project
-   Save the project

Link the tenant to the right project (from tenant page) and add
necessary people to the tenant

#### 4. Checking identity entity propagation

-   LDAP -&gt; Redmine synchronization must happen. It happens
    automatically each 10 minutes.
-   LDAP -&gt; Keystone synchronization must happen. It happens
    automatically each 10 minutes.

-   KE makes sure that the new user is available in Redmine.

    -   if the user is not available in Redmine after 10 minutes, check
        /tmp/redmine_ldap_sync.log and grep for the new login name
-   KE makes sure that the new tenant and user are available
    in Keystone.

#### 5. Closing the account creation ticket

-   KE closes the support ticket with **Affiliate account created**
    template from *Insert canned response* menu

#### 6. Technical contact training request

-   Create the new issue in Redmine
-   Assign the request to Digile group
-   Set the issue category as "Training request"

User account creation
----------------------------------------------------------------------------

### Initiation by DIGILE or by an affiliate technical contact

User account creation is initiated by DIGILE or by a technical contact
from an existing affiliate party by creating a new support issue in Redmine.
The new support issue should contain following details

-   Person details: name, surname, mobile, mail
-   Organization details: name of the organization
-   Project name: name of the project on OpenStack

### The procedure by KE

The identity entities are created by Kainuun Etu.

#### 1. Verifying affiliate technical contact

-   If the creation request comes from someone out of Digile and CSC, KE
    verifies the user is a technical contact of given organization. This
    can be viewed in Insightly by searching with the project name and
    checking from the links if the user is technical contact of
    the project.

-   if the requester is not the technical contact, KE closes the ticket
    as invalid with the message "Please ask your technical contact to
    submit additional account creation request for this project."

#### 2. Creating the affiliate account

-   Make sure there isn't already an account for this person by
    searching Insightly
-   Click the + button and select "Add new contact" or click this link
    <https://forgeservicelab.insight.ly/contacts/create>
-   Add all information and save the contact
-   Add user to correct projects

#### 3. Checking identity entity propagation

-   LDAP -&gt; Redmine synchronization must happen. It happens
    automatically each 10 minutes.
-   LDAP -&gt; Keystone synchronization must happen. It happens
    automatically each 10 minutes.

-   KE makes sure that the new user is available in Redmine.

    -   if the user is not available in Redmine after 10 minutes, check
        /tmp/redmine_ldap_sync.log and grep for the new login name
-   KE makes sure that the new user is available in Keystone.

#### 4. Closing the account creation ticket

-   KE closes the "support" ticket with **Affiliate account created**
    template from *Insert canned response* menu

Disable an account / Remove from project
----------------------------------------------------------------------------------------------------------------

### 1. Submit a ticket to Support project

With the following info at least:

    Name:
    Project(s):

### 2. Disabling the account on FORGE

-   Go to <https://forgeservicelab.insight.ly/contacts> and search by
    name
-   Remove the link to the project on contact page

### 3. In case it is internal account

-   Assign the ticket to DIGILE
-   DIGILE checks all other places for access (admin, git, support,
    auth, db servers/xmpp admin/etc)

### 4. Verify account deletion

-   Verify that the account has been either deleted or locked from FORGE
    services and it can't be used

### 5. Remove firewall rules / security groups created for deleted person

-   Verify that all firewall rules created for deleted person
    are removed.

Change of technical contact
----------------------------------------------------------------------------------------

**If tenant is a multi-admin tenant, make sure that all admins agree
with tech contact change!**

### 1. Create account as normal

### 2. Open the project on Insightly and add the new account there with "Technical Contact" description and remove old tech contact description

### 3. Create admin notification ticket

-   KE creates new Admin notification issue in Redmine
    in the FORGE Support project
-   Use the **Admin notification** from *Insert canned response* menu
-   Add Admin's email address as watcher
-   Close the notification ticket so that an admin receives confirmation
    via email

### 4. Technical contact training request for new technical contact

-   Create the new issue in Redmine
-   Assign the request to Digile group
-   Set the issue category as "Training request"

Project End of Life
------------------------------------------------------------------------

The request for ending a project must come from DIGILE.

### 1. Remove resources

-   Go to Insightly and search for the project
-   Set project stage as "Resources removal"

### 2. Remove assets from OpenStack

-   VMs
-   Volumes
-   Networks (remove in specific order)
    -   Router
    -   Subnet(s)
    -   Network

Quota increase for an Affiliate
======================================================================================

1.  An Affilate requests for more computing resources

    An Affiliate might request for more computing resources in addition
    to what is granted as a
    [default](2_Infrastructure#openstack-quota-and-flavor).
    In this case DIGILE can instruct the Affiliate Administrative
    contact person or Technical contact person to file a new issue in Redmine
    with the details described below.

2.  KE Assigns a newly created support ticket to DIGILE to be decided

3.  DIGILE reviews the ticket and decides upon computing resource
    increase (REJECT or RESOLVED)

    If the decision is NOT OK, then DIGILE documents the reason to the
    ticket and sets the ticket status as REJECTED
     If the decision is OK, then DIGILE re-assigns it to KE and sets the
    status as RESOLVED

4.  If the ticket was RESOLVED and re-assigned to KE then KE implements
    the change and finally sets the issue status as CLOSED

5.  In all cases the issue status becomes either REJECT or CLOSED

-   **Title for the ticket: Additional computing resource request**

		Name of the organization:
		Business ID:
		Postal address:
		Project name: The project name (OpenStack project name)

		Total number of instances:
		Total number of cores:
		Total amount of RAM in GB:
		Total amount of volume storage in GB:
		Total amount of external IPv4 addresses:
		Justification for the quota increase:

Technical support for sales
==========================================================================

Sales frequently needs support from the technical team.

FORGE team is prepared to act upon these requests within the capacity
that is available and based on the priorities. The requests are being
handled in FORGE team's sprint planning every odd week Tuesdays. High
priority requests may be handled out of the sprint planning as long as
they have an approval from or are filed by (USERNAME REMOVED). Approval is
needed since all unplanned ad-hoc requests will impact on the ongoing
planned sprint results.

Prepare to provide following input. They will be asked in the support
request.

-   Describe the sales opportunity case in CRM tool and have a link to
    that entry
-   Add a customer contact detail into CRM tool who to agree a meeting
    with and have a link to that entry
-   Additional info e.g. describe the need of the kind of a support and
    desired timing

Request support from the FORGE project team by creating a new issue in Redmine
and mark the category as sales technical support.

Cost estimation
====================================================

The following outlines the process of retrieving cost estimates from
<https://planforcloud.rightscale.com> and correlating them against FORGE
tenants.

For each tenant
----------------------------------------------------

-   Select Create New Deployment
-   Select Servers -&gt; Add Server
    -   Adjust VCPU and Memory sliders to same values as the
        CRA (default/bigdata/custom)
    -   If 1:1 correspondencies that meet VCPU/RAM/HDD requirements are
        found
        -   Mark down their quantity
        -   Sort according to price
        -   Mark down cheapest flavor name and price
        -   Mark down most expensive flavor name and price
        -   You are done
    -   If 1:1 correspondencies that meet VCPU/RAM requirements are
        found
        -   Mark down their quantity
        -   Sort according to price
        -   Select cheapest option and mark price (USD/h) down
            -   Typically this option doesn't have HDD
            -   If configurable, select resource as On-Demand (as
                opposed to 1/3yr contract)
            -   If configurable, select usage as 24hours/day
            -   If storage requirements are not met, Add Storage in next
                step
        -   Select most expensive option with least overhead for
            VCPU/RAM/HDD, mark price (USD/h) down
            -   If configurable, select resource as On-Demand (as
                opposed to 1/3yr contract)
            -   If configurable, select usage as 24hours/day
            -   If storage requirements are not met, Add Storage in next
                step
    -   If 1:1 correspondencies are not found
        -   Select range via VCPU/RAM sliders (which means 0 pcs of
            1:1 correspondencies)
        -   If no corresponding flavors are still not found, either mark
            CRA as unable to correlate or deduce price from
            individual flavors.
-   Select Storage -&gt; Add Storage
    -   For a Server Type which did not include adequate storage, select
        storage from same vendor e.g. for Google instances select Google
        "Provisioned Space", for Amazon instances select "AWS EBS" and
        so on
    -   Set desired quantity and size (typically 1*1024 for CRA)
    -   If configurable, disable Provisioned IOPS and any other I/O
        modes that strive to guarantee quality
    -   Add price to Server which was missing HDD, converting monthly
        price to hourly price.

As a result you should have two prices which are in either of these
formats:

-   0,X USD/h - Vendor A server type B
-   0,X + Y/(24*30) USD/h - Vendor C server type D

Where Y is the monthly cost for the storage. Mark the flavors, storage
types and overall costs down (as min/max).

For individual flavors
------------------------------------------------------------------

If 1:1 correspondence for CRA is not found, cost can be estimated from
individual flavors. For example, Big Data CRA can be estimated by
retrieving min/max prices for the flavors that are typically in use in
Big Data CRA:

-   1x m1.tiny
-   2x hadoop.small
-   10x hadoop.medium

New team member
====================================================

DIGILE
----------------------------------

-   Create digile account
    -   Add to digile tenants
    -   Add common (USERNAME REMOVED) key
        to OpenStack account
-   If personal sandbox tenant is created:
    -   Add (USERNAME REMOVED) account to the tenant's members
    -   Add SSH access for admin machine to default and
        Digile_to_TriPort security groups
-   Add to mailinglists: forge-devel, digile-all

-   Add to XMPP chatrooms: digile

-   Add to gitlab groups: Ansible, FORGE

-   Add as gitlab admin if needed

-   Organize FORGE technology training
    for the new member

-   Add to appropriate google drives (e.g. FORGE meeting minutes)

-   Communications to existing team members

-   Edit and run forge_users playbook against FORGE VMs if
    needed (DEPRECATED)

    -   forgeadmin.csc.fi
    -   auth.forgeservicelab.fi
    -   support.forgeservicelab.fi
    -   git.forgeservicelab.fi

New member
------------------------------------------

-   Login to support and git so that user accounts gets created
-   Create ssh key and commit public part to git repository of FORGE
    ssh keys
-   Use Trainings and tutorials documentation
    in wiki to start get going

Internal account removal
===============================================================================

These actions are intended to be executed when e.g. a person no longer
works Digile for or otherwise needs to be denied access.

Vetonaula IT related cleanup
---------------------------------------------------------------------------------------

-   Windows laptop account
-   Windows account on any network drives
-   VPN/firewall accounts

FORGE related cleanup
-------------------------------------------------------------------------

-   LDAP account
-   Edit and run forge_users playbook against FORGE VMs if needed
-   authorized_keys from VMs
-   Account from barebone
-   Keypair from openstack
-   Group memberships in gitlab

Other
-----------------------------------------

-   Basic Google account (access to gmail, drive, calendar etc.)
-   Additional/other Google related accounts (Insightly)
