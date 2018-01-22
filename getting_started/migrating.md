# Migrating to zenite

You can easily move your existing database to zenite. The process involves creating a backup archive, uploading it through zenite web portal and executing the restore process. On your existing server, run the following command(s):

### MariaDB / MySQL
```
mysqldump --single-transaction --flush-logs --master-data=2 --databases your-database-name | gzip > database.sql.gz
```

### PostgreSQL
```
pg_dump --dbname your-database-name --username your-username --password your-password --serializable-deferrable --format c --compress 9 > database.dmp
```

### MongoDB
```
mongodump --db your-database-name --username your-username --password your-password --authenticationDatabase admin --archive --gzip --quiet > database.gz
```

After the archive has been created, login to zenite and upload the resulting archive file to server.zenite.io -> Backups -> Upload. After the files has uploaded, click the restore icon to restore the database onto the server.
