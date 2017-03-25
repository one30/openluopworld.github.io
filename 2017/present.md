---
layout: default
---

# 轻量级分组密码PRESENT及实现介绍
2017.02.03

2017.03.22：增加PRESENT一些实现的链接

### 1. 数据变换
并行实现64个分组的加密。设64个分组分别为：
```C
uint64_t plain[64];
```
首先需要对数据的格式做处理，将64个分组相同位置的比特位统一放在一个uint64_t变量中。设变换后的输入数据为：
```C
uint64_t input[64];
```
则有，

input[0] = plain[63]<sub>0</sub>...plain[1]<sub>0</sub>plain[0]<sub>0</sub>

input[63] = plain[63]<sub>63</sub>...plain[1]<sub>63</sub>plain[0]<sub>63</sub>

其中，plain[63]<sub>0</sub>表示plain[63]的最低比特位，plain[0]<sub>63</sub>表示plain[0]的最高比特位，其它同理。

[64 blocks in parallel of PRESENT](https://github.com/pfasante/present)

[An 8-bit Implementation of the PRESENT block cipher in C](https://github.com/michaelkitson/Present-8bit)

[Some lightweight cryptography algorithms optimized for x86](https://github.com/rb-anssi/lightweight-crypto-lib)

Paper: High-throughput implementations of lightweight ciphers in the AVR ATtiny architecture
