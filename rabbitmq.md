# RabbitMQ脚本

```bash
#!/bin/bash
########################
# rabbit shell script
########################

help() {
  cat <<EOF
Usage: rabbit start | stop | restart | status
EOF
}

if [ $# -lt 1 ];then
  help
  exit
fi

case "$1" in
start)

  service rabbitmq-server start
;;
stop)

  service rabbitmq-server stop
;;
restart)
 
  service rabbitmq-server stop
  service rabbitmq-server start 
;;
status)
  
  service rabbitmq-server status
;;
*)
  help
;;
esac
```
