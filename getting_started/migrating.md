# Migrating to zenite

# MariaDB / MySQL

You can easily move your existing MariaDB / MySQL database to zenite. On your existing server, run the following command:

```
mysqldump --single-transaction --flush-logs --master-data=2 --databases your-database-name | gzip > database.sql.gz
```

Login to zentie and upload the resulting sql.gz file to Server -> Backups -> Upload. After the files is uploaded, click the restore icon to restore the database to the server.

# PostgreSQL

# MongoDB
