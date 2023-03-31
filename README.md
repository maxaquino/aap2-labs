aap2-labs
=========

Ansible Automation Platform 2.x playbooks to be used for ansible smart management demo.

Run ** aap2-setup ** first to create credentials, projects, inventories and job templates.

Export all variable before running the playbook

```
export CONTROLLER_HOST=<ansible controller host>
export CONTROLLER_USERNAME=<ansible controller username>
export CONTROLLER_PASSWORD=<ansible controller password>
export CONTROLLER_TOKEN=<ansible controller token>
export SNOW_HOST=<ServiceNow hostname>
export SNOW_PASSWORD=<ServiceNow password>
export SNOW_USERNAME=<ServiceNow username>
```

** Note **
If the password contains special chars (such as $), use the following to export the variable:
```
export SNOW_PASSWORD=$( echo ‘<the password goes here>’)

example:
export SNOW_PASSWORD=$( echo ‘blabla$L$13’)
```

** Note **
To allow ServiceNow automation, it needs to create a custom execution environment which contains the required collection.
Istructions can be found [here](https://github.com/maxaquino/aap2-labs/blob/main/docs/ee_build_for_snow.md)

Below the content of the directories:

## ansible-servicenow
This folder contains playbooks to open changes and incidents on ServiceNow.
It requires:
- A working ServiceNow demo instance
- An execution environment on Ansible Automation Platform which includes the servicenow collection 

## dummy-lb
Just a test playbook which run on localhost

## patching
Some playbook to work with for patching a Linux server and installing httpd

