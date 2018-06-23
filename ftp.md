# FTP上传下载

1. 文件上传

```bash
#!/bin/bash

ftp -v -n ${HOST} <<EOF
  user $USER $PWD
  cd $REMOTE_DIR
  lcd $LOCAL_DIR
  prompt off
  mput *.txt
  close
  bye
EOF
```

2. 文件下载

```bash
#!/bin/bash

ftp -v -n ${HOST} <<EOF
  user $USER $PWD
  cd $REMOTE_DIR
  lcd $LOCAL_DIR
  prompt off
  mget *.txt
  close
  bye
EOF
```

