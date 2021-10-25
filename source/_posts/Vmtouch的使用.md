---
title: Vmtouch的使用
date: 2021-10-25 17:26:56
categories: Tool
---
**vmtouch**主要作用是做数据的warmup，即对于将要用到的数据，通过**vmtouch**把它们事先读入内存，而不是在需要时再从硬盘上读入，这样可以提高系统效率。注意功能如下：

- 查看一个文件（或者目录）哪些部分在内存中；

- 把文件调入内存；

- 把文件清除出内存；

- 把文件锁住在内存中而不被换出到磁盘上；



## 安装

```text
git clone https://github.com/hoytech/vmtouch
cd vmtouch
make
sudo make install
```

## 示例

- 查看目录有多少文件在缓存中

```text
[root@host-192-168-1-57 data]# vmtouch nodes/
           Files: 1097
     Directories: 140
  Resident Pages: 781596/824164  2G/3G  94.8%
         Elapsed: 0.35741 seconds

```

- 查看一个文件有多少数据在缓存中

```text
[root@host-192-168-1-57 index]# vmtouch -v _13_Lucene84_0.tim 
_13_Lucene84_0.tim
[ O] 1/2

           Files: 1
     Directories: 0
  Resident Pages: 1/2  4K/8K  50%
         Elapsed: 0.000186 seconds


```

## 参考文档

[GitHub - hoytech/vmtouch: Portable file system cache diagnostics and control](https://github.com/hoytech/vmtouch)

[Hoytech](https://hoytech.com/vmtouch/)


