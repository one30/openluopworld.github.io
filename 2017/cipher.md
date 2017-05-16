---
layout: default
---

# 密码
2017.05.11

## 分组密码

## 流密码
* [salsa20]

## 密码杂凑函数
* [SHA2]
  + SHA256: 摘要长度为256比特
  + SHA512: 摘要长度为512比特
  + SHA2算法中一些常数的选择是通过素数平方根的小数部分得到的，突然想到QQ号码生成的随机性

## 消息认证码
* [Poly1305], [rfc7539]

## 认证加密

## 公钥密码算法

## 密码套件

密码套件通常包括：协议名称，秘钥交换算算法，身份认证算法，加密算法，加密模式，密码杂凑函数。常见的密码算法套件包括但不限于：

* TLS_RSA_WITH_AES_128_CBC_SHA
* TLS_RSA_WITH_AES_128_CBC_SHA256
* TLS_ECDH_ECDSA_WITH_RC4_128_SHA
* TLS_ECDH_ECDSA_WITH_AES_256_CBC_SHA
* TLS_DHE_RSA_WITH_AES_128_GCM_SHA256
* TLS_DH_RSA_WITH_AES_128_GCM_SHA256
* TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
* TLS_ECDHE_PSK_WITH_AES_128_CBC_SHA

[SHA2]:<https://en.wikipedia.org/wiki/SHA-2>
[salsa20]:<https://en.wikipedia.org/wiki/Salsa20>
[Poly1305]:<https://en.wikipedia.org/wiki/Poly1305>
[rfc7539]:<https://tools.ietf.org/html/rfc7539>
