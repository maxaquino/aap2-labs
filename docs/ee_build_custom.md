## Build a new EE with the ServiceNow and Community collections in Ansible Automation Platform

Follow the below instructions to create a custom Execution Environment which contains ServiceNow and Community collections if not already available on the registry

(run the steps below on the ansible controller node)

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
  - name: community.general
COL

podman login registry.redhat.io

ansible-builder build -t ee_custom:0.0.1

podman image ls

podman image prune

podman tag localhost/ee_custom:0.0.1 quay.io/maquino/ee_custom:0.0.1

podman login quay.io

podman push quay.io/maquino/ee_custom:0.0.1
```

