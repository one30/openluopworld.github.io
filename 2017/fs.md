---
layout: default
---

文件系统基本知识

In Unix and related computer operating systems, a [file descriptor] (FD, less frequently fildes) is an abstract indicator (handle) used to access a file or other input/output resource, such as a pipe or network socket. (from wiki)

The [inode] is a data structure in a Unix-style file system that describes a filesystem object such as a file or a directory. Each inode stores the attributes and disk block location(s) of the object''s data. Filesystem object attributes may include metadata (times of last change,[2] access, modification), as well as owner and permission data. (from wiki)

![file descriptor and inode](./../images/fd_inode.png?raw=true)

References

[What does opening a file actually do](https://stackoverflow.com/questions/33495283/what-does-opening-a-file-actually-do)

[inode]:<https://en.wikipedia.org/wiki/Inode>
[file descriptor]:<https://en.wikipedia.org/wiki/File_descriptor>

