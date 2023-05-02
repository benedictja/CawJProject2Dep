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

Author: Eric Lacroix