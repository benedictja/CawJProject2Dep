# CawJProject2Dep
This is the initial test of git.

File Structure Template
inventories/
   production/
      hosts               # inventory file for production servers
      group_vars/
         group1.yml       # here we assign variables to particular groups
         group2.yml
      host_vars/
         hostname1.yml    # here we assign variables to particular systems
         hostname2.yml

   staging/
      hosts               # inventory file for staging environment
      group_vars/
         group1.yml       # here we assign variables to particular groups
         group2.yml
      host_vars/
         stagehost1.yml   # here we assign variables to particular systems
         stagehost2.yml

library/
module_utils/
filter_plugins/

site.yml
webservers.yml
dbservers.yml

roles/
    common/
    webtier/
    monitoring/
    fooapp/

#!/bin/bash
mkdir library
mkdire module_utils
mkdir module_utils
mkdir filter_plugins
touch site.yml
touch webservers.yml
touch dbservers.yml
mkdir -p roles/common
mkdir -p roles/monitoring  

Session 3 - Project restructuring & Code Migration

Objective
1) Move existing inventories and variables into new structure
2) Write a simple play to verify it works
3) Test GIT
4) Start migrating complex plays

Decisions
- Pre-Prod First
   My existing ESX hosts will become my pre-prod environment.
   Once that is done and working, we will create a "prod" env elsewhere, some options
      a) Cloud
      b) OpenShift
      c) Another set of esx hosts
- Play Strucuture - keep zoned concept
   Build one playbook for each zone deployment and hook them in to the main playbook via includes

Starting Point
- all servers have had the ansiblead (password ******) installed, ssh key deployed and added to wheel just like we typically get from the O/S teams

1) Move existing inventories and variables to new structure - done
2) Write a simple play to verify it works - done

Session 3b (recap)

Objective
1) Move existing inventories and variables into new structure
2) Write a simple play to verify it works
3) Test GIT
4) Start migrating complex plays

Decisions
- Pre-Prod First
   My existing ESX hosts will become my pre-prod environment.
   Once that is done and working, we will create a "prod" env elsewhere, some options
      a) Cloud
      b) OpenShift
      c) Another set of esx hosts
- Play Strucuture - keep zoned concept
   Build one playbook for each zone deployment and hook them in to the main playbook via includes

Starting Point
- all servers have had the ansiblead (password ******) installed, ssh key deployed and added to wheel just like we typically get from the O/S teams

1) Move existing inventories and variables into new structure
- done again

2) Write a simple play to verify it works
- 
3) Test GIT
4) Start migrating complex plays

benedictja - "developer" - vs code
check-in to GIT
ansiblead - "operations" -
check-out from GIT 
execute it against the environment

Session 4 - The "migration"

Description

Now that we've got the new structure setup and working with git, its time to start migrating the deployment plays.

Decisions

Based on the previous decisions, I will be breaking my plays by "tier" and creating roles for each individual task.

Objectives
1) Create main (site.yml) to launch total update - done
2) It will be mostly a skeleton, importing each tier -done
3) Write "roles" for each task 
4) I will break rols down in to common and tier specific

- I have created a motd role as a sample/test to verify roles
- next step will be to create the patch (dnf) role and test it

Urls that I used for reference

https://docs.ansible.com/ansible/2.8/user_guide/playbooks_best_practices.html - this is an older link, the latest is
https://docs.ansible.com/ansible/2.9/user_guide/playbooks_best_practices.html

https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html - reference for roles

Next Session
- operational roles
1) LACMS check 
   . check admin rights or perms
   . do it right now
1.1) cleanup
2) Start/Stop/Restart individual/tier/system
3) Push password changes and certificates


Meeting Notes

Session 5 - Lets get Operational (2023-05-23)

Description

Work on starting/stoping/restarting components, and entire system

Decisions

- operations directory to keep separate from depoyment/config tasks (might move it to own project)

Objectives

- start/stop apache

Meeting Notes


Session 5, Friday Afternoon

Recap

completed initial deployment, started on ops tasks
created start/stop for tomcat

Today
- fixed tomcat war deployment
- show ansible deployment war 
- plan for apache start/stop
- restart
- start all


Session 6, Tuesday Morning

Description

Last session we started working on the operational tasks.  We created playbooks to start/stop tomcat and apache as individual tasks.  We attempted to create a stop-all playbook, but ran into some obstacles. This is where we will pickup today.

Objectives

1) Debug the stop-all playbook and get it working.
2) Write a start-all playbook
3) Plan a restart playbook

If we get all of this finished, then we can look at refactoring OR move on to our next operational task.

Decisions

1) For this version, we will focus on individual playbooks to get our start/stop tasks working BUT will revisit/refactor this once we've gained some experience.
2) Try to reuse existing code where possible, including refactoring if necessary

Notes


