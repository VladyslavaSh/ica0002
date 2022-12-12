## Backup coverage

- Agama MySQL database backup
- InfluxDB database backup


## RPO (Recovery point objective)

RPO is the acceptable amount of data that can be lost in the event of a failure. 

### MySQL: 
Full backups are done daily at 23:10 UTC and incremental backups are done at 23:10 UTC on every day-of-week from Monday through Saturday.

### InfluxDB: 
Full backups are done daily at 22:10 UTC and incremental backups are done at 22:10 UTC on every day-of-week from Monday through Saturday.


## Versioning and retention
Versioning and retention describe how many backup versions are stored and for how long.

Backup versions are stored 24 hours before they are replaced with a new backups.

## Usability checks
Usability checks describe how is backup usability verified.

The whole backup system is automated, therefore it can be considered usable.
To verify the backup usability try to restore the backup by following the restoration rules in the backup_restore.md file.

## Restoration criteria
The backup can be restored in cases such as server failure, data loss, need to return to the original server.
If you want to restore the backup, please follow the restoration rules in the backup_restore.md file.

## RTO (Recovery time objective):

RTO is the time required to restore the system to an operational state after a failure.
RTO is up to 4 hours which means that you will need up to 4 hours to bring databases back up again.

