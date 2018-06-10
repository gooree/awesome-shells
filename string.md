# Shell字符串操作
---

1. length
```bash
  expr length "$string"
  echo ${#string}
  echo "$string":".*"
```

2. substr
```bash
  echo ${string:2}           # 从第二个位置开始提取字符串
  echo ${string:2:3}         # 从第二个位置开始提取3个字符
  echo ${string:(-6):5}      # 从倒数第二个位置向左提取字符串
  echo ${string:(-4):3}      # 从倒数第二个位置向左提取6个字符
  expr substr "$string" beginIndex endIndex
```
3. indexOf
```bash
  expr index "$string" '123'    //结果4 字符串对应的下标是从0开始的
```
4. lastIndexOf

5. trim
```bash
  echo $string|sed 's/^\s*//;s/\s*$//' > trim.txt
  string=`cat trim.txt`
```
6. charAt
```bash
  echo ${string:N:1}	# N为数字下标
```
7. replace
```bash
  ${string/pattern/replacement}
```
8. replaceAll
```bash
  ${string//pattern/replacement}
```
9. toLowerCase
```bash
  ${string,,}
```
10. toUpperCase
```bash
  ${string^^}
```
11. concat
```bash
  ${str1}${str2}
```
12. replacePrefix
```bash
  ${string/#prefix/replacement}
```
13. replaceSuffix
```bash
  ${string/%suffix/replacement}
```
