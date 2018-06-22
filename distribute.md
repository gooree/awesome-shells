# 文件分发

```bash
#!/bin/bash

SRC_DIR=/opt/soft
DEST_DIR=/opt/soft

for line in `cat servers.txt`
do
  host=${line%%:*}
  port=${line##*:}

  echo "scp -P $port -r $SRC_DIR root@${host}:${DEST_DIR}/"
  scp -P $port -r $SRC_DIR root@${host}:${DEST_DIR}/
done
```
