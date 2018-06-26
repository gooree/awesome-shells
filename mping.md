# 服务器是否联网

```bash
#!/bin/bash

RETRY=3
isConnect=0
hostname=`hostname`

for ((i=1;i<=RETRY;i++));
do
  echo "ping www.baidu.com: $i times"

  ping -c 1 -w 3 www.baidu.com &> /dev/null

  if [[ $? != 0 ]]; then
    echo 'can not connect'
    sleep 3
  else
    isConnect=1
    break
  fi
done

if [ $isConnect -eq 1 ]; then
  echo "$hostname is online"
else
  echo "$hostname is offline"
fi
```
