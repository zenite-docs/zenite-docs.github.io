# Manual backups

> (server) > Backups > Manual

You can manually trigger the backup of any non-system database immediately.

1. Choose the database you want to backup from the drop-down.
2. Click the `Trigger backup now` button.
3. After the backup has been completed, the backup archive will appear in the `Manual backups` grid.

The maximum number of manual backup archives zenite can hold at once is 10.

The backup operation may slow down your database. Trigger the backup action in the appropriate time (during non-business hours, for example).

Click on any backup name to download the backup archive, or click the restore the icon in the grid to restore the backup directly onto the server.

Restoring a backup will overwrite the databases on the server with databases contained within the backup. Restore with caution.