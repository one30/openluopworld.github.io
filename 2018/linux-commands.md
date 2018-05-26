---
layout: default
---

## Linux Commands
2018.05.26

+ find -inum <inodenum>
  * 通过i_ino查找文件信息
+ find . -path ./misc -prune -o -name '*.txt' -print
+ find . -type d \( -path dir1 -o -path dir2 -o -path dir3 \) -prune -o -print
  * [-path dir -prune -o排除指定目录查找](https://stackoverflow.com/questions/4210042/how-to-exclude-a-directory-in-find-command)
+ grep -v 'not-included-word'
  * 排除指定内容的行
