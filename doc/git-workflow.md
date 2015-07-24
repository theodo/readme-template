Git Workflow
=============

Branches description
--------------------

The **master** branch corresponds to the **production** environment where the final project is.
The **staging** branch corresponds to the **pre-production** environment where tests are done.
Other branches are **development** branches. Each development branch should match a **feature**, and match the following
pattern: **feature/XXX-name-of-the-feature**.


How to use Git on the project
-----------------------------

- Create a new branch **feature/XXX-name-of-the-feature** from **master**
- Commit your modifications on it
- Merge your custom branch on **staging**
- Deploy on the **staging** environment
- Upon validation, merge **feature/XXX-name-of-the-feature** onto **master**
- Deploy on the **preprod** environment
- Run tests and check everything is good
- Deploy on the **prod** environment

**NOTE**: Do not merge **staging** on **master** otherwise you will merge not validated features and deploy them on
the **prod** environment!

Congratulations! Your feature is now published on the production environment.
