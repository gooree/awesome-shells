# nginx动态黑名单

```bash
#!/bin/bash

LOG_DIR=/var/log/nginx
MAX_ACCESS_LIMIT=10000
BLACK_LIST=black.txt

logfile=`find $LOG_DIR -type f -size +0 -name "access.log*" | xargs ls -lt | head -n 1 | awk '{print $9}'`

cat $logfile | awk '{print $1,$7,$9}' | grep -i -v "baidu|360|sougou|soso" | awk '{print $1}' | sort | uniq -c | sort -rn | awk -v access_limit=$MAX_ACCESS_LIMIT '{if($1>access_limit)print "deny: "$2";"}' > $BLACK_LIST
```