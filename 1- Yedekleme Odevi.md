```
#!/bin/bash
for user in $(ls /home)
do
        tar -zcvpf /mnt/${user}_$(date +%d%m%Y_%H%M).tar.gz /home/${user}
        md5sum /mnt/${user}_$(date +%d%m%Y_%H%M).tar.gz  | cut -d ' ' -f1  > /mnt/${user}_$(date +%d%m%Y_%H%M).tar.gz.md5.txt
        echo $(date +%d%m%Y_%H%M) >> /tmp/son-calisma.log
done
```

```
#-- Crontab --
#
# 05 23 * * * /home/hakangunes/yedekleme.sh
```

