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

After the archive has been created, do the following actions:

1. Click the "your-server-name.zenite.io" the.
2. Click the "Backups" tab.
3. Click the "Upload" tab.
2. Click "Choose Files..." button and select an archive that you just created on your server.
3. Click the "Upload" button.
4. After the file has been uploaded, click the restore icon in the grid to restore the database onto the server.
