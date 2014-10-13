Name of the project
===================

Team members
------------

Developer team:
  - **Dev 1** (dev1@theodo.fr)
  - **Dev 2** (dev2@theodo.fr)
  - **Dev 3** (dev3@theodo.fr)

Scrum Master:
  - **Scrum Master** (scrum.master@theodo.fr)

Product Owner:
  - **Product Owner** (product.owner@acme.com)
 
Project dates : from **01 Jan 2013** to **15 Aug 2014** 

Project environments
--------------------
The following environments are available for this project:

**Prod** : http://prod.project.com/index
  - ***IP*** : 192.192.192.192
  - ***Associated Git branch*** : master
  - ***HTTP login*** : http_login / http_password
  - ***User login*** : username / password
  - ***Admin login*** : admin / adminpwd

**Preprod** : http://preprod.project.com/index
  - ***IP*** : 193.193.193.193
  - ***Associated Git branch*** : staging
  - ***HTTP login*** : http_login / http_password
  - ***User login*** : username / password
  - ***Admin login*** : admin / adminpwd

How to get SSH access
---------------------
To get secured shell access to the different environments, you have to:
  - Send an email to give.me.ssh@access.com with your SSH key
  - Add you ssh key into the `puppet/hieradata/common.yml` file of the project's Puppetmaster
  - Reprovision the servers through the OpenStack interface

How to deploy
-------------
First, the git workflow for deployment is the following:
  - Create a new branch from **master**
  - Commit your modifications on it
  - Merge your custom branch on **staging**
  - Deploy on the **preprod** environment
  - Upon validation, merge **staging** onto **master**
  - Deploy on the **prod** environment

To deploy onto a particular environment, use the following command:
```
    cap [environment] deploy
```
##### More details in the [documentation for deploy].

Project installation
--------------------
To install the project, you must at first clone both the code repository and the provisioning repository:
```
    git clone git@github.com:theodo/project.git
    git clone git@github.com:synalabs/puppetmaster-project.git
```

Then, this project can be installed by running the install script:
```
    cd project/
    ./install.sh
```
### /!\ Desperate message of your dear APP team: Please, do your best to compile all the installation process in a single script. There's no pleasure at all in waiting for one command to end before typing the other, and a good project should have a simple way to be installed. ;-) /!\

Local users
----------
This project uses a login form, and you need to login to access some particular pages on the application.

You can either use on the following users already provided in the database:

| ***User type***    | ***Login***    | ***Password***    |
|:------------------:|:--------------:|:-----------------:|
| **Superadmin**     | superadmin     | superadmin        |
| **Admin**          | admin          | admin             |
| **User**           | user           | user              |


... or generate yourself a user by using the following command:
```
    create-user [username] [password]
```

[documentation for deploy]: app/Resources/doc/deploy.md
