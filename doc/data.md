Deal with data
==============

First step
----------

This project uses DoctrineMigrationsBundle, so, first, you must build your database schema:
`app/console doctrine:migrations:migrate`

Available commands
------------------

There are several commands you can use in order to fill your database the way you want:

  * List users (`app/console users:list`)
    - Returns a list of all users

  * Populate users (`app/console users:populate`)
    - Initialises database with a set of predefined users.

  * Create user (`app/console users:create [login] [password]`)
    - Creates a single user, with given login and password.


Local users
-----------
This project uses a login form, and you need to login to access some particular pages on the application.

You can either use on the following users already provided in the database:

| ***User role***    | ***Login***    | ***Password***    |
|:------------------:|:--------------:|:-----------------:|
| **Superadmin**     | superadmin     | superadmin        |
| **Admin**          | admin          | admin             |
| **User**           | user           | user              |


... or generate yourself a user by using the following command:
```
    app/console users:create [login] [password]
```

Execute data commands on remote environments
--------------------------------------------

If you have to execute a data loading command on preproduction or production, you can do this easily through Capifony.
On your **virtual machine**, use custom Capifony tasks:

  * List users => `cap (preproduction|production) users:list`
  * Populate users => `cap (preproduction|production) users:populate`
