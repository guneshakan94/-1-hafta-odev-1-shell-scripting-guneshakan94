```
#!/bin/bash
THRESHOLD=90
EMAIL=hgnes92@gmail.com

df -h | grep -v Use | awk '{ print  $1, " " $5 }' | cut -d'%' -f1 | \
while read line
do
Dname=$( echo $line | awk '{ print  $1 }')

USE=$( echo $line | awk '{ print  $2 }')

if [ $USE -gt $THRESHOLD ]; then
  echo "The partition "$Dname" reached: %$USE"
  echo "The partition "$Dname" reached: %$USE" | mail -s "Disk Usage Rate " -r hgnes92@gmail.com $EMAIL
fi
done
```

```
#--Crontab--
#
# * * * * * /home/hakangunes/diskusage.sh
```
