Installation
============

Requirements
------------

Before anything, you need the following software installed on your machine:

  * [Ansible](http://docs.ansible.com/intro_installation.html),
  * [Virtualbox](https://www.virtualbox.org/wiki/Linux_Downloads),
  * [Vagrant](https://www.vagrantup.com/downloads.html),
  * [Capifony](http://capifony.org/)
  * ...

Secrets
-------

Stored in [myproject-secrets.kdbx](myproject-secrets.kdbx) (Keepass 2.x)

Master password owners:
 * Dev 1 (dev1@theodo.fr)
 * Architect 1 (architect1@theodo.fr)
 * Hosting Guy (hosting.guy@operator.com)

How to get SSH/VPN access
---------------------
To get secured shell access to the different environments, you have to:
  - Send an email to give.me.ssh@access.com with your SSH key
  - Add your ssh key into the `path/to/file` file of the project's provisioning
  - Reprovision the servers through the OpenStack interface

To get access to the VPN, you have to contact John OPERATOR (john.operator@access.com),
so that he can send you personal credentials.


Project installation
--------------------
To install the project, you must at first clone both the code repository and the provisioning repository:
```
    git clone git@github.com:theodo/project.git
    git clone git@github.com:ops/provisioning-project.git
```

Then, this project can be installed by running the install script:
```
    cd project/
    ./install.sh
```


Application initialisation
--------------------------

Once you have everything required, you must:

  * Clone the repository: `git clone git@github.com:theodo/project.git && cd project`
  * Download composer: `curl -sS https://getcomposer.org/installer | php`
  * Install vendor libraries: `composer install --prefer-dist`
  * Run your virtual machine: `vagrant up --provision`
  * Connect through SSH to the virtual machine: `vagrant ssh`
  * Grant read, write permissions for cache and logs for each environment:
```
cd /var/www/project/current
chown -R www-data.www-data ../current
chmod 777 app/cache app/logs
```
  * Install Capifony: `gem install capifony`
  * Build your database schema: `app/console doctrine:migrations:migrate`

Your application is almost installed!


Hosts configuration
-------------------

For more convenience, setup local hosts on your **host machine**

```
sudo /bin/bash -c 'echo "192.192.192.192  project.dev" >> /etc/hosts'
sudo /bin/bash -c 'echo "193.193.193.193  project.preprod" >> /etc/hosts'
sudo /bin/bash -c 'echo "194.194.194.194  project.prod" >> /etc/hosts'
```

Now you should be able to access the application in your Web browser:
  * Use http://project.dev/ for local environment (need virtual machine to be up)
  * Use http://project.preprod/ for preproduction environment
  * Use http://project.prod/ for production environment

On your **virtual machine**, you should set up hosts for VPN servers:
```
sudo /bin/bash -c 'echo "193.193.193.193  project.preprod" >> /etc/hosts'
sudo /bin/bash -c 'echo "194.194.194.194  project.prod" >> /etc/hosts'
```

SSH configuration
-----------------

From your **host machine**, generate and add (if needed) an SSH key pair:
```
ssh-keygen -f ~/.ssh/rsa_project
ssh-add ~/.ssh/rsa_project
```

Then copy-paste the following SSH configuration, by replacing %SSH_KEY% by the path of your SSH key:
```
Host project-preprod
Hostname project.preprod
user www-data
IdentityFile %SSH_KEY%

Host project-prod
Hostname project.prod
user www-data
IdentityFile %SSH_KEY%
```


Database initialisation
-----------------------

The last thing to do to make the project work locally: you must generate a database filled with entities.
For this purpose, see the [database documentation](data.md).
