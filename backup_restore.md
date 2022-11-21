
# Backup Restoration Instruction

#### Become a **root**:
```
sudo -i
```

#### Become a **backup** user:
```
sudo -i
su - backup
```

## MySQL backup restoration

#### As a backup user download the MySQL backup:
```
duplicity --no-encryption restore rsync://VladyslavaSh@backup.vlada.vld//home/VladyslavaSh/mysql /home/backup/restore/mysql
```

#### As a root user restore the MySQL backup:
```
mysql agama < /home/backup/restore/mysql/agama.sql
```

## InfluxDB backup restoration

#### As a backup user download the InfluxDB backup:
```
duplicity --no-encryption restore rsync://VladyslavaSh@backup.vlada.vld//home/VladyslavaSh/influxdb /home/backup/restore/influxdb
```

#### As a root user restore the InfluxDB backup:
```
service telegraf stop
influx -execute 'DROP DATABASE telegraf'
influxd restore -portable -database telegraf /home/backup/restore/influxdb
```
#### Since the telegaf was stopped, you need to start it. This can be done in two ways, so choose the one that suits you.
##### Start manually as a root user:
```
service telegraf start
```
##### Run ansible playbook:
```
ansible-playbook infra.yaml
```
