---
layout: default
---

## Passcode
2018.07.03

术语说明：
* 业务密钥DEK（Data Encryption Key）：具体加密数据的密钥
* 中间密钥KEK（Key Encryption Key）：用于包含DEK（或KEK）的密钥
* 根密钥HUK（Hardware Unique Key）：硬件唯一密钥

如何根据passcode产生一个秘钥，用于秘钥的加密？

1. HUK的硬件加密引擎在一次passcode的计算中不会被调用很多次，加密一次和加密两次的安全级别相同（加密多次涉及多次通信）。最后在经过一次HUK的加密，一方面将加密后的密文作为KEK；另一方面，经过派生（如hash）后保存，用于校验passcode的合法性。

KDF算法不可逆，用到了hash算法。

>> Such use may be expressed as DK=KDF(Key, Salt, Iterations) where DK is the derived key,
>> KDF is the key derivation function, Key is the original key or password, Salt is a
>> random number which acts as cryptographic salt, and Iterations refers to the number of
>> iterations of a sub-function. The derived key is used instead of the original key or
>> password as the key to the system. The values of the salt and the number of iterations
>> (if it is not fixed) are stored with the hashed password or sent as plaintext with an
>> encrypted message.
