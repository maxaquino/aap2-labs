## Build a new EE with a collection for ServiceNow in Ansible Automation Platform

Follow the below instructions to create a custom Execution Environment for ServiceNow

```
cd; mkdir builder; cd builder

cat<<EE > execution-environment.yml
version: 1
dependencies:
  galaxy: requirements.yml
  python: requirements.txt
  system: bindep.txt
EE

touch requirements.txt
touch bindep.txt

cat<<COL > requirements.yml
---
collections:
  - name: servicenow.itsm
COL

podman login [registry.redhat.io]

ansible-builder build -t ee_snow:0.0.1

podman image ls

podman prune

podman tag localhost/ee_snow:0.0.1 quay.io/maquino/ee_snow:0.0.1

podman login quay.io

podman push quay.io/maquino/ee_snow:0.0.1
```


