---
layout: default
---

文件系统基本知识

In Unix and related computer operating systems, a [file descriptor] (FD, less frequently fildes) is an abstract indicator (handle) used to access a file or other input/output resource, such as a pipe or network socket. (from wiki)

The [inode] is a data structure in a Unix-style file system that describes a filesystem object such as a file or a directory. Each inode stores the attributes and disk block location(s) of the object''s data. Filesystem object attributes may include metadata (times of last change,[2] access, modification), as well as owner and permission data. (from wiki)

![file descriptor and inode](./../images/fd_inode.png?raw=true)

# f2fs

### 文件系统布局

### inode信息

下面的代码给出了f2fs文件系统inode在磁盘中的数据（需要注意和虚拟文件系统中数据的区别，虚拟文件系统中的数据比实际存储的数据要丰富），代码来自linux-4.13。

```C
#define F2FS_NAME_LEN            255
#define F2FS_INLINE_XATTR_ADDRS  50
#define DEF_ADDRS_PER_INODE      923
#define DEF_NIDS_PER_INODE       5

struct f2fs_inode {
  __le16 i_mode;                      /* file mode */
  __u8 i_advise;                      /* file hints */
  __u8 i_inline;                      /* file inline flags */
  __le32 i_uid;                       /* user ID */
  __le32 i_gid;                       /* group ID */
  __le32 i_links;                     /* links count */
  __le64 i_size;                      /* file size in bytes */
  __le64 i_blocks;                    /* file size in blocks */
  __le64 i_atime;                     /* access time */
  __le64 i_ctime;                     /* change time */
  __le64 i_mtime;                     /* modification time */
  __le32 i_atime_nsec;                /* access time in nano scale */
  __le32 i_ctime_nsec;                /* change time in nano scale */
  __le32 i_mtime_nsec;                /* modification time in nano scale */
  __le32 i_generation;                /* file version (for NFS) */
  __le32 i_current_depth;             /* only for directory depth */
  __le32 i_xattr_nid;                 /* nid to save xattr */
  __le32 i_flags;                     /* file attributes */
  __le32 i_pino;                      /* parent inode number */
  __le32 i_namelen;                   /* file name length */
  __u8 i_name[F2FS_NAME_LEN];         /* file name for SPOR */
  __u8 i_dir_level;                   /* dentry_level for large dir */
  struct f2fs_extent i_ext;           /* caching a largest extent */
  __le32 i_addr[DEF_ADDRS_PER_INODE]; /* Pointers to data blocks */
  __le32 i_nid[DEF_NIDS_PER_INODE];   /* direct(2), indirect(2),
                                      double_indirect(1) node id */
} __packed;
```

> 目录是一种特殊的文件，因此文中inode有时直接用文件表示，请根据上下文理解。

+ i_mode: inode的类型，包括文件，目录，软链接（同时也是一个文件），字符设备，块设备等
+ i_inline: 扩展属性是否包括在inode内部（若是，inode中将会有200字节用于存储扩展属性，否则全部用于存储地址）
+ i_uid: inode所属的用户id
+ i_gid: inode所属的组id
+ i_links: 硬链接的数目，硬链接和源文件共享同一个inode，本质上硬链接和源文件没有任何区别。当删除一个文件时：
  * 若该文件不存在硬链接，则会删除文件（从父目录的目录项中删除），同时删除inode；
  * 若该文件存在硬链接，则会删除文件（从父目录的目录项中删除），同时将i_links减1（但不删除inode）。
+ i_size: inode数据的大小，对于文件值文件内容，对于目录指目录项的大小
+ i_atime, i_ctime, i_mtime, i_atime_nsec, i_ctime_nsec, i_mtime_nsec
  * 访问，修改文件属性，修改文件内容的时间
+ i_xattr_nid
+ i_pino: 父目录的inode编号
+ i_namelen: 文件名的长度	
+ iname: 文件名的最大长度，255字节
+ i_dir_level: 目录层次
+ i_addr[923]: 文件内容的指针（即文件内容所在inode的编号）
  * 
  * 
  * 
+ i_nid[5]:

References

[What does opening a file actually do](https://stackoverflow.com/questions/33495283/what-does-opening-a-file-actually-do)

[inode]:<https://en.wikipedia.org/wiki/Inode>
[file descriptor]:<https://en.wikipedia.org/wiki/File_descriptor>

