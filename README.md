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
<<<<<<< HEAD
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

1) Move existing inventories and variables to new structure
=======
mkdir -p roles/monitoring

Author: Eric Lacroix
>>>>>>> 09909563f3a7893d2f161249b754be8bce1f4a54
