# datax脚本

```bash
#!/bin/bash
#################
# datax script
# 
# @author guorui
#################
print_help() {
  cat <<EOF
Commands:
  init <reader-name> <writer-name>
  run <job-file>
EOF
}

if [ $# -lt 1 ]; then
  echo "Usage: $0 <command> [options]"
  print_help
fi

case "$1" in
run)

  if [ $# -lt 2 ]; then
    echo "Usage: $0 run <job-file>"
  else

    echo "start job"
    python $DATAX_HOME/bin/datax.py $2
  fi
;;
init)

  if [ $# -lt 3 ]; then
    echo "Usage: $0 init <reader-name> <writer-name>"
  else

    echo "init datax config file"
    python $DATAX_HOME/bin/datax.py -r $2 -w $3
  fi
;;
*)
  print_help
;;
esac
exit
```
