# Scheduled backups

> (server) > Backups > Schedule

You can create a schedule that will backup your database automatically in regular intervals. The minimum backup interval is 1 hour.

1. Click Add new Schedule...
2. Configure the backup interval using Cron syntax. Learn about Cron syntax [here](https://en.wikipedia.org/wiki/Cron). The text below will show the Cron interval in a human readable format.
3. Select the database you want to backup periodically.
4. Click the "Save" button.
5. You will see the schedule appear in the "Schedules" grid. To edit or delete a schedule, click the corresponding icon in the grid.

On every configured interval, a backup will be triggered automatically.

The Scheduled backups grid below will show the last 50 backup archives that have been created. Click on any backup name to download the backup archive, or click the restore the icon in the grid to restore the backup directly onto the server.

> The backup operation may slow down your database. Configure your interval appropriately (during non-business hours, for example).

> Please note that the backups older than last 50 are automatically deleted. Configure your Cron interval appropriately to ensure your backup history is sufficient.

> Restoring a backup will overwrite the backed up databases on the server with databases contained within the backup. Restore with caution.