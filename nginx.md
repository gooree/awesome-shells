# Nginx脚本

```bash
#!/bin/bash
########################
# nginx shell script
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

  systemctl start nginx.service
;;
stop)

  systemctl stop nginx.service
;;
restart)
 
  systemctl restart nginx.service
;;
status)
  
  systemctl status nginx.service
;;
*)
  help
;;
esac
```
