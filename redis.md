# Redis脚本

```bash
#!/bin/bash
#####################
# redis shell script
#####################

# help function
help() {
  cat <<EOF
Usage: redis start | stop | status
EOF
}

if [ $# -lt 1 ];then
  help
  exit
fi

case "$1" in
start)

  redis-server /etc/redis/redis.conf
;;
stop)

  redis-cli shutdown
;;
status)
 
  cmd=`netstat -natp|grep 6379|wc -l`
  if [ $cmd -gt 0 ];then
    echo "redis server is running!"
  else
    echo "redis server is stopped!"
  fi
;;
*)
  help
;;
esac
```