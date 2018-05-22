# Database credentials

## Administrator credentials

> (server) > Information

You can view the server admin credentials for establishing a connection to the database with any compatible client in the Server Information tab.

```
Username: root
Password: XXXXXXXXXX
```

When you initially deploy a server, the password will be generated automatically. It is recommended that you change the default password.

## Changing the administrator account password

### MariaDB

```sql
SET PASSWORD FOR 'root'@'%' = PASSWORD('new_password');
```

### PostgreSQL

```sql
ALTER USER root WITH PASSWORD 'new_password';
```

### MongoDB

```javascript
db.changeUserPassword('root', 'new_password');
```