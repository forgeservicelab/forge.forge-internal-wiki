Releases
========================================


Release 2013-11
====================================================

-   Duration 2013-10-01 - 2013-11-29
-   Content and burnup charts are available in Redmine

Targets
------------------------------------

### High level targets

-   Reference service design blueprint from the partner
-   Manual version of the FORGE Service Lab functionality up and running
-   Cloud is able to run example service

### Detailed targets

-   Contracting. We are able to sign contracts with affiliates
-   CRA. We are able to allocate computing resources
-   Technical support services available. Tickets can be opened for FAP
    and resolved by FAP
-   Temporary portal with help texts and help desk contacts
    and instructions. There is a web page with the information and links
    that FORGE affiliates need in order to use CRA
-   Readyness for an affiliate to create a service. An affiliate who
    creates a contract is able to get credentials for FORGE and is able
    start using CRA and create services

Planning targetsetting
------------------------------------------------------------------

-   Targets were set in the meeting with (USERNAMES REMOVED) 2013-09-11
-   Targets and project mgmt process v0.2 were reviewed and agreed with
    (USERNAME REMOVED) 2013-09-12 and with (USERNAME REMOVED) 2013-09-13
-   It was agreed that each projects will define storypoints in its
    sprint planning for its stories
-   Appropriate stories which match the target setting were moved to
    Release 2013-11 sprint which is visible to all projects
-   Release can start 2013-09-13 after targets are agreed and projects
    can start planning the stories in their sprints
