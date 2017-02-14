---
layout: post
title: SAT solver for sbox implementation
date: 2016.10.11
discription: SAT solver for sbox implementation
---

### 1. SAT solver for sbox implementation

### 1.1 SAT solver
SAT求解模型如下：对于n个GF(2)上的变量，给定m个限制条件，每个限制条件给出其中任意多个变量的限制（取0或者取1）,求是否存在满足所有限制条件的解。相关介绍可以参考[这里]。

使用SAT求解sbox指令序列的方法可以参考[paper]，具体介绍参考[sboxoptimization]，如下是一个简单的例子：

```sh
$ ./getanf.py gc rectangle 11 > rectangle_gc11.eqs
C:\\Sun\\SDK\\bin\\java -Xms256M -Xmx1200M -cp C:\\cygwin\\sat ANFtoCNF arg1 arg2
# where arg1 will be ignored
# and arg2 should be the input filename
$ nohup minisat rectangle_gc11.eqs.cnf > rectangle_gc11.eqs.cnf.claim &
# 目前minisat求解的格式与cnfclaimtoclaim.py定义的不同，使用cnfclaimtoclaim.py解析时会提示有错
$ ./cnfclaimtoclaim.py rectangle_gc11.eqs.cnf.claim > rectangle_gc11.eqs.claim.txt
$ ./getsolution.py rectangle_gc11.eqs > rectangle_gc11.solution
```

需要依赖的工具有：
* JDK，ANFtoCNF的java程序：用于将ANF的格式转化为CNF格式
* 下载安装[minisat]求解器，[MiniSat在线求解]可以解决一些规模较小的问题，但规模较大时无法解决。

[这里]:<http://sahandsaba.com/understanding-sat-by-implementing-a-simple-sat-solver-in-python.html>
[paper]:<https://ko.stoffelen.nl/papers/fse2016-sboxoptimization.pdf>
[sboxoptimization]:<https://github.com/Ko-/sboxoptimization>
[minisat]:<https://github.com/niklasso/minisat>
[MiniSat在线求解]:<https://www.msoos.org/2013/09/minisat-in-your-browser/>
