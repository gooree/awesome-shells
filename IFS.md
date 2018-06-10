# 利用IFS读取CSV文件

```bash
data="name,age,gender,location"
oldIFS=$IFS
IFS=","

for item in $data;
do
  echo Item: $item
done

IFS=$oldIFS
```
