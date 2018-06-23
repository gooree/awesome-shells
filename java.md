# 执行java代码

1. 目录结构如下

```
|--src
   |--main
      |--java（class文件目录）
      |--resources（配置文件目录）
|--libs（依赖jar包目录）
```

2. shell脚本

```bash
#!/bin/bash

export JAVA_HOME=/usr/java/jdk1.x.xx

CLASSPATH=./src/main/java:./src/main/resources
MAIN_CLASS=com.awesomeshell.Helloworld

for f in `ls ./libs/*.jar`;do CLASSPATH=$CLASSPATH:./libs/$f;done

$JAVA_HOME/bin/java -classpath $CLASSPATH $MAIN_CLASS
```
