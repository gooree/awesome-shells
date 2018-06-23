# shell多线程

```bash
#!/bin/bash

MAX_THREAD_NUM=10

start_time=`date +%s`
# make fifo file
[ -e /tmp/fd1 ] || mkfifo /tmp/fd1
exec 9<>/tmp/fd1
rm -rf /tmp/fd1

# write signals
for ((i=1; i<=$MAX_THREAD_NUM; i++))
do
  echo >&9
done

for ((i=1; i<=100; i++))
do
{
  read -u 9
  {
    sleep 1
	echo "[$i]:done"
	
	echo >&9
  }&
}
done

wait

stop_time=`date +%s`
echo "TIME:`expr $stop_time - $start_time`"
exec 9<&-
exec 9>&-
```
