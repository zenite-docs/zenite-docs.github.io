# Server configuration

zenite servers are configured with sane defaults to accomodate the performance requirements of most users.

If required, any advanced configuration changes will have to be done by our support team. This includes changes to database server configuration files, changes to server configuration etc. If you require such changes, please contact us at support@zenite.io.

## Service user

Each database server includes a service user which zenite uses to access the databases when executing queries and database backups. This user is accessible only on localhost, and is protected with a randomly generated password for each server. This user has the following username:

```
_zenite_root_do_not_modify_or_delete
```

As the name indicates **do not modify** this user. This includes changing the service user's password, permissions etc. Doing so will cause zenite to fail to access your databases, which means you won't be able to execute queries or backup databases through zenite portal. If you accidentally changed this user's configuration, please contact us at support@zenite.io.

## Server specification

zenite makes an effort to use the recent Linux kernel version on all database servers. Currently running Linux kernel version:

```
4.15.12-x86_64
```

The servers are configured with minimal services required to run the database to keep the performance optimal.