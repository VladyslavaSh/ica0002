
# Backup Restoration Instruction

#### Become a **root**:
`sudo -i`

#### Become a **backup** user:
```
sudo -i
su - backup
```

## MySQL backup restoration

#### As a backup user ownload the MySQL backup:
`duplicity --no-encryption restore rsync://VladyslavaSh@backup.vlada.vld//home/VladyslavaSh/mysql /home/backup/restore/mysql`


#### As a root user restore the MySQL backup:
`mysql agama < /home/backup/restore/agama.sql`


## InfluxDB backup restoration

#### As a backup user download the InfluxDB backup:
`duplicity --no-encryption restore rsync://VladyslavaSh@backup.vlada.vld//home/VladyslavaSh/influxdb /home/backup/restore/influxdb`

#### As a root user restore the InfluxDB backup:
```
service telegraf stop
influx -execute 'DROP DATABASE telegraf'
influxd restore -portable /home/backup/restore/influxdb
```
