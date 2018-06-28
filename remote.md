# 远程执行shell命令

```bash
#!/bin/bash

for line in `cat servers.txt`
do
    host=${line%%:*}
    port=${line##*:}
    
    ssh -p $port ${host} "/usr/sbin/adsl-stop;sleep 3;/usr/sbin/adsl-start" &> /dev/null
done
```
