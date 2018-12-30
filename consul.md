# Consul脚本

```bash
#!/bin/bash
#####################
# consul shell script
#####################

help() {
  cat <<EOF!
Usage: consul start | stop | status
EOF!
}

if [ $# -lt 1 ];then
  help
  exit
fi

case "$1" in
start)

  nohup /usr/local/bin/consul agent -dev &
;;
status)
  
  cmd=`netstat -natp|grep 8500|wc -l`
  if [ $cmd -gt 0 ];then
    echo "consul is running!"
  else
    echo "consul is stopped!"
  fi
;;
stop)
  
  pid=`ps -ef|grep consul|grep -v grep|awk '{ print $2 }'`
  kill -9 $pid
;;
*)
  help
;;
esac
```
