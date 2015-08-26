Access to FORGE services from the Internet
================================================================================================================================

This page describes a test scenario for basic access to FORGE services
from the Internet.

The services for FORGE affiliates should be accessible from the
Internet, as opposed to the administation interfaces and SSH where the
access should be restricted.

Exposure of service can be seen in the [Services table in the
Infrastructure Overview](2_Infrastructure.md#infrastructure-overview).

As we have several layer for IP access control, we should verify that
our services are available from outside of our VPN. following table
lists basic access test. Note: One big precondition for all these tests
is that it's done from outside of Digile VPN.

	  preconditions              task                                                                                outcome
	  -------------------------- ----------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------
	  not authenticated in CAS   access <http://support.forgeservicelab.fi>                                          redirected to <https://support.forgeservicelab.fi> and from there to <https://auth.forgeservicelab.fi>
	  authenticated in CAS       access <http://support.forgeservicelab.fi>                                          redirected to <https://support.forgeservicelab.fi>
	  ---                        access <http://git.forgeservicelab.fi>                                              redirected to <https://git.forgeservicelab.fi/users/sign_in>
	  not authenticated in CAS   access <http://auth.forgeservicelab.fi> or <https://auth.forgeservicelab.fi>        CASino login view
	  authenticated in CAS       access <http://auth.forgeservicelab.fi> or <https://auth.forgeservicelab.fi>        CASino sessions view
	  ---                        connect to xmpp.forgeservicelab.fi with a XMPP client with FORGE LDAP credentials   it works
	  ----                       access <http://support.forgeservicelab.fi/password>                                 forwarded to <https://support.forgeservicelab.fi/password>

	You can check if you are authenticated in CAS by visiting
	<https://auth.forgeservicelab.fi>.

TcE2E ws
===============================

	 Steps   Description
	 ------- ----------------------------------------------------------------------------------------------------------------------
	 1.  Affiliate sign/creates a contract
	 2.  Digile checks the contract and payment
	 3.  Digile initiates the affiliate creation procedure
	 4.   KE performs affiliate creation
	 5.  Affiliate receives an email with welcome message and instructions and forwards it to other testers
	 6.  Affiliate resets password according to instructions in his email
	 7.  Affiliate logs into gitlab, creates a project and commits something according to external wiki instructions
	 8.  Affiliate creates a support ticket to add a new user according to external wiki instructions
	 9.  KE performs a user creation
	 10. Affiliate logs into openstack and uploads and image and launches an instance according to external wiki instructions
	 11. Affiliate needs more resources to newly created VM (more CPU/mem/disk) and creates a new support ticket.

TcAffiliate
========================================

	 ------------------------------------------------------
	 No      Test Case name         Notes/Description
	 ------ ----------------------- -----------------------
	 1      Affiliate creates VM in  Using existing image
		 	 openstack               

	 2      Affiliate upload an     Upload image thourgh
		 	 server image to         Horizon
		 	 openstack               

	 3      Affiliate logs into     Affiliate is able to
		 	 XMPP server to get      login to support room
		 	 support                 

	 4       Affiliate generated     Generate SSH key based
		 	 SSH key and uses it     in wiki instruction and
		 							 use it for accessing VM

	 5       Affiliate start using  Create a git repo and
		 	 GIT                     upload data, pull data
		 							 from another machine

	 6      Affiliate creates a     
		 	 support ticket to add a 
		 	 new user according to   
		 	 external wiki           
		 	 instructions            

	 7      Affiliate needs more    
		 	 resources to newly      
		 	 created VM (more        
		 	 CPU/mem/disk) and       
		 	 creates a new support   
		 	 ticket.                 

	 8       Affiliate uses          A volume can be
		 	 persistent storage on   attached to a single
		 	 single instance         instance at a time.

	 9       Affiliate uses          It is possible to
		 	 persistent storage and  detach a Volume and
		 	 detach & attach to      attach it to another
		 	 another                 instance. The data
		 							 remains on the volume.

	 10      Affiliate uses         You can have multiple
		 	 mulitple persistent     volumes.
		 	 storages                

	 11     Affiliate deletes       You can delete the
		 	 persistent storage      unnecessary Volumes
	 ------------------------------------------------------

TestRun1
===============================

admin:<USERNAME@DOMAIN>
tech:<USERNAME@DOMAIN>

	 -----------------------------------------------------------------
	 Steps Description    Status         Responsible    Other
	 ----- -------------- -------------- -------------- --------------
	 1.    Affiliate      Done           Jari           Contract
		  	Create                                       signing part
		  	contract                                     scanned &
		  												 emailed to
		  												 <forge-contrac
		  												 ts@digile.fi>

	 2.    Digile receive Done           Jari           
		  	email and send                               
		  	"workinprogess                               
		  	"                                            
		  	message to                                   
		  	Affiliate                                    

	 3.    Digile review  Done           Jari           Essi&Jari will
		  	contract &                                   go through the
		  	create acc                                   contract &
		  	request                                      create a
		  												 ticket for
		  												 account
		  												 creation
		  												 [\#559](/issue
		  												 s/559 "Describ
		  												 e step by step
		  												  process for C
		  												 ontract review
		  												  phase (Reject
		  												 ed)")
		  												 [\#563](/issue
		  												 s/563 "Contrac
		  												 t template sho
		  												 uld have the s
		  												 ame info as in
		  												  wiki for defa
		  												 ult quota (Clo
		  												 sed)")
		  												 [\#564](/issue
		  												 s/564 "Admin (
		  												 affliate) acco
		  												 unt should be 
		  												 informed when 
		  												  techincal acc
		  												 ount creation 
		  												 is done  (Clos
		  												 ed)")

	 4.    KE receive acc Done           Ilkka          
		  	request &                                    
		  	implement acc                                

	 5.    Digile receive Done           Tomas          Email was
		  	acc msg                                      mistyped in
		  												 first place.
		  												 So needed to
		  												 update email
		  												 manually &
		  												 resend the
		  												 ticket to
		  												 Affiliate
		  												 [Changing\_use
		  												 rs\_data](#Cha
		  												 nging_users_da
		  												 ta)

	 6.    Affiliate      Done           Tomas          Email template
		  	receive                                      modified so
		  	Welcome msg                                  that username
		  												 & project name
		  												 are in
		  												 separate lines

	 7.    Affiliate      Done           Tomas          Acdc123456\#
		  	create pwd                                   

	 8.    Use OpenStack  Done           Jorge/Tomas    Use turnkey WP
		  	& create WP                                  image in Demo
		  	instanse                                     

	 9.    Public user    Done           Anyone         WP Working
		  	browse to IP                                 
		  	where WP is                                  
		  	located                                      
	 -----------------------------------------------------------------

TestRun 2
=================================

	--------------------------------------------------------------
	Steps Description         Status            Responsible
	----- ------------------ ------------------ ------------------
	1.    Affiliate                             Previous run
		  sign/creates a                        
		  contract                              

	2.    Digile checks the                     Previous run
		  contract and                          
		  payment                               

	3.    Digile initiates                      Previous run
		  the affiliate                         
		  creation procedure                    

	4.    KE performs                           Previous run
		  affiliate creation                    

	5.    Affiliate receives                    Previous run
		  an email with                         
		  welcome message                       
		  and instructions                      
		  and forwards it to                    
		  other testers                         

	6.    Affiliate resets                      Previous run
		  password according                    
		  to instructions in                    
		  his email                             

	7.    Affiliate logs     Done               Antti
		  into gitlab,                          
		  creates a project                     
		  and commits                           
		  something                             
		  according to                          
		  external wiki                         
		  instructions                          

	8.    Affiliate creates  Done               Pasi
		  a support ticket                      
		  to add a new user                     
		  according to                          
		  external wiki                         
		  instructions                          

	9.    KE performs a user Done               Tomas
		  creation                              

	10.   Affiliate logs     Done               Jorge
		  into openstack,                       
		  uploads an image                      
		  and launches an                       
		  instance according                    
		  to external wiki                      
		  instructions                          

	11.   Affiliate needs    Skipped            Process must be
		  more resources to                     documented to wiki
		  newly created VM                      [\#565](/issues/56
		  (more                                 5 "Define the proc
		  CPU/mem/disk) and                     ess for affiliate 
		  creates a new                         to ask for more re
		  support ticket.                       sources/quota (Clo
		 										 sed)")

	12.   Newly created      Done               Tomas
		  Affiliate logs                        
		  into XMPP support                     
		  room for techincal                    
		  discussion                            

	13.   Newly created      Done               Tomas
		  Affiliate logs                        
		  into OpenStack and                    
		  browse available                      
		  servers&networks                      

	14.   Newly created      Done               Pasi
		  Affiliate clones                      
		  git repo created                      
		  in step 7 and                         
		  makes a commit                        
	--------------------------------------------------------------


TestRunSprint20140124
======================================================================

	No   Test Case name                                                     Notes/Description                                                                                       Excecution status
	---- ------------------------------------------------------------------ ------------------------------------------------------------------------------------------------------ --------------------
	8    Affiliate uses persistent storage on single instance               A volume can be attached to a single instance at a time.                                               PASSED
	9    Affiliate uses persistent storage and detach & attach to another   It is possible to detach a Volume and attach it to another instance. The data remains on the volume.   PASSED
	10   Affiliate uses mulitple persistent storages                        You can have multiple volumes.                                                                         PASSED
	11   Affiliate deletes persistent storage                               You can delete the unnecessary Volumes                                                                 PASSED
