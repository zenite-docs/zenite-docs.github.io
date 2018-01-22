# Migrating to zenite

You can easily move your existing database to zenite. On your existing server, run the following command(s):

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

Login to zenite and upload the resulting archive file to Server -> Backups -> Upload. After the files is uploaded, click the restore icon to restore the database on the server.




