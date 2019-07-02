# Scan Port
注：本shell使用了nc命令测试服务器端口，请确保本地已安装了相应的程序包。

 ```bash
#!/bin/bash
 
if [ $# -lt 1 ]; then
    echo "Usage: ./scan.sh <hostip> [<port>]"
else
    ping=`ping -c 1 $1`
 
    string=${ping#*received, }
    string=${string% packet loss*}
 
    if [ $string = '0%' ];then
        echo $1 is alive.
        if [ $# -eq 2 ]; then
          nc -nvv -z $1 $2 >/dev/null 2>&1
          if [ $? -gt 0 ]; then
             echo "$2 port is closed."
          else
             echo "$2 port is open."
          fi
        fi
    elif [ $string = '100%' ];then
        echo $1 is dead.
    else
        echo The network sucks!
    fi
fi
```
