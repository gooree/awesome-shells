# 文件分发

1. mscp.sh

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

2. servers.txt

```
61.153.48.18:20052
61.153.48.18:20272
61.153.48.18:20402
61.153.48.18:20462
61.153.48.18:20492
```
