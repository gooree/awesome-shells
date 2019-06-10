# 查找nginx访问量最大的N个ip

```bash
#################################
## Finding top N nginx visitors
#################################
#!/bin/bash

#default nginx log dir
LOG_DIR=/var/log/nginx

#find top 10 by default,you can change it in the command line. eg: topN.sh 5
topN=10
if [ $# -gt 0 ];then
  topN=$1
fi

#############################
#find out latest logfile
#############################
#date=`date +%Y%m%d`
#logfile=$LOG_DIR/access.log-$date
#
#if [ ! -e $logfile ]; then
#  date=`date -d "1 day ago" +"%Y%m%d"`
#  logfile=$LOG_DIR/access.log-$date
#fi

logfile=`find $LOG_DIR -type f -size +0 -name "access.log*" | xargs ls -lt | head -n 1 | awk '{print $9}'`
if [ $# -gt 1 ]; then
  logfile=$2
fi

echo -e "client_ip   access_times"
cat $logfile | awk '{print $1,substr($4,14,21),$7,$9}' | grep -i -v "baidu|360|sougou" | awk '{print $1}' | sort | uniq -c | sort -rn | head -n $topN | awk '{print $2,$1}'
```