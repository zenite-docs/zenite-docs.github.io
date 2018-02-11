# Migrating to zenite

You can easily move your existing database to zenite. The process involves creating a backup archive, uploading it through zenite web portal and executing the restore process. On your existing server, run the following command(s):

##### MariaDB / MySQL
```bash
mysqldump --single-transaction --flush-logs --master-data=2 --databases your-database-name | gzip > database.sql.gz
```

##### PostgreSQL
```bash
pg_dump --dbname your-database-name --username your-username --password your-password --serializable-deferrable --format c --compress 9 > database.dmp
```

##### MongoDB
```bash
mongodump --db your-database-name --username your-username --password your-password --authenticationDatabase admin --archive --gzip --quiet > database.gz
```

After the archive has been created, you can upload it to zenite from the upload backups tab. Read more on how to upload the backups in the [Upload backups](backup/upload.md) section.