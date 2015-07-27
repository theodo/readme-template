Environments
============

The following environments are available for this project:

**Prod** : http://prod.project.com/index
  - ***IP*** : 192.192.192.192
  - ***Associated Git branch*** : master

**Preprod** : http://preprod.project.com/index
  - ***IP*** : 193.193.193.193
  - ***Associated Git branch*** : master

**Staging** : http://staging.project.com/index
  - ***IP*** : 193.193.193.194
  - ***Associated Git branch*** : staging

Deploy to pre-production
------------------------

Use the following commands on your **virtual machine**:
```
cap preproduction deploy
```

Deploy to production
--------------------

Use the following commands on your **virtual machine**:
```
cap production deploy
```

Execute a database modification command on a remote server
----------------------------------------------------------

See the documentation about [database commands](data.md).
