Name of the project
===================

Description of the project, the main features of the application, and the value for the client.


Documentation index
-------------------

  * [Installation](doc/installation.md)
  * [Project model](doc/model.md)
  * [Database](doc/data.md)
  * [Provisioning](doc/provisioning.md)
  * [Git Workflow](doc/git-workflow.md)
  * [Deployment](doc/deploy.md)

Team members
------------

Sales representative:
- **Commercial** (commercial@theodo.fr)

Developer team:
  - **Dev 1** (dev1@theodo.fr)
  - **Dev 2** (dev2@theodo.fr)
  - **Dev 3** (dev3@theodo.fr)

Scrum Master:
  - **Scrum Master** (scrum.master@theodo.fr)

Product Owner:
  - **Product Owner** (product.owner@acme.com)

If you want to know which developers commited to the project and when are their last commits, use this helper in your project (Linux):
```bash
git log --format="%aN" | perl -ne 'print unless $seen{$_}++' | xargs -i -d '\n' git log -1 --author={} --format="%aN (last commit %cd)" --date=short | cat
```
