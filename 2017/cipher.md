---
layout: default
---

# 密码
2017.05.11

## 杂凑函数
* [SHA2]
  + SHA256: 摘要长度为256比特
  + SHA512: 摘要长度为512比特
  + SHA2算法中一些常数的选择是通过素数平方根的小数部分得到的，突然想到QQ号码生成的随机性

## 流密码
* [salsa20]

## 密码套件
* HMAC-SHA512
* AES256-GCM
* ChaCha20-Poly1305
* ChaCha20-Poly1305-IETF
* XChaCha20-Poly1305-IETF
* Key exchange: X25519
* Signle-part Signature: Ed25519
* Multi-part Signature: Ed25519ph
* Short message hash: SipHash-2-4

[SHA2]:<https://en.wikipedia.org/wiki/SHA-2>
[salsa20]:<https://en.wikipedia.org/wiki/Salsa20>
