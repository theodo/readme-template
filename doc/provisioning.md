Provisioning
============

Provision local virtual machine
-------------------------------
Use the following command on your **host machine**:
```
vagrant provision
```

Provision pre-production server
-------------------------------
Use the following command on your **host machine**:
```
ansible-playbook \
--connection=ssh \
--inventory-file=provisioning/ansible/inventories/hosts \
--limit=staging  \
 provisioning/ansible/playbook.yml -vvvv
```

Provision production server
---------------------------
Use the following command on your **host machine**:
```
ansible-playbook \
--connection=ssh \
--inventory-file=provisioning/ansible/inventories/hosts \
--limit=master \
provisioning/ansible/playbook.yml -vvvv
```