-   Modifications to the guidelines is now updated in
    [Project\_planning](3_OperationalGuides.md#project-planning)

Additionally following planning principles are recommended
------------------------------------------------------------------------------------------------------------------------------------------

-   It’s recommend to have a story size such that it can be implemented
    during one sprint
-   If a story are too large, then it can be split to smaller stories
-   If a story belongs to more than one project, then it can be split so
    that each project can have it’s own story
-   It’s recommended to have tasks size such that they can be completed
    during the task followup period. This means that tasks would always
    be either 0 or 100 complete but nothing between
-   There is a risk that Redmine project and workflow configurations
    might have some issues which we will face later. We’ll then resolve
    them on the go


Release 2014-01
====================================================

-   Duration 2013-12-02 - 2014-01-31
-   Content and burnup charts are available in Redmine
    Note! The
    burnup graph is available only late of the project after we moved
    from Epic focused releases to backlog focused releases.

Targets
------------------------------------

### High level targets

-   OpenStack version upgrade to Havana
-   Monitoring solutions for the cloud, for service developers and FAP
    support statistics
-   Service Design Support for Release 2013-11 FORGE
    -   Reference *process* description for organzations
-   Configuration management capability trough the templates (Examples:
    Puppet or Chef or something else)
-   Support for FORGE pilot projects (D2I VisualLabel, JulkICT Lab)
-   Preparing for FORGE production
-   Study and select the FORGE Plaza technical solution

### Detailed targets

-   Advanced cloud platform reporting (Examples: Ceylometer, Nagios)
-   Monitoring and notification capability for service developers
    (Examples: Nagios, NewRelic)
-   Ticket troughput statistics (Example: Redmine plugin)
-   Documented reference service design flow of FORGE Service Lab
-   Landing service (processes and tools) for FORGE Affiliates
-   Service design support for FORGE Affiliatesc
-   Infrastructure configuration management tool selected and deployed
-   VisualLabel and JulkICT will be running on FORGE and using FORGE
    Plaza to unveil the service
-   Test and simulate FORGE end to end

### Planning targetsetting

-   Targets were set in the planning meeting 2013-11-04 (USERNAMES REMOVED)
-   Targets were reviewed and agreed
-   Appropriate stories which match the target setting were moved to
    release
-   Release can start right after release 2013-11

### Additionally following planning principles are recommended

-   It’s recommend to have a story size such that it can be implemented
    during one sprint
-   If a story are too large, then it can be split to smaller stories
-   If a story belongs to more than one project, then it can be split so
    that each project can have it’s own story
-   It’s recommended to have tasks size such that they can be completed
    during the task followup period. This means that tasks would always
    be either 0 or 100 complete but nothing between

Results
------------------------------------

### Not everything targeted got done \*)

-   198 storypoints have to be moved to the next release
-   Service design related stories because of the lack of partner
-   JulkICTLab related stories because of the lack of customer
-   Some documentation polishing tasks and end to end test workshop bugs
    because of the lack of capacity
-   Update OpenStack to Havana because of the lack of capacity and
    unexpected complexity of HA
-   Swift because of the lack of capacity and unexpected complexity of
    HA

### Some content was inserted on the go

-   Test management tool
-   Redmine improvements
-   Business process automation stories
-   VRK certificate risk mitigation
-   Frontend process improvements (managing input coming from outside)
-   Surprise high priority tasks from management

### Lot of things got done

-   135 storypoints got done
-   Plaza concept
-   We have a solution to monitor our infrastructure
-   OpenStack functioning and Cinder works
-   Documentation improvements
-   Provisioning
-   Contract works proceeds and we expect to get new users to FORGE in
    few days

### Summary

-   The effective time in this release was closer to 1 month than 2
    months because of the Christmas and new year period and vacations
-   We had ambitious targets and more content was planned than what we
    have capacity
-   Some high priority "surprise" tasks inserted on the go delays things
    that were originally planned
-   Some things have external dependency which we cannot really impact
    (service design partner) nor speed them up
-   We'd like to improve the documentation further and spend time with
    that
-   We don’t have enough capacity to do everything in the backlog in
    reasonable amount of time and with the quality we want
-   We are ready to start taking customers in using manual process
-   Progress has been rapid in the areas where no interruptions occur

### \*) Following stories were not done and had to be moved to the next release 2014-03.

        #   Tracker Subject Project Status  Story points
    CSC                     
        356 Story   Test: User is able to manage VM     CSC In Progress 7
        261 Story   Set up and performance test Equallogic  CSC In Progress 13
        257 Story   Set up HA stack CSC In Progress 13
        243 Story   Update OpenStack to Havana  CSC Reviewed    
        242 Story   Monitoring of the IaaS platform CSC In Progress 
        171 Story   Advanced IaaS Reporting CSC Reviewed    
        149 Story   Set up swift    CSC In Progress 21
        148 Story   Set up cinder   CSC In Progress 13
        144 Story   Implement live migration    CSC In Progress 3
    DIGILE                      
        685 Story   Announcements for Affiliates    DIGILE  Reviewed    5
        627 Story   Test management tool deployment DIGILE  Reviewed    5
        625 Story   Infrastructure monitoring for internal use and to be used as an example DIGILE  Reviewed    13
        624 Story   PLAZA implementation plan   DIGILE  Reviewed    3
        614 Change  Improve Redmine and plugins DIGILE  Reviewed    5
        578 Story   Business process automation stories DIGILE  Reviewed    8
        564 Bug Admin (affliate) account should be informed when  techincal account creation is done    DIGILE  New 
        563 Bug Contract template should have the same info as in wiki for default quota    DIGILE  New 
        485 Story   End to end test workshop bugs   DIGILE  Reviewed    8
        422 Story   Polish the minumun viable FORGE documentation   DIGILE  Reviewed    8
        412 Story   Landing process and tools for FORGE Affiliates  DIGILE  Reopened    
        411 Story   D2I VisualLabel DIGILE  Reopened    
        406 Story   Polish FORGE service design documentation   DIGILE  Reopened    
        282 Story   Partner & owner of the service design concept   DIGILE  Reviewed    8
        245 Story   Support for manual contracting process  DIGILE  Reviewed    13
        219 Story   JulkICT Lab development support DIGILE  Reopened    
        212 Story   JulkICT Lab stakeholder and community dialogue  DIGILE  Reopened    2
        190 Story   The scope of service design support DIGILE  Reopened    
        189 Story   Reference model/flow for service desing DIGILE  Reopened    
        187 Story   IaaS infrastructure provisioning implementation DIGILE  Reviewed    13
        180 Story   Service Design support for FORGE affiliates DIGILE  Reopened    
        179 Story   Service Design examples for FORGE affiliates    DIGILE  Reopened    
        178 Story   Operating system images DIGILE  Reviewed    8
        165 Story   Service design concept for FORGE    DIGILE  Reviewed    21
    KE                      
        726 Story   Support process flow    FORGE   New 
        723 Story   Monitoring FAP troughput    KE  New 8

                            198


Release 2014-03
====================================================

-   Content and burnup charts are available in Redmine
    (=release notes)
-   Duration 2014-02-03 - 2014-03-28
-   Previous release is [Release\_2014-01](#release-2014-01)
-   Next release is [Release\_2014-06](#release-2014-06)

Targets
------------------------------------

-   FORGE public launch 23th of April 2014
-   External facade of FORGE service lab (sales and marketing)
    -   Public web pages of FORGE
-   FORGE Dashboard (aka. FORGE Landing Page) that is visible after the
    login
    -   It's now in Redmine, but Drupal to be used instead
    -   Account mgmt
    -   Gateway to all other features in FORGE Service Lab
        (Wiki, Gitlab,...)
-   FORGE Plaza up and running as a service and as a process
-   Support for pilot projects
    -   JulkICT Lab minimum viable product ready
    -   Land survey
    -   others
-   Documentation improvements
    -   Screencast recording solution
    -   FORGE introduction video
    -   FORGE tutorial videos (2-5 max)
    -   Continuous wiki improvements
-   Cloud improvements
    -   Capacity for 2nd level support
    -   Upgrade to Havana
    -   Swift
    -   Plans ready for the next cloud HW investment
-   Improving support operations
    -   Scalability
    -   Support documentation
    -   Support function process and practises improvements and
        processes documented

### Less important

-   Automating all the customer facing processes (contracting, computing
    resource allocation)
-   Billing, ERP
-   Training partner and training concept and MVP
    -   Decision of what kind of training solutions there will
        be...videos, f2f, workshops, manuals...)

### Dropped

-   Infrastructure configuration management support. (Examples and owner
    within DIGILE)

### Following planning principles are recommended

-   [Project\_planning](3_OperationalGuides.md#project-planning)

Results
------------------------------------

### Not everything targeted got done. See below \*)

-   170 storypoints have to be moved to the next release
-   Service design related stories are late
-   Documentation related stories (videorecordings) are late and pending
    hardware (camera, mic) and FORGE look and feel renewal
-   FORGE WEB, Plaza and Dashboard related stories appear being late
    from Inc03 but it should be noted that lot of content was added to
    Inc03 on the go while the right release would have been
    Inc06 instead.
-   D2I visual label support has not started because contract signing is
    pending
-   It should be noted that the risk "Single exploited VM instance
    breaks down network" is still kept open on purpose even when there
    are related mitigations implemented.

### Some content was inserted on the go

-   Lot of FORGE Web, Plaza and Dashboard content
-   Process related content: Announcements, Incident procedure
-   Surprise high priority tasks from management don't show up as user
    stories but reduced the capacity
-   Changes in Redmine projects (FORGE Support was split into FORGE
    Support and FORGE Forums, LDAP changes, role changes in
    related places) due to new roles introduced by partner roles
-   Admin machine

### Lot of things got done

-   386 storypoints got done
-   Upgrade OpenStack to Havana and High Availability (HA) setup
-   Object storage (Swift)
-   Agreed JulkICTLab deliverables were completed (CentOS VM image,
    identity backend and SSO)
-   Pilot projects have started successfully
-   FORGE WEB, Dashboard and Plaza work has started and development is
    proceeding and visible in the test environment.
-   Testing is operational
-   Monitoring FORGE internal services with Nagios and example Ansible
    playbook for it
-   FORGE reference process model was created...work still continues
-   Operating system images produced (Debian, CentOS and Ubuntu VMs)
-   Process improvements: Debian VM image generation automation, Method
    for making announcements (e.g. service breaks) is in place as well
    as Incident process.
-   A centralized admin machine was set up where admin tools are present
    and all admin tasks can be performed
-   Lot of documentation updates and improvements in readability

### Summary

-   **Pilot projects** have started successfully. Welcome new pilots!
-   **OpenStack** is in nice shape and so are other internal services
    (Redmine, XMPP, CAS...)
-   **LDAP structure needs to be rethought** since new access control
    requirements were introduced by partner roles
-   We had **ambitious targets** again and lot of content was waiting
    for partner to take over
-   **FORGE WEB, Plaza and Dashboard** got a quick start and is
    proceeding fast. Welcome new partners!
-   **Capacity has increased** along with new partners on board
-   We were still unable to account high priority **"surprise" tasks**
    coming from management which cause us having less capacity than
    originally thought. We should account them better in planning and
    not take too much content in.
-   Some things have **external dependency** which we cannot really
    impact on (e.g. process of getting partners onboard and process on
    getting pilot projects to sign up the contracts) nor speed them up
-   Progress has been rapid in the areas where **no interruptions**
    occur
-   We have to continue having following FORGE public related **business
    targets** in the next release 06
    -   FORGE public launch 23th of April 2014
    -   FORGE WEB. External facade of FORGE service lab (sales
        and marketing)
    -   FORGE Dashboard (aka. FORGE Landing Page) that is visible after
        the login
    -   FORGE Plaza up and running as a service and as a process

### Leftovers \*)

Following stories were not done and had to be moved to the next release
2014-06.

	----------------------------------------------------------------------------
			   \#         Tracker    Subject    Project    Status     Story
																	  points
	---------- ---------- ---------- ---------- ---------- ---------- ----------
	DIGILE                                                            

			   798        Story      Service    DIGILE     Reviewed   8
									 design                           
									 concept                          
									 for FORGE                        
									 verificati                       
									 on                               

			   797        Story      Service    DIGILE     Reviewed   8
									 design                           
									 concept                          
									 for FORGE                        
									 implementa                       
									 tion                             

			   771        Story      Journey    DIGILE     In         
									 canvas                Progress   

			   758        Story      DOCUMENTAT DIGILE     Reviewed   21
									 ION:                             
									 Tutorial                         
									 videos for                       
									 FORGE                            

			   757        Story      DOCUMENTAT DIGILE     Reopened   
									 ION:                             
									 Introducti                       
									 on                               
									 video for                        
									 FORGE                            

			   746        Story      WEB:       DIGILE     New        
									 Content                          
									 for FORGE                        
									 Web                              

			   614        Change     Improve    DIGILE     Reviewed   5
									 Redmine                          
									 and                              
									 plugins                          

			   563        Bug        Contract   DIGILE     New        
									 template                         
									 should                           
									 have the                         
									 same info                        
									 as in wiki                       
									 for                              
									 default                          
									 quota                            

			   487        Story      PLAZA      DIGILE     New        
									 internal                         
									 guidance:                        
									 instructio                       
									 ns                               
									 to fill                          
									 out                              
									 Partner                          
									 offering                         
									 descriptio                       
									 n                                

			   422        Story      Polish the DIGILE     Reviewed   8
									 minumun                          
									 viable                           
									 FORGE                            
									 documentat                       
									 ion                              

			   411        Epic       D2I:       DIGILE     Reopened   
									 VisualLabe                       
									 l                                
									 support                          

			   406        Story      SERVICEDES DIGILE     Reopened   
									 IGN:                             
									 Polish                           
									 FORGE                            
									 service                          
									 design                           
									 documentat                       
									 ion                              

			   282        Story      Partner &  DIGILE     Reviewed   8
									 owner of                         
									 the                              
									 service                          
									 design                           
									 concept                          

			   245        Story      Support    DIGILE     Reviewed   13
									 for manual                       
									 contractin                       
									 g                                
									 process                          

			   212        Story      JULKICTLAB DIGILE     Reviewed   2
									 :                                
									 stakeholde                       
									 r                                
									 and                              
									 community                        
									 dialogue                         

			   190        Story      SERVICEDES DIGILE     Reopened   
									 IGN:                             
									 The scope                        
									 of service                       
									 design                           
									 support                          

			   180        Story      SERVICEDES DIGILE     Reopened   
									 IGN:                             
									 support                          
									 for FORGE                        
									 affiliates                       

			   179        Story      SERVICEDES DIGILE     Reopened   
									 IGN:                             
									 examples                         
									 for FORGE                        
									 affiliates                       

			   165        Story      PLAZA user DIGILE     Reviewed   13
									 experience                       
									 in FORGE                         
									 context                          
									 descriptio                       
									 n                                

	DRUID                                                             

			   1286       Story      WEB: Term  DRUID      New        
									 &                                
									 Conditions                       
									 for web                          

			   1285       Story      WEB:       DRUID      New        
									 Contact us                       

			   1244       Story      DASHBOARD  DRUID      New        
									 Tutorial                         
									 graphical                        
									 element                          
									 implementa                       
									 tion                             

			   1177       Story      WEB: front DRUID      New        
									 page -                           
									 general                          
									 layout                           
									 javascript                       
									 s                                

			   1176       Epic       Plaza:     DRUID      New        
									 Tutorial                         
									 graphical                        
									 navigation                       
									 element                          

			   1174       Epic       WEB:       DRUID      New        5
									 Caching                          

			   1172       Epic       WEB:       DRUID      New        
									 Testing                          

			   1171       Epic       WEB:       DRUID      New        
									 Define all                       
									 commenting                       
									 related                          
									 fields and                       
									 ensure                           
									 those                            
									 working in                       
									 blog etc.                        

			   1169       Epic       WEB:       DRUID      In         
									 changes to            Progress   
									 registrati                       
									 on                               
									 wizard                           

			   1168       Epic       WEB: how   DRUID      New        
									 to manage                        
									 logged in                        
									 users that                       
									 have not                         
									 yet                              
									 generated                        
									 contracts                        

			   1157       Story      WEB: Plaza DRUID      New        
									 offering                         
									 liftup                           

			   1156       Story      WEB: Plaza DRUID      New        
									 offering                         
									 listing                          
									 page                             

			   1094       Story      WEB: Spell DRUID      New        1
									 check for                        
									 content                          
									 editor                           

			   1079       Story      PLAZA:     DRUID      New        
									 thumb                            
									 up/down                          

			   1076       Epic       PLAZA: how DRUID      New        
									 to page                          

			   966        Story      WEB:       DRUID      New        
									 mapping of                       
									 Drupal and                       
									 LDAP user                        

			   940        Epic       WEB:       DRUID      New        5
									 Roadmap                          
									 for FORGE                        

			   938        Story      WEB:       DRUID      New        8
									 roadmap                          
									 for FORGE                        
									 Plaza                            
									 future                           
									 developmen                       
									 t                                

			   937        Story      WEB: Plaza DRUID      New        
									 offering                         
									 page                             

			   934        Epic       WEB:       DRUID      New        20
									 Online                           
									 signature                        

			   930        Epic       WEB:       DRUID      New        5
									 sign-up +                        
									 sign-in                          

			   929        Epic       WEB:       DRUID      New        40
									 Basics                           
									 about                            
									 FORGE                            

			   656        Story      DASHBOARD: DRUID      Reopened   
									 Account                          
									 and                              
									 contract                         
									 governance                       
									 system                           

			   655        Story      DASHBOARD: DRUID      Reopened   
									 Affiliate                        
									 account                          
									 management                       

			   601        Story      WEB,       DRUID      Reviewed   
									 DASHBOARD                        
									 and PLAZA                        
									 are                              
									 accessible                       
									 in FORGE                         
									 Drupal                           
									 production                       
									 environmen                       
									 t                                
									 (public                          
									 launch)                          

			   575        Story      PLAZA      DRUID      New        
									 Customisat                       
									 ion                              

			   574        Story      PLAZA      DRUID      New        
									 becoming                         
									 FORGE                            
									 Partner                          
									 and                              
									 entering                         
									 Plaza:                           
									 purpose                          

			   533        Story      PLAZA      DRUID      New        
									 becoming                         
									 FORGE                            
									 Partner                          
									 and                              
									 entering                         
									 Plaza:                           
									 guidance                         

			   530        Story      PLAZA      DRUID      New        
									 service                          
									 ramp-down                        
									 as per                           
									 contract                         

			   529        Story      PLAZA:     DRUID      New        
									 updating                         
									 Affiliate                        
									 informatio                       
									 n                                

			   527        Story      PLAZA      DRUID      New        
									 provides                         
									 overview                         
									 of all                           
									 offering                         
									 available                        
									 through                          
									 Plaza                            

			   412        Story      DASHBOARD: DRUID      Reopened   
									 Landing                          
									 process                          
									 and tools                        
									 for FORGE                        
									 Affiliates                       

			   197        Story      PLAZA can  DRUID      Reopened   
									 be used to                       
									 search for                       
									 a digital                        
									 service                          

			   196        Story      PLAZA      DRUID      Reopened   
									 services                         
									 are                              
									 organized                        
									 into                             
									 categories                       
									 in the                           
									 catalog                          

			   166        Story      DASHBOARD: DRUID      Reopened   
									 Affiliate                        
									 can                              
									 initiate                         
									 automatic                        
									 contractin                       
									 g                                
									 and CRA                          
									 allocation                       
									 process                          

	FORGE                                                             

			   610        Risk       Single     FORGE      Reviewed   
									 exploited                        
									 VM                               
									 instance                         
									 breaks                           
									 down                             
									 network                          
									 for the                          
									 whole                            
									 OpenStack                        
									 deployment                       

																	  170
	----------------------------------------------------------------------------



Release 2014-06
====================================================

-   Content and burnup charts are available in Redmine
    (=release notes)
-   duration 2014-03-31 - 2014-06-24
-   Previous release is [Release\_2014-03](#release-2014-03)
-   Next release is [Release\_2014-09](#release-2014-09)

Targets and results
------------------------------------------------------------

### 1. Support for deployment to production in the commercial cloud

-   Example deployment of Drupal cluster to various clouds (Azure,
    Amazon, Rackspace, Cybercom Finland, Tieto)
-   Process documentation and improvement
-   Ansible playbook instructions

    **Results**

    -   Support for deployment to production in the commercial cloud
        work was started right after we got a new partner team onboard.
        Welcome new partner team!
    -   A deployment to FORGE cloud was done successfully with the
        deployment playbook that was created earlier to setup a Drupal
        cluster for FORGE WEB, Plaza and Dashboard
    -   Documentation of the guidelines has started and is available in
        wiki.
    -   Accounts for Rackspace, Amazon and Azure exists while getting
        accounts for Cybercom and Tieto require something else than just
        a credit card and is work in progress.
    -   The deployment to Rackspace, Amazon and Azure will be tried out
        next

### 2. R&D operational improvements

-   Continuous delivery
-   Continuous integration
-   Test automation
-   Configuration management
-   All services as playbook. Ability to easily reproduce FORGE
    installation

    **Results**

    -   Jenkins CI server has been set up and is operational
    -   We have deployment playbooks ready for GitLab and Plaza and they
        also have a deployment pipeline set up in Jenkins.
    -   We can deploy Plaza automatically to testing environment and
        manually to production environment straight from Jenkins UI.
        Same should be possible with GitLab but we have not enforced
        that yet.
    -   FORGE's deployment pipeline is defined and documented and the
        guideline is available also for affiliates.
    -   The automation of the test cases has started and we're now
        increasing the test automation asset in addition to running
        manual tests
    -   We'll continue adding the deployment pipeline for other FORGE
        services too

### 3. Generic identity management example solution for public sector services

-   SAML 2.0 compatible
-   XACML 3.0 support
-   LDAP based
-   Federation capability
-   Tested with government identity management
-   Requirements references from CSC, MML, Palveluväylä. Customer is
    FORGE (USERNAME REMOVED)

    **Results**

    -   The big picture has been defined in wiki
    -   We should have an access to Virtu test APIs but we haven't tried
        that in practice yet
    -   The implementation of this work has not started because of the
        lack of capacity

### 4. Generic analytics example solution

-   FORGE Plaza, Dashboard, WEB
-   Analysis
-   Improvements to FORGE processes how to use the data

    **Results**

    -   The implementation of this work has not started because of the
        lack of capacity

### 5. Security inside OpenStack project subnet

-   Network monitoring, detect anomalies with e.g. Bro
-   Make example solution
-   Automatize vulnerability check testing (e.g. Backtrack)
-   Document the security of FORGE. What is being done, not done, by
    who, when

    **Results**

    -   We have a Naqios monitoring system in shape to monitor the
        availability of our services and means to automatically file an
        issue in case of a problem.
    -   We run ad-hoc security tests. Couple of issues have been found
        and fixed.
    -   We don't have systematic and ongoing network monitoring
        capability in place and the implementation of this work has not
        really started because of the lack of capacity

### 6. Security in IaaS

-   Network monitoring, detect anomalies with e.g. Bro
-   Automatize vulnerability check testing (e.g. Backtrack)
-   Document the security of IaaS. What is being done, not done, by who,
    when

    **Results**

    -   IaaS monitoring system is in place so that we can react upon
        service breaks
    -   No network monitoring nor vulnerability check testing is in
        place

### 7. Off the shelf marketplace study

-   Drupal based
-   Contract automatisation capability
-   Payment support (credit cards, paypal) extendable
-   Skinnable
-   Workflows tailorable

    **Results**

    -   Study exists but not yet reviewed
    -   Next the study to be reviewed and then the implementation plan
        to be approved
    -   The implementation of this work has not started because of the
        lack of capacity

### 8. Generic big data example solution

-   Playbooks for DB engine
-   How to connect big data engine to object storage swift

    **Results**

    -   The implementation of this work has not started because of the
        lack of capacity

### 9. Performance testing example solution

-   Study and select tool for perf tests so that tests can be
    automatized
-   Create test cases to measure Redmine, Drupal performance

    **Results**

    -   The implementation of this work has not started because of the
        lack of capacity

### 10. Computing resources reporting on project basis vs total available

-   2nd HW procurement ready
-   2nd HW installation ready
-   Big data readyness verified
-   E.g. application would be Hadoop cluster with swift as a storage
    engine

    **Results**

    -   The proposal for 2nd HW installation is ready and the approach
        selected is a generic that supports big data but can be reused
        for ordinary computing in case big data (hadoop specifics) is
        not needed.
    -   Horizon or command line tool (nova) shows some usage but not a
        nice summary e.g. vs total resources. CSC has been reporting
        capacity usage for steering groups with Excel
    -   A Python script has been developed and should be finalised by
        the end of June. Also DIGILE people with admin rights can
        then use. Further development need likely during the
        next release.
    -   Note! It would be possible to try out Hadoop already now
        utilizing current FORGE OpenStack
    -   Acquisition was postponed because there was capacity available
        and the requirements for the new kind of (big data) analysis
        environment were delayed.

### 11. 1st complete version of JulkICT Lab is ready with domain specific service design

-   **Results**
-   The status of the JulkICT service design is not yet visible in
    Redmine since the project has not really started using it for
    project management.
-   Two workshops held with VM, MML facilitated by JAMK and
    DIGILE (Kata). The third workshop scheduled with VM in
    September 2nd.
-   JULKICT requirements towards Plaza are being collected as a separate
    workstream by Kata.
-   More information from Kata.

### 12. Evaluation and OpenStack upgrades as upstream proceeds

-   **Results**
-   CSC is driving the OpenStack upgrades. The current plan is to
    upgrade to Icehouse in August
-   There are not yet requirements to have a Ceilometer nor Heat.

### 13. Training solutions operational

-   **Results**
-   The implementation of this work has not started because of the lack
    of capacity

### 14. Misc

-   FORGE public launch 23th of April 2014 was held and FORGE WEB,
    Dashboard and Plaza are operational.
-   We continued working on FORGE WEB, Plaza and Dashboard (Drupal)
    further development and they now support FORGE single sign on (SSO)
    authentication and LDAP
-   Accounts still need to be revisited and content created with
    temporary Drupal specific accounts must be migrated to
    FORGE accounts.
-   Lot of refactoring and UI improvements in Drupal
-   We have tutorial videos now and we have capability to easily produce
    more
-   Support ticket (FAP) statistics was improved

Summary
------------------------------------

-   Not everything targeted got done and 158 storypoints have to be
    moved to the next release. See the list of leftovers below \*)
-   High priority "surprise" tasks coming from out of the sprint
    planning still causes reduced sprint capacity. We should account
    them better in planning and not take too much content in.
-   Lot of things got done and 463 storypoints were completed and
    implementation was rapid in the areas where no
    interruptions occurred.
-   The focus has clearly been in operational improvements,
    documentation and Drupal while the rest of the areas have then
    suffered
-   No new service development projects have started and D2I visual
    label support work has not started because contract signing is
    pending
-   We have nice set of partners in Plaza
-   Lot of documentation updates and improvements in readability
-   OpenStack and other supporting services (Redmine, XMPP, CAS...) are
    operational
-   Pilot projects are operational in FORGE
-   We will have to continue working on the same business target we had
    in Inc06

### Leftovers \*)

Following issues were not done and had to be moved to the next release
2014-09.

	----------------------------------------------------------------------------
	Project    \#         Tracker    Subject    Status     Story      Related
														   points     issues
	---------- ---------- ---------- ---------- ---------- ---------- ----------
	CSC        1279       Story      Icehouse   New                   
									 update                           

	CSC        1257       Bug        Regular    New                   
									 users                            
									 should not                       
									 be able to                       
									 make                             
									 images                           
									 public                           

	CSC        960        Story      Resource   New                   
									 utilizatio                       
									 n                                
									 vs total                         
									 report                           

	CSC        781        Story      LoadBalanc New                   
									 er                               
									 as a                             
									 Service                          

	CSC        722        Story      HW         Reviewed              
									 installati                       
									 on                               
									 round 2                          
									 implementa                       
									 tion                             

	CSC        721        Story      HW         Reviewed   13.00      
									 installati                       
									 on                               
									 round 2                          
									 planned                          

	CSC        569        Bug        Newly      Resolved              
									 created                          
									 security                         
									 group                            
									 cannot be                        
									 added                            
									 already                          
									 existing                         
									 instance                         

	CSC        171        Story      Advanced   Reviewed   8.00       Related to
									 IaaS                             [\#229](/i
									 Reporting                        ssues/229 
																	  "OpenStack
																	   tenant mo
																	  nitoring a
																	  nd alertin
																	  g (Closed)
																	  ")

	---        ---        ---        ---        ---        ---        ---

	DIGILE     2385       Story      Hadoop     New                   
									 example                          
									 playbook                         
									 for                              
									 affiliates                       
									 (savanna?)                       

	DIGILE     2375       Story      DOCUMENTAT New                   
									 ION:                             
									 Test                             
									 automation                       
									 documentat                       
									 ion                              
									 for                              
									 Affiliates                       

	DIGILE     2343       Story      ANALYTICS: New                   
									 Run                              
									 analytics                        
									 for FORGE                        
									 WEB, Plaza                       
									 and                              
									 Dashboard                        

	DIGILE     2342       Story      ANALYTICS: New                   
									 Develop a                        
									 playbook                         
									 for                              
									 analytics                        

	DIGILE     2341       Story      ANALYTICS: New                   
									 Analytics                        
									 solution                         
									 proposal                         

	DIGILE     2326       Story      TA: Test   New                   
									 automation                       
									 example                          
									 solution                         
									 for                              
									 affiliates                       

	DIGILE     2325       Story      CI:        New                   
									 Continuous                       
									 integratio                       
									 n                                
									 example                          
									 for                              
									 affiliates                       

	DIGILE     2324       Story      ANALYTICS: New                   
									 Analytics                        
									 example                          
									 for                              
									 service                          
									 developers                       

	DIGILE     2321       Story      CI: Single New                   
									 sign on to                       
									 Jenkins                          
									 with FORGE                       
									 CAS                              

	DIGILE     2308       Story      FORGE      New                   
									 support                          
									 services'                        
									 backups                          

	DIGILE     2188       Story      Resources  New                   
									 utilizatio                       
									 n                                
									 reporting                        
									 requiremen                       
									 ts.                              
									 Study                            
									 ceilometer                       
									 vs.                              
									 informatio                       
									 n                                
									 from nova                        

	DIGILE     2138       Story      PLAZA      New        3.00       
									 requiremen                       
									 ts                               
									 iteration                        

	DIGILE     1966       Story      DOCUMENTAT New                   
									 ION:                             
									 FORGE                            
									 Reference                        
									 model                            
									 tutorial                         
									 video                            

	DIGILE     1964       Story      DOCUMENTAT New                   
									 ION:                             
									 FORGE                            
									 Contract                         
									 wizard                           
									 tutorial                         
									 video                            

	DIGILE     1957       Story      DOCUMENTAT New                   
									 ION:                             
									 Developmen                       
									 t                                
									 process                          
									 descriptio                       
									 n                                

	DIGILE     1954       Bug        Performanc New                   
									 e                                
									 issues in                        
									 forgeservi                       
									 celab.fi                         
									 (productio                       
									 n)                               

	DIGILE     1695       Story      Refactor   New                   
									 the                              
									 production                       
									 LDAP, so                         
									 that it's                        
									 simply                           
									 reproducib                       
									 le.                              

	DIGILE     1688       Story      TA:        Reviewed   21.00      
									 Prepare                          
									 FORGE                            
									 Service                          
									 Lab test                         
									 environmen                       
									 t                                

	DIGILE     1665       Epic       CM:        New                   
									 Configurat                       
									 ion                              
									 management                       
									 for FORGE                        
									 services                         

	DIGILE     1663       Story      CI:        New                   Related to
									 Continuous                       [\#176](/i
									 integratio                       ssues/176 
									 n                                "CI: Conti
									 of CAS                           nuous inte
																	  gration of
																	   FORGE ser
																	  vices (Rev
																	  iewed)")

	DIGILE     1562       Epic       RM:        New                   
									 Release                          
									 management                       
									 of FORGE                         
									 services                         

	DIGILE     1532       Story      DOCUMENTAT New                   
									 ION:                             
									 Backup                           
									 instructio                       
									 ns                               
									 for                              
									 Affiliates                       

	DIGILE     1509       Story      Revisit    New                   
									 the                              
									 mission                          
									 and                              
									 strategy                         

	DIGILE     1464       Story      What is    New                   
									 the plan                         
									 to collect                       
									 customer                         
									 input                            

	DIGILE     1303       Story      Legal      New                   
									 process                          
									 and                              
									 training                         

	DIGILE     1195       Story      Test       New                   
									 statistics                       
									 for Story,                       
									 Sprint and                       
									 Increment                        

	DIGILE     1151       Story      CI:        New        13.00      Related to
									 Continuous                       [\#176](/i
									 integratio                       ssues/176 
									 n                                "CI: Conti
									 of Redmine                       nuous inte
																	  gration of
																	   FORGE ser
																	  vices (Rev
																	  iewed)")

	DIGILE     1145       Story      REDMINE:   New        8.00       
									 Redmine                          
									 example                          
									 for                              
									 affiliates                       

	DIGILE     1086       Story      OpenStack  New                   
									 CPU                              
									 overcommit                       
									 ment                             
									 ratio                            
									 study                            

	DIGILE     796        Epic       ANALYTICS: New                   
									 Analytics                        
									 for FORGE                        
									 WEB, Plaza                       
									 and                              
									 Dashboard                        

	DIGILE     771        Story      Journey    In                    
									 canvas     Progress              

	DIGILE     759        Story      DOCUMENTAT Reviewed              
									 ION:                             
									 Wiki                             
									 improvemen                       
									 ts                               

	DIGILE     577        Story      FORGE      New                   
									 Service                          
									 Lab home                         
									 view                             
									 platform                         
									 stories                          

	DIGILE     422        Story      Polish the Reviewed   8.00       
									 minumun                          
									 viable                           
									 FORGE                            
									 documentat                       
									 ion                              

	DIGILE     411        Epic       D2I:       Reopened              
									 VisualLabe                       
									 l                                
									 support                          

	DIGILE     282        Story      Partner &  Reviewed   8.00       
									 owner of                         
									 the                              
									 service                          
									 design                           
									 concept                          

	DIGILE     245        Story      Support    Reviewed   13.00      
									 for manual                       
									 contractin                       
									 g                                
									 process                          

	DIGILE     230        Epic       Modern     Reopened              Related to
									 tools for                        [\#176](/i
									 affiliates                       ssues/176 
																	  "CI: Conti
																	  nuous inte
																	  gration of
																	   FORGE ser
																	  vices (Rev
																	  iewed)")

	DIGILE     218        Story      TRAINING:  New                   
									 Targeted                         
									 training                         
									 concept                          
									 for                              
									 JulkICT                          
									 Lab                              

	DIGILE     217        Story      TRAINING:  New                   
									 Training                         
									 concept                          
									 for the                          
									 technical                        
									 contacts                         
									 of FORGE                         
									 affiliates                       

	DIGILE     212        Story      JULKICTLAB Reviewed   2.00       
									 :                                
									 stakeholde                       
									 r                                
									 and                              
									 community                        
									 dialogue                         

	DIGILE     183        Story      2nd tier   Reviewed              
									 technical                        
									 support                          
									 for                              
									 service                          
									 developmen                       
									 t                                

	---        ---        ---        ---        ---        ---        ---

	DRUID      2388       Story      PLAZA:     New        2.00       
									 Offering                         
									 listing                          
									 needs to                         
									 be                               
									 filerable                        

	DRUID      2387       Story      WEB:       New        1.00       
									 Change the                       
									 feed block                       
									 filtering                        
									 colors                           

	DRUID      2374       Story      WEB:       New        2.00       
									 Mobile                           
									 navigation                       
									 needs to                         
									 have all                         
									 the links                        
									 available                        
									 as the                           
									 desktop                          
									 version                          

	DRUID      2316       Story      JOIN FORGE New                   
									 adjustment                       
									 s                                

	DRUID      2305       Story      PLAZA:     New        1.00       
									 Taxonomy                         
									 term                             
									 management                       
									 view needs                       
									 ability to                       
									 modify                           
									 hierarchy                        
									 and order                        
									 of the                           
									 terms                            
									 easily                           

	DRUID      2278       Story      WEB: Feed  New                   
									 changes                          

	DRUID      2241       Bug        Language   New        1.00       
									 changes                          
									 from                             
									 finnish to                       
									 english in                       
									 "FORGE                           
									 Service                          
									 Lab Use                          
									 Instructio                       
									 ns"                              
									 page                             

	DRUID      2215       Bug        Administer New        1.00       
									 comments                         
									 link                             
									 active                           
									 status                           

	DRUID      1950       Bug        forgeservi New        1.00       Duplicated
									 celab.fi                         by
									 title                            [\#2157](/
									 localizati                       issues/215
									 on                               7 "Plaza p
									 missing                          age title 
																	  always in 
																	  Finnish. (
																	  Closed)")

	DRUID      1865       Bug        Feeds in   New        1.00       
									 finnish                          
									 has only                         
									 one item                         

	DRUID      1648       Story      WEB: Plaza New        1.00       
									 offering?I                       
									 E9                               
									 gets                             
									 ckeditor.j                       
									 s                                
									 error when                       
									 logged in                        
									 and on                           
									 product                          
									 offering                         
									 page                             

	DRUID      1593       Bug        Carousel   New        2.00       
									 items are                        
									 updated/ch                       
									 anged                            
									 while                            
									 playing                          
									 video in                         
									 carousel                         

	DRUID      1590       Bug        "Why?" &   Reopened   2.00       
									 "What?"                          
									 blocks are                       
									 opened                           
									 with title                       
									 cutted                           

	DRUID      1588       Story      PLAZA: FSL New                   
									 Use                              
									 Instructio                       
									 n                                
									 change                           
									 acceptance                       

	DRUID      1567       Bug        Role       New        1.00       
									 selection                        
									 is cleared                       
									 after                            
									 "Learn                           
									 more" and                        
									 "Back to                         
									 role                             
									 selection"                       

	DRUID      1565       Bug        Video      New        2.00       
									 playback                         
									 continues                        
									 when                             
									 change the                       
									 item in                          
									 carousel.                        

	DRUID      1563       Bug        Dashboard  New        1.00       
									 layout is                        
									 broken                           
									 when zoom                        
									 out                              

	DRUID      1521       Bug        Some       New        2.00       
									 special                          
									 charaters                        
									 are                              
									 converted                        
									 to HTML                          
									 Number                           

	DRUID      1512       Bug        Configurat New        2.00       
									 ion                              
									 link not                         
									 working                          

	DRUID      1500       Bug        About      New        1.00       
									 Forge                            
									 -&gt;                            
									 Feeds                            
									 opens page                       
									 footer in                        
									 Firefox                          

	DRUID      1177       Story      WEB: Front New                   
									 page -                           
									 general                          
									 layout                           
									 javascript                       
									 s                                

	DRUID      1171       Epic       WEB:       New                   
									 Define all                       
									 commenting                       
									 related                          
									 fields and                       
									 ensure                           
									 those                            
									 working in                       
									 blog etc.                        

	DRUID      971        Epic       WEB:       New                   
									 Multiple                         
									 users can                        
									 access/edi                       
									 t                                
									 ?company                         
									 contracts                        

	DRUID      940        Epic       WEB:       New                   
									 Roadmap                          
									 for FORGE                        

	DRUID      934        Epic       PLAZA:     New                   
									 Online                           
									 signature                        

	DRUID      656        Story      DASHBOARD: Reopened              
									 Account                          
									 and                              
									 contract                         
									 governance                       
									 system                           

	DRUID      655        Story      DASHBOARD: Reopened              
									 Affiliate                        
									 account                          
									 management                       

	DRUID      530        Story      PLAZA      New                   
									 service                          
									 ramp-down                        
									 as per                           
									 contract                         

	DRUID      412        Story      DASHBOARD: Reopened              
									 Landing                          
									 process                          
									 and tools                        
									 for FORGE                        
									 Affiliates                       

	DRUID      197        Story      PLAZA can  Reopened              
									 be used to                       
									 search for                       
									 a digital                        
									 service                          

	DRUID      196        Story      PLAZA      Reopened              
									 services                         
									 are                              
									 organized                        
									 into                             
									 categories                       
									 in the                           
									 catalog                          

	DRUID      166        Story      DASHBOARD: Reopened              
									 Affiliate                        
									 can                              
									 initiate                         
									 automatic                        
									 contractin                       
									 g                                
									 and CRA                          
									 allocation                       
									 process                          

	DRUID      108        Epic       DASHBOARD: Reopened              
									 Affiliate                        
									 account                          
									 view                             

	FORGE      610        Risk       Single     Reviewed              Related to
									 exploited                        [\#630](/i
									 VM                               ssues/630 
									 instance                         "IDS syste
									 breaks                           m research
									 down                              feasibili
									 network                          ty for FOR
									 for the                          GE (Reject
									 whole                            ed)"),
									 OpenStack                        Related to
									 deployment                       [\#628](/i
																	  ssues/628 
																	  "Research 
																	  ratelimit 
																	  traffic pe
																	  r instance
																	   on OpenSt
																	  ack (Revie
																	  wed)"),
																	  Related to
																	  [\#631](/i
																	  ssues/631 
																	  "Incidents
																	   can be re
																	  ported bas
																	  ed on the 
																	  collected 
																	  security r
																	  elated sta
																	  tistics (C
																	  losed)"),
																	  Related to
																	  [\#632](/i
																	  ssues/632 
																	  "Define an
																	  d agree co
																	  mmon incid
																	  ent proced
																	  ure (Close
																	  d)")

	---        ---        ---        ---        ---        ---        ---

	KE         1903       Story      Account    New                   
									 creation                         
									 automatisa                       
									 tion                             

	---        ---        ---        ---        ---        ---        ---

	SERVICEDES 1873       Epic       JULKICT:   New                   Related to
	IGN                              JulkICT                          [\#1870](/
									 Lab                              issues/187
									 service                          0 "JULKICT
									 design                           : service 
									 project                          design pro
																	  ject plan 
																	  creation (
																	  Closed)"),
																	  Related to
																	  [\#1872](/
																	  issues/187
																	  2 "JULKICT
																	  : workshop
																	   23.5. (Cl
																	  osed)")

	SERVICEDES 1871       Epic       FORGE      New                   
	IGN                              Service                          
									 Lab                              
									 service                          
									 modeling                         
									 offering                         
									 definition                       

	SERVICEDES 1870       Story      JULKICT:   New        8.00       Related to
	IGN                              service                          [\#1873](/
									 design                           issues/187
									 project                          3 "JULKICT
									 plan                             : JulkICT 
									 creation                         Lab servic
																	  e design p
																	  roject (Cl
																	  osed)")

	SERVICEDES 798        Story      Service    Reviewed   8.00       
	IGN                              design                           
									 concept                          
									 for FORGE                        
									 verificati                       
									 on                               

	SERVICEDES 797        Story      Service    Reviewed   8.00       
	IGN                              design                           
									 concept                          
									 for FORGE                        
									 implementa                       
									 tion                             

	SERVICEDES 406        Story      Polish     Reopened              
	IGN                              FORGE                            
									 service                          
									 design                           
									 documentat                       
									 ion                              

	SERVICEDES 190        Story      The scope  Reopened              
	IGN                              of service                       
									 design                           
									 support                          

	SERVICEDES 189        Story      Reference  Resolved   13.00      
	IGN                              model/flow                       
									 for                              
									 service                          
									 desing                           

	SERVICEDES 180        Story      Support    Reopened              
	IGN                              for FORGE                        
									 affiliates                       

	SERVICEDES 179        Story      Examples   Reopened              
	IGN                              for FORGE                        
									 affiliates                       

	---        ---        ---        ---        ---        ---        ---
	----------------------------------------------------------------------------



Release 2014-09
====================================================

-   Content and burnup charts are available in Redmine
    (=release notes)
-   Duration 2014-06-25 - 2014-09-26
-   Previous release is [Release\_2014-06](#release-2014-06)
-   Next release is [Release\_2014-11](#release-2014-11)

Targets and results
------------------------------------------------------------

### 1. Generic identity management example solution for public sector services

-   SAML 2.0 compatible
-   XACML 3.0 support
-   LDAP based
-   Federation capability
-   Tested with government identity management
-   Requirements references from CSC, MML, Palveluväylä. Customer is
    FORGE (USERNAME REMOVED)

    **Results**

    -   LDAP backed IdP instance running
    -   Document about how it can be used to test SP is available in wiki
    -   It turned out to be impossible to connect to VIRTU because VIRTU
        is available for governmental organizations only
    -   As a result, there is SAML compliant IdP instance running which
        application developers can test their SP application against.
        The setup is similar to VIRTU.
    -   An example application is under construction

### 2. Generic analytics example solution

-   FORGE Plaza, Dashboard, WEB
-   Analysis
-   Improvements to FORGE processes how to use the data

    **Results**

    -   FORGE Web, Gitlab and Redmine are being analyzed both with Piwik
        and Google Analytics
    -   The data from analytics is being used on ad hoc manner and FORGE
        doesn't have analysis process in place to analyse data
        systematically
    -   Document and instructions about analytics solutions is available
        for Affiliates in wiki

### 3. Support for deployment to production in the commercial cloud

-   Example deployment of Drupal cluster to various clouds (Azure,
    Amazon, Rackspace, Cybercom Finland, Tieto)
-   Process documentation and improvement
-   Ansible playbook instructions

    **Results**

    -   Selected commercial cloud environments were experimented. The
        report is available in DEPLOYMENT project's internal wiki
    -   Based on the experiments, an extensive documentation about
        deployments to commercial clouds was produced and it is
        available for Affiliates at wiki
    -   Both Ansible documentation and instructions for deploying is
        available in wiki

### 4. R&D operational improvements

-   Continuous delivery
-   Continuous integration
-   Test automation
-   Configuration management
-   All services as playbook. Ability to easily reproduce FORGE
    installation

    **Results**

    -   FORGE has now a complete deployment pipeline defined and set up
        for WEB and Gitlab. The deployment pipeline includes both test
        and production environments and in desired cases (WEB) a devel
        environment too.
    -   Additionally FORGE has test environments available for Auth and
        Redmine even when deployment pipeline was not enabled for them
    -   Development process improvement enables following things: A
        source code commit may automatically trigger the deployment
        pipeline execution, a source code commit message can be used to
        automatically close the issue in the project management system,
        the deployment pipeline is able to automatically tag the good
        code into the version control system in case of test
        automation succeeded.
    -   FORGE also has a process in place where a product owner is able
        to see the automated and manual test results and can deploy to
        production with the click of a mouse button
    -   Jenkins is being used to orchestrated build, test and deployment
        activities
    -   Selenium RobotFW is being used for test automation
    -   There are no specific activities in terms of CM nor RM
    -   All selected services are available as playbooks. Note! it
        doesn't necessarily make sense to have a playbook for each and
        every service and e.g. there is no playbook to deploy complete
        FORGE Redmine
    -   FORGE has also improved monitoring with Nagios and it's possible
        to detect service failures.
    -   Monitoring agent (Nagios) is able to file bugs to the project
        management system automatically in case of a service failure. It
        can also close bugs automatically when it detects that the
        service returned back to normal operations.

### 5. Improvements in FORGE WEB, Plaza and Dashboard (Drupal)

-   Service developer landing page and navigation
-   Plaza iteration \#3: JulkICT Lab adjustments, bulletin board 1st
    version implementation and testing
-   UX improvements

    **Results**

    -   First version of service developer landing page has
        been implemented.
    -   First version of JulkICTLab specific functionality has been
        planned and developed and is in testing. Organization
        description for JulkICTLab exists on Plaza and JulkICTLab
        specific offering form is in testing. Visibility on Plaza has
        been planned and is in development.
    -   First test version of bulletin board is implemented. Further
        development of the functionality is waiting for design resource
        and probably will happen in next sprint.
    -   Light weight expert evaluation has been conducted for use case
        where user arrives to Forge web page and tries to get offering
        to Plaza. Writing of findings to stories is ongoing.

### 6. Security in IaaS

-   Network monitoring, detect anomalies with e.g. Bro
-   Automatize vulnerability check testing (e.g. Backtrack)
-   Document the security of IaaS. What is being done, not done, by who,
    when

    **Results**

    -   Draft on Security Document on IaaS done, but depending on the
        goal it might need to polished and published in wiki
    -   CSC has not committed to provide security monitoring but network
        router information was found to be an existing solution which
        was discussed. The progress was slow due many party
        communication and rule defining (what to monitor) for new kind
        of tool difficulties. The work continues in Q4/2014.

### 7. Security inside OpenStack project subnet

-   Network monitoring, detect anomalies with e.g. Bro
-   Make example solution
-   Automatize vulnerability check testing (e.g. Backtrack)
-   Document the security of FORGE. What is being done, not done, by
    who, when

    **Results**

    -   Not done because of the lack of resources

### 8. 2nd set of HW

-   2nd HW procurement ready
-   2nd HW installation ready
-   Big data readyness verified
-   E.g. application would be Hadoop cluster with swift as a storage
    engine

    **Results**

    -   Hardware was ordered in end of June, physically installed in
        August
    -   September host operating system installation and system
        configuration
    -   Release schedule was 3-4 weeks too optimistic
    -   Big data meeting with DIGILE (responsible) on PaaS layer

### 9. Generic big data example solution

-   Playbooks for DB engine
-   How to connect big data engine to object storage swift

    **Results**

    -   It was decided that the minimum viable solution was an
        installation of [CDH
        5.1](http://www.cloudera.com/content/cloudera/en/documentation/cdh5/latest/CDH5-Release-Notes/cdh5rn_new_in_513.html).
    -   A
        [playbook](https://git.forgeservicelab.fi/ansible/cdh5-hadoop/tree/master)
        exists to provision and deploy a 12+1 hadoop cluster.
    -   12+1 hadoop cluster includes 1 monitor, 2 namenodes and
        10 datanodes.
    -   Despite the supported versions definitions from Cloudera, the
        cluster has been tested to work on Ubuntu Trusty Tahr
        (14.04 LTS) by using the "precise" Cloudera repositories, and
        Debian Wheezy 7.6 (Cloudera states 7.1). Backend database
        postgresql 9.3 (Cloudera states 9.1).
    -   After research it became apparent that the original target of
        connecting hadoop to object storage (swift) was not relevant due
        to the ephemeral nature of operations. Hadoop processes external
        data and produces consumables, these may or may not be eligible
        for long term storage but that falls outside the scope of
        Hadoop's operations.

### 10. Evaluation and OpenStack upgrades as upstream proceeds

-   Upgrade and keep OpenStack uptodate as needed

    **Results**

    -   Operating system level updates.
    -   Icehouse migration work was extensively done. Update due by end
        of October.\

### 11. Off the shelf marketplace study

-   Drupal based
-   Contract automatisation capability
-   Payment support (credit cards, paypal) extendable
-   Skinnable
-   Workflows tailorable

    **Results**

    -   Technical comparison of 4 different webshop platforms was
        conducted and poc was done for the most suitable one,
        Drupal Commerce. It was concluded that technically it is fairly
        straightforward to take the functionality into use. Business
        case for taking it into use remains weak as so far there is no
        identified customer need.

### 12. Performance testing example solution

-   Study and select tool for perf tests so that tests can be
    automatized
-   Create test cases to measure Redmine, Drupal performance

    **Results**

    -   Performance testing tools were evaluated and Jmeter was selected
    -   Performance tests are in use. Results available at
        <https://ci.forgeservicelab.fi>
    -   Example solution for affiliates. Including:
        -   example test script in git
        -   Support projects wiki page

### 13. Computing resources reporting on project basis vs total available

-   How much capacity there is left after CRAs are shared

    **Results**

    -   Python scripts done based on nova command results. Discussion
        with (USERNAME) still to be needed.
    -   Available resources reporting was given when requested.

### 14. 1st complete version of JulkICT Lab is ready with domain specific service design

-   JulkICT Lab stuff

    **Results**

    -   3 workshops have been conducted for JulkICTLab by JAMK and high
        level concept is in finalization stage. Further work is waiting
        for results of JulkICTLab's audit and report by VTT and
        following decision about JulkICTLab's organizational positioning
        and source of funding.

### 15. Training solutions operational

-   Training modules
-   Operations

    **Results**

    -   Two training modules (OpenStack basisc and FORGE technicalities)
        are ready and available. Third module (OpenStack CLI
        is underway). Materials serve both as a self learning material
        and instructor led training
    -   A training was organized for VisualLabel project's technical
        contacts
    -   A training ordering and enrollment process was not yet defined
        but it's underway and coming in the beginning of next release

Summary
------------------------------------

-   Not everything targeted got done and 283 storypoints (109 issues)
    have to be moved to the next release. See leftovers in the
    attachment
    [leftovers\_inc\_2014-09.pdf](/files/leftovers_inc_2014-09.pdf)
-   The target setting was overly ambitious if compared to capacity that
    is available. Also, some high priority "surprise" tasks coming from
    out of the sprint planning causes reduced sprint capacity.
-   Lot of things got done and 420 storypoints (189 issues) were
    completed
-   Lot of operational improvements were made especially in the areas of
    deployment pipeline and automation in testing and monitoring
-   A new service development project VisualLabel was started and
    kickoff training was organized for the project
-   The amount of partners in Plaza got increased
-   OpenStack and other supporting services (Redmine, XMPP, CAS...) are
    operational
    -   Several surprise breaks occurred in OpenStack in the beginning
        of August i.e. the cloud middleware management interfaces were
        not available. 6.8. morning there was also VM network cut due
        network hardware issue.\
-   Support function is operational
-   Deployment to production experimentation project was kicked off and
    completed during summer. The results have been shared explicitly to
    JulkICTLab project manager. The results are available for other
    affiliates too.
-   Pilot projects are operational in FORGE.
-   Some business targets will need more work in the next
    release 2014-11. E.g. trainings, security monitoring, big data
    server usage and available CRA reporting.



Release 2014-11
====================================================

-   Content and burnup charts are available in Redmine
    (=release notes)
-   Duration 2014-10-03 - 2014-11-28
-   Previous release is [Release\_2014-09](#release-2014-09)
-   Next release is [Release\_2015-02](#release-2015-02)

Targets and results
------------------------------------------------------------

### R&D operational improvements

-   The automation of the contract signing process
    -   Turn the contract into machinereadable format, have it created
        by customers by using e.g. forms, have the workflow so that
        legal is able to accept it digitally and finally trigger
        automated account creation based on the machinereadable contact
        information in the contract.
-   All decided services available as playbook. Ability to easily
    reproduce FORGE installation. After the release it should be
    possible to experiment the recreation of FSL environment. That would
    need a decision.
-   Increase the FAP competence in the selected areas. E.g. Service
    Design customer support.

    **Results**

    -   The contract has been turned into machinereadable format (HTML),
        the signup process is digital but the contract signing process
        is still manual
    -   The design and proof of concept for the fully digital signup
        process was made
    -   The solution for digital signing was selected
    -   Not all services are deployed using playbooks and part of CI.
        E.g. Redmine, CAS, password change app.

### Improvements in FORGE WEB, Plaza and Dashboard (Drupal)

-   Bulletin board iteration 2 (enabling announcements and dialogue
    inside Forge)
-   Further development of dashboard (link to training target)
-   Contract renewal and ramp-down process including Partner (and
    Service developer) invoicing
-   Partner: allowing other than content editor (technical contact)
    access to Forge
-   UX improvements

    **Results**

    -   Target list was changed after sprint start. Budget used for
        performance improvement, Feed-functionality and first iteration
        of dashboard.
    -   Decided to develop generic listing -view that can be applied
        across FORGE website with Feed-page as pilot
    -   One iteration of dashboard done but was decided to not to
        proceed with it because of complex technical implementation.
        Next iteration has been waiting for next batch of design
        capacity which is available in December.
    -   Number of UX improvements was done, e.g.
	  - [\#3438](/issues/3438 "Password recovery: approved initial, self-created password as old one before allowing to set new. (Resolved)"),
	  - [\#3357](/issues/3357 "PRODUCT OFFERING compulsory data behind tabs (In Progress)"),
	  - [\#3522](/issues/3522 "Client side validation doesn't work with advagg module (Resolved)"),
	  - [\#3533](/issues/3533 "Product family node view (Resolved)"),
	  - [\#3398](/issues/3398 "Wizard: cost, paymentm attn changes (Resolved)"),
	  - [\#3359](/issues/3359 "PRODUCT LISTING fix (Resolved)"),
	  - [\#3358](/issues/3358 "PRODUCT OFFERING Error messages fixes (In Progress)").

### Service design support for projects

-   Definition of FORGE service design support components
-   Kick off the co-operation project with partner
    -   To create FORGE Service design framework
    -   Memorandum of understanding signed
    -   Project plan created
    -   Project management framework operational
    -   Project operational
-   Implementation and further development

    **Results**

    -   FORGE service design support components defined on high level
        and sourcing plan done
    -   MoU signed
    -   Project is operational

### Security in IaaS

-   Network monitoring: define and iterate the monitored rules
-   Finalise the the security review of IaaS. What is being done, not
    done, by who, when

    **Results**

    -   Network monitoring is in place using nfsen rules defined
    -   The IaaS security document and guidelines exists in wiki

### Security inside OpenStack project subnet

-   Study what should be monitored in the projecet in order to detect
    anomalies
-   Network monitoring, detect anomalies with e.g. Bro
-   Make example solution
-   Automatize vulnerability check testing (e.g. Backtrack)
-   Document the security of FORGE. What is being done, not done, by
    who, when

    **Results**

    -   Network intrusion detection was studied and proven not to be
        feasible since ip packages are not echoed to VMs inside subnet
        and access to that kind of functionality is not available for
        FORGE
    -   A document exists in wiki about how FORGE has been secured

### 2nd set of HW

-   Big data node in customer usage

    **Results**

    -   2nd set of hardware (big data optimized) was installed,
        configured and made accessible for affiliates as big data CRAs

### 3rd set of hardware procured

-   Define what to order together with DIGILE

    **Results**

    -   There was a management decision to defer 3rd set of hardware

### Generic big data example solution

-   Playbook exists for Affiliates to setup a Hadoop cluster (for
    DB engine). Ability to connect big data engine to object
    storage swift.

    **Results**

    -   A playbook to install Hadoop cluster exists and is available
        for affiliates. The playbook was tested with the new big data
        optimized hw.

### Performance testing example solution

-   Study and select tool for perf tests so that tests can be
    automatized and run prior to deployment in order to detect
    performance drops
-   Create test cases to measure Redmine, Drupal performance

    **Results**

    -   A performance testing solutions were studied and selected
    -   A performance testing was implemented and automated as part of
        FORGE deployment pipeline and Drupal is now continuously
        performance tested
    -   Instructions for affiliates are documented in wiki

### Evaluation and OpenStack upgrades as upstream proceeds

-   OpenStack kept up to date: Icehouse

    **Results**

    -   OpenStack version was successfully upgraded to Icehouse version
        of OpenStack as planned
    -   No major hickups were detected during upgrade and the network
        outage was only matter of minutes

### Training solutions operational

-   Define and propose training streams and methods as a matrix
    (instructor led, videos, slides)
-   Training packages (self learning material and instructor
    led trainings) available for: Technical contact, FORGE IaaS users,
    Service Design training, FORGE Reference model training for Service
    developers, Admin contact training, Partner training (technical vs.
    admin)
-   Identify trainer partner

    **Results**

    -   Training solution was defined and implemented
    -   Trainings are now available for affiliates as self learning
        packages and some are also available as instructor led trainings
    -   The training solution supports for adding more training modules
        anytime

### Portfolio management

-   Portfolio management process defined and enfoced?
-   A mechanism to followup and report the progress of service
    development projects in FORGE documented and enforced.
-   A customer feedback and analytics feedback process documented. E.g.
    frequent interviews or phoneinterviews according to the predefined
    list of questions.
-   A followup and reporting template documented. A template could be
    the list of defined questions to be filled for reporting purposes
    during interviews.
-   The template tested with at least two potential customer projects
-   The feedback from projects collected and analyzed. High
    level summary.

    **Results**

    -   Portfoliomgmt is operational

### Misc

-   1st complete version of JulkICT Lab is ready with domain specific
    service design
-   Computing resources reporting on project basis vs total available

    **Results**

    -   Computing resources online report is available but doesn't yet
        report volume usage
    -   Automated CRM data fetching from Insightly was implemented
    -   Docker study was made and results are available

Summary
------------------------------------

-   Not everything targeted got done and 151 storypoints (in 74 issues)
    have to be moved to the next release. See leftovers in the
    attachment
    [leftovers\_2014-11.pdf](/files/leftovers_2014-11.pdf)
-   The target setting was again too ambitious when compared to capacity
    that is available and high priority "surprise" tasks keep on coming
    from out of the sprint planning and that causes reduced
    sprint capacity.
-   Lot of things got done and 368 storypoints (in 129 issues) were
    completed
-   SAML capable FORGE identity provider (IdP) connected to FORGE LDAP
    is operational and an example Django application using it is
    available for affiliates
-   IaaS capacity was increased along with the new hardware
-   A bigdata optimized 2nd set of hardware is now available for service
    developers as big data CRAs
-   OpenStack was updated to Icehouse version and the upgrade went as
    planned
-   IaaS has been stable and there has not been server breaks
-   Bigdata example (Hadoop cluster) is available as Ansible playbook
-   Again operational improvements were made. The amount of automated
    test cases was increased. Performance testing solution was selected,
    implemented and automated.


Release 2015-02
====================================================

-   Content and burnup charts are available in Redmine
    (=release notes)
-   Duration 2014-12-01 - 2015-02-27
-   Previous release is [Release\_2014-11](#release-2014-11)
-   Next release is [Release\_2015-04](#release-2015-04)

Targets
------------------------------------

### R&D operational improvements

-   The automation of the contract signing process

    -   Turn the contract into machinereadable format, have it created
        by customers by using e.g. forms, have the workflow so that
        legal is able to accept it digitally and finally trigger
        automated account creation based on the machinereadable contact
        information in the contract.

    **Results**\
     - HTML template exists and contract PDF can be generated from it.
    Generated documents are reviewed\
     - Implementation is not complete yet. Changes to the workflow were
    initiated and those require implementation changes\
     - This topic is carried on by SBD team (Note! DIGILE
    organization change). Contact: Sanna

### Feedback from customers

-   Design and implement process for collecting feedback from
    customer projects.

    **Results**

    -   This topic is carried on by SBD team (Note! DIGILE
        organization change). The first round of interviews is being
        carried out in February-March 2015. The process is being
        developed later during spring 2015. Contact: Kata.

### Analytics and reporting

-   Online computing resources reporting on project basis vs allocated
    vs total available (volumes to be reported too)
-   Online and always up to date analysis of FORGE WEB usage statistics

    **Results**

    -   Online IaaS reports are provided by BIRT system (Business
        Intelligence Reporting Tool). Reports are based on the data
        available from OpenStack. Reports are available
        <http://analytics.forgeservicelab.fi:8080/birt-viewer/run?__report=forge_birt_reports/iaas.rptdesign&sample=my+parameter>
    -   Online FORGE WEB usage statistics are provided by Piwik system.
        Reports are based on the data that is populated to Piwik by
        end-users browsing to FORGE WEB pages. Reports are available at
        <https://analytics.forgeservicelab.fi/piwik/>
    -   Both systems are connected to FORGE continuous delivery pipeline
        and Ansible playbooks exists for deployments
    -   Both systems are accessible only from the selected networks
        (DIGILE, KE, CSC). Note! Accessing WEB usage statistics reports
        requires FORGE credentials
    -   FORGE internal documentation is at internal wiki
    -   Customer documentation for Piwik analytics is at external wiki

### Service design and reference model

-   Service design support for projects as it is specified is
    implemented and operational
-   Reference model facelift
-   Increase the FAP competence in the selected areas. E.g. Service
    Design customer support.

    **Results**

    -   The final version of the service design toolkit and templates
        were created. See
        [\#2482](/issues/2482 "Toolkit reviewing and refining (Closed)")
    -   The examples of service designs of digital services (Spotify,
        Airbnb, Dropbox). See
        [\#179](/issues/179 "Examples for FORGE affiliates (Closed)")
    -   JulkICT Labs visualized Service Concept has been reviewed by
        JulkICT Lab (Kirsi Pispa) and has been published in the JulkICT
        Lab wiki.
    -   Service design contract with JAMK ended
    -   The topic "service design support" topic is carried on by SBD
        team (Note! DIGILE organization change). Service design Coach
        offering is being developed together with Laurea during
        spring 2015. Contact: Jaakko.
    -   The topic Reference model's "concept development" phases Define,
        Learn, Explore are carried on by SBD team (Note! DIGILE
        organization change). When when the phases are ready enough, the
        overall review will be coordinated by SBD team. Contact: Eero.
    -   Reference model's "build" phases Build, Golive and Measure
        were reviewed. The phases were modified according to
        the feedback.

### Training modules

-   New training modules (self learning material and instructor
    led trainings) available for

    -   Service Design training
    -   FORGE Reference model training for Service developers
    -   Admin contact training
    -   Partner training
    -   Capability to Live WEBcast study. E.g. OpenMeeting or
        Google Hangouts.

    **Results**\
     - "Service Design training" is carried on by SBD team (Note! DIGILE
    organization change). Contact: Jaakko.\
     - "FORGE Reference model training for Service developers" is
    carried on by SBD team (Note! DIGILE organization change). Contact:
    Jaakko.\
     - "Partner training" is carried on by SBD team. (Note! DIGILE
    organization change) Contact: Jaakko.\
     - "Admin contact training" was not done because of the lack of
    resources and because authentication backend changes were
    prioritized.\
     - "Capability to Live WEBcast study. E.g. OpenMeeting or Google
    Hangouts." was not done because of the lack of resources and because
    new team member induction to more important operational things was
    prioritized as well as authentication backend changes were
    prioritized.\
     - Additional training module "Deployment pipeline training" was
    done and added to the training portfolio

### Improvements in FORGE WEB, Plaza and Dashboard (Drupal)

-   UX improvements
-   Consistent listing views across service
-   Finalization of dashboard user interfaces
-   Means to show other platforms in Plaza (Itewiki, API Suomi,
    JulkICTLab, Bluemix)

    **Results**

    -   Lot of changes and bug fixes. E.g. empty feeds view, front page
        general layout, service developer permissions in drupal,
        mobileview search bar, frontpage searchbar.
    -   This topic is carried on by SBD team (Note! DIGILE
        organization change). Contact: Kata.

### Security of OpenStack VMs

-   Study and proposal of host intrusion detection systems
-   Study and proposal of network intrusion detection systems
-   Example solutions as playbooks

    **Results**

    -   Network intrusion detection was studied already in the previous
        release and proven not to be feasible since ip packages are not
        echoed to VMs inside subnet and access to that kind of
        functionality is not available for FORGE
    -   Host intrusion detection system was not studied bacause of the
        lack of resources and authentication backend changes were
        prioritized
    -   The feasibility study of pursuing FORGE IaaS towards basic Vahti
        level 3 security level has started.\
    -   The feasibility of pursuing other FORGE services towards basic
        Vahti level 3 security level was made. The decision was that
        DIGILE won't pursue the auditing other FORGE service to a
        certain security level. See
        [\#3794](/issues/3794 "FORGE operations is not capable of the basic security level defined for Finnish officers (Closed)")
        for more information.

### 3rd set of hardware

-   3rd set of hardware procured

    **Results**

    -   FORGE Steering group decided to postpone the last procurement
        for the year 2015. The money was proposed to be moved from 2014
        to 2014 in the 1st additional finance budget. Budget results is
        expected by end of March. However, there is no plan yet when the
        procurement will be done. It has to be decided 3-4 months before
        aimed usage. Feedback for the hardware specifications is
        continuously welcome. CSC follows technology development
        continuously also in its other projects.

### OpenStack upgrades

-   Planned FORGE OpenStack upgrades to mainstream versions
-   Ceilometer
-   LbaaS
-   Docker driver (Future)
-   Heat (Pouta)
-   DNSaaS Designate (Juno)
-   IPv6 (Juno)

    **Results**

    -   Lots of effort has been put into operations.
        -   For example OpenStack cleaning feature caused I/O errors on
            the VMs. Luckily we were able to recover most of the images
            and fix the issue not to happen again. Did not
            affect (seriously) to affiliates.
        -   Bug fixes for Cinder and Nova have been created. Cinder
            suffered management API problems several times.
        -   A network incident (short breaks) in the central storage
            system in the beginning of February. Its root cause and
            effects remained mostly unclear. After consulting the vendor
            some firmware upgrades will be done in March.
        -   Some problems were fixed in e.g. "regular users should not
            be able to make public images" and "volumes stau in creating
            state"
        -   LDAP migration (auth.forgeservicelab.fi) including
            consulting DIGILE in LDAP
        -   Some server hardware maintenance (a disk and DIMM changed)
        -   Flavors issues (ID changed due some actions
            by administrators) causing error messages not to be able to
            show flavor information. Flavors were fixed and
            administration guide improved.
    -   Windows Server image and instructions to use it was enabled to
        Generisk project after licencing issues and liabilities were
        resolved
    -   CSC started to use (CSC internal) SCRUM in its cloud projects. A
        sprint is 1 month. This strenghtens communication, knowledge
        distribution and administration capacity inside CSC. The
        preparations for the next OpenStack versio has been on going
        since mid January and are expected to be finished by end
        of April. That included a major version change in the host
        operating system (CentOS 7).
    -   Preparation for the ISO27001 began. Time when the certification
        will be done is not known and thus cannot be
        communicated outside.
    -   A comment regarding the list: As was discussed when planning the
        this EPIC, some of the additional features requires CentOS 7 or
        Juno and some will be done first in cPouta. When there is a
        customer need, please let CSC know.

### Misc

-   1st complete version of JulkICT Lab is ready with domain specific
    service design
-   All decided services available as playbook. Ability to easily
    reproduce FORGE installation. After the release it should be
    possible to experiment the recreation of FSL environment. That would
    need a decision.

    **Results**

    -   JulkICT lab operating in FORGE continues
    -   JulkICT Labs visualized Service Concept has been reviewed by
        JulkICT Lab (Kirsi Pispa) and has been published in the JulkICT
        Lab wiki.
    -   All decided services are available as playbooks. Playbooks are
        used for easy and reproducible service deployment. Not all FORGE
        services are yet available as playbooks and the work continues
        in future releases.
    -   The work has started to improve the account creation
        (and removal) process and practicalities
    -   Lot of effort was put into the improvement of the identity
        management backend by implementing a new LDAP schema and by
        running it in the new auth2 machine and by migrating all FORGE
        services (Gitlab, OpenStack, Redmine, XMPP, Piwik,
        Drupal, Nagios) to that. This work also enables the data model
        where the service design project can be represented like they
        are in practice. E.g. earlier the assumption was that the
        project may have only one admin contact and technical contact.
        It has turned out that this is not the case but the projects may
        have multiple admin contacts from different organizations while
        still having one technical contact.
    -   The improvement was also made to manage CRM related contact
        information separately from the authentication and authrization.
        Former is being managed in Insightly CRM tool and latter is
        being managed in FORGE ldap. This change makes sure that no
        duplicate information has to be managed in two places and with
        two tools.
    -   The testing was improved and the load testing of selected FORGE
        services (Gitlab and Auth2) was added to the test asset. The
        load testing solution is also provided to service developers as
        an example and is documented in external wiki
	-   Test automation asset was increased
    -   Piwik analytics solution was upgraded, hardened and connected to
        FORGE identity backend.
    -   Playbooks were reviewed against the new Ansible version
        requirements and were refactored accordingly. Playbooks are now
        Ansible 1.8 compliant.
    -   POODLE vulnerabilities in certain services were fixed
    -   New SHA2 certificates were ordered and deployed to FORGE WEB
        services because old SHA1 certificates are getting
        potentially weak.

### Changes

-   FORGE team member Tomas Karasek decided to left DIGILE. We thank
    Tomas for the excellent contribution to FORGE and wish Tomas
    brilliant future in his new challenges.
-   A new FORGE team member Jukka Nousiainen joined DIGILE. We warmly
    welcome Jukka to the team and to his new new challenges in FORGE
    as devops.
-   DIGILE made a slight organization change in the beginning of 2015.
    The new SBD team managed by Jaakko Talvitie has following members:
    Erkinheimo Pia, Kalatie Katariina, Vainionpää Sanna, Lehtinen Risto,
    Rautsi Eero. SBD team will focus on service business development and
    carries on sales and marketing and service design development
    activities as well as continues the product ownership of public web
    page based on Drupal. FORGE platform team will carry on the defined
    technology activities as before.


Release 2015-04
====================================================

-   Content and burnup charts are available in Redmine
    (=release notes)
-   Release start date: 2015-03-02
-   Release end date: 2015-04-24
-   Previous release is [Release\_2015-02](#release-2015-02)
-   Next release is [Release\_2015-06](#release-2015-06)

Targets
------------------------------------

### R&D operational improvements

-   Complete the new authentication and authorization system by
    migrating all FORGE services to use auth2
-   Improve FORGE setup continuous delivery by preparing playbooks and
    by enabling Jenkins jobs in continuous integration machine for the
    selected FORGE services. Long term target is to have an ability to
    easily reproduce complete FORGE installation by using playbooks of
    each and every FORGE service and have them available for affiliates
    as examples.
    -   Piwik
    -   Password change app
-   Study and propose IaaS neutral provisioning solution for FORGE (e.g.
    Apache libcloud, Ansible...). It should be possible to use one
    single solution to provision set of instances in various IaaS
    environments: FORGE, Azure, AWS, Rackspace

    **Results**

    -   All services are migrated to use new auth (LDAP) and
        multitenancy in the project is now possible as well as support
        for multiple admin contacts per project
    -   Redmine and plugins can now be recreated from scratch by using
        the playbook
    -   Redmine and plugins are now connected to the CI pipeline
    -   A playbook for Analytics (BIRT and Piwik) is available but not
        yet fully tested nor connected to CI pipeline because of lack of
        time and other priorities
    -   The complete set of identity backend related playbooks are
        available and connected to CI pipeline
    -   IaaS neutral provisioning solution has not been investigated
        because of other priorities
    -   The management of services that are not managed by CI is now
        centralized to the admin node
    -   Gitlab was upgraded
    -   Lot of work was done in integrating the CRM tool with the
        authentication and authorization infrastructure and resources
        creation automation
    -   Load testing was improved with Plaza load testing
    -   Test automation asset was again increased

### Platform study

-   New platform initiative defined, proposed and decided by DIGILE mgmt
-   Use case for the selected platform initiative is defined
-   Study and demonstrate the selected platform initiative. Long term
    target is to have an example platform solution and wiki instructions
    available for affiliates use.

SELECTED

-   X-Road service usage trough Zato ESB to X-Road.

DEFERRED

-   FORGE replica on OrangeBox + RaspberryPi
-   PaaS stack for FORGE (e.g. OpenShift, CloudFoundry...)
-   Microservice Architecture for FORGE

    **Results**

-   KaPA was studied and it was demonstrated how FORGE's demo
    application can talk to KaPA test service

-   The use scenario of FORGE providing a "shared secure server" i.e.
    gateway to KaPA was studied and demonstrated and it turned out that
    the use scenario has not been completely accounted by KaPA

-   A playbook was developed to automate the installation and setting up
    a secure server connected to KaPA. The configuration of the secure
    server cannot be fully automated because of the design decisions
    made in KaPA code base. Therefore certain manual steps are needed to
    finalize the installation.

-   There are couple of risks related to using KaPA software. Potential
    legal problems in using KaPA software
    ([\#4680](/issues/4680 "KAPA: Potential legal problems in using X-Road components because licencing terms are not clear (New)"))
    and potential problems caused by KaPA sofware because source code is
    not available
    ([\#4679](/issues/4679 "Potential problems caused by X-Road components without ability to fix them because source code is... (New)"))

### Training modules

-   New training modules (self learning material and instructor
    led trainings) available
    -   Reference model training for Service developers
    -   Admin contact training
-   Capability to Live WEBcast study. E.g. OpenMeeting or Google
    Hangouts

    **Results**

    -   Admin contact training module was created
    -   Reference model training for Service developers was not created.
        This is driven by SBD team and the team is busy with more
        important priorities
    -   Capability to Live WEBcast was not studied because of other
        priorities took over

### Security of OpenStack VMs

-   Study, demonstrate and propose a host intrusion detection system for
    FORGE
-   Example solutions of HIDS available for affiliates use as playbooks
    and wiki instructions

**Results**

-   Not done because of other priorities took over

### IaaS

-   3rd set of hardware procured
-   Feasibility and plan for the security certification against defined
    VAHTI level. The long term target is to have an security audited
    IaaS available for affiliates use
-   Planned FORGE OpenStack upgrades to mainstream versions

    -   Juno (next OpenStack version)
    -   Ceilometer
    -   LbaaS
    -   Docker driver (Future)
    -   Heat (Pouta)
    -   DNSaaS Designate (Juno)
    -   IPv6 (Juno)

    **Results**\
     - IaaS was migrated to a new auth\
     - Maintaining the system (operations). Some hickups with the Volume
    management interface. No lost customer VMs or data.\
     - Preaudit for ISO 27001 preparation was done. The final audit to
    be done in autumn (date not fixed). Raised Vahti level was never
    aimed for FORGE.\
     - 3rd set of hardware procurement was (financing steering
    group 24.4.) decided still to be postponed until needed to avoid
    data center costs and getting hardware old without usage. Better
    models might be available and hardware might get cheaper. Budget was
    succesfully transfered actually to be available even to end of
    2016.\
     - Juno upgrade did not come in this Release although it
    was planned. There were unexpected difficulties including CentOS 7
    migration.\
     - Juno will be taken into CSC ePouta usage in May 2015 so at least
    there we will get experience and thus lower some risks. The FORGE
    specific issue is the migration of the current VMS to new OS
    virtualisation layer and Juno.

### Summary

-   Plenty of things got done and the velocity of the release was 198
    storypoints (of 200 planned)
-   [Leftover content](issues.pdf) was moved to release 2015-06 release
-   There were some changes in priorities along with the release that
    had an impact on planned activities
    -   CRA cost and price tag estimation was done
    -   Contributions to Drupal activities restructuring and
        reprioritization
    -   Heatmap solution was studied
    -   Many bugs were fixed
    -   Slight contributions to negotiating the new responsibilities
        after the organization change
-   There are risks involved in running the FORGE operations with
    reduced budget
-   There are risks involved in running Drupal and Plaza operations with
    reduced budget and because of the organization change impacts
-   The velocity of the next releases will be smaller than 200
    storypoints because of the budget reductions

------------------------------------------------------------------------

Release 2015-06
====================================================

-   Content and burnup charts are available in Redmine
    (=release notes)
-   Duration 2015-04-27 - 2014-06-26
-   Previous release is [Release\_2015-02](#release-2015-02)
-   Next release is [Release\_2015-08](#release-2015-08)

Targets
------------------------------------

### Generic data analysis pipeline as a service

-   Study and propose the technical implementation alternatives of the
    data analytics pipeline. ETL.
-   See the patterns from: <https://vimeo.com/79533035>,
    <http://johnmcox.blogspot.fi/2013/09/building-data-analysis-pipelines-with.html>,
    <https://cloud.google.com/solutions/real-time/kubernetes-redis-bigquery>

### KaPA platform study

-   Create live production gw for organizations to connect to KaPA
-   Create customer processes for common usage of FORGE's secure server.
    Agreements, Joining, Executing, Closing
-   Create customer documentation and internal operations documentation

### R&D operational improvements

-   FORGE reproducibility
    -   Experiment with creating a FORGE clone
    -   Identify the areas that need to be prepared for reproducability.
    -   Learn OpenStack deployment alternatives.

### Trainings

-   New training modules (self learning material and instructor
    led trainings) available
    -   Ansible training by using one of the selected FORGE playbooks as
        an example
-   Capability to Live WEBcast study. E.g. OpenMeeting or Google
    Hangouts

### Security of OpenStack VMs

-   Study, demonstrate and propose a host intrusion detection system for
    FORGE
-   Example solutions of HIDS available for affiliates use as playbooks
    and wiki instructions

### IaaS

-   3rd set of hardware procurement based on needs in Q3/2015 or 2016
    (but not in this Release)
-   Planned FORGE OpenStack upgrades to mainstream versions
    -   Juno (next OpenStack version)
    -   Ceilometer
    -   LbaaS
    -   Docker driver (Future)
    -   Heat (Pouta)
    -   DNSaaS Designate (Juno)
    -   IPv6 (Juno)


Release 2015-08
====================================================

-   Content and burnup charts are available in Redmine
    (=release notes)
-   Duration 2015-06-29 - 2014-08-28
-   Previous release is [Release\_2015-06](#release-2015-06)
-   Next release is [Release\_2015-10](#release-2015-10)

Targets
------------------------------------

### FORGE asset publishment preparations

-   Due diligence of FORGE assets
    -   Define the process for publishment of assets; docs and sw
    -   Define the checklist and get it accepted by legal. Checklist to
        consits of items e.g. remove secrets from all assets (names and
        IP addresses and so on), crosscheck of licences
-   Decide the place for publishment
-   Start the publishment activities based on the accepted process

### JulkICTLab handover to CSC

-   Create a common list of items together with CSC to be transferred
-   Plan and execute transfer activites

### Measuring the impact of FORGE Service Lab in Finnish society

-   Provide support for the team that is in charge of the measurement

