---
layout: default
---

# OpenPGP
2016.08.20

### 1. 密码简介

#### 1.1 密码算法分类
* 对称密码算法(Symmetric key algorithm)
  + 也称为私钥密码算法(Private key cryptography)，但这种叫法不常见。
  + 对称密码只有一个密钥，加密解密都使用同样的密钥。

* 非对称密码算法(Asymmetric key algorithm)
  + 也称为公钥密码算法(Public key cryptography)
  + 非对称密码包括私钥和公钥两部分，其中公钥是公开部分，私钥由用户自己保存。其中公钥和私钥都可以用来加密，由公钥／私钥加密的密文只能通过私钥／公钥解密。非对称密码体制最早由Whitfield Diffie和Martin Hellman在1976年提出，但当时只从理论上提出了非对称的思想，并没有找到一个实际的系统。直到1977年MIT的三位科学家基于大素数分解的难题提出RSA，才正式开始有实际的算法。(一说RSA最早是由英国的数学家Clifford Cocks在1973年发明的，只是由于保密性要求直到1997年才公开。)

<table align="center">
<tr>
<td><img alt="Whitfield Diffie" src="https://upload.wikimedia.org/wikipedia/commons/1/19/Whit_Diffie_at_CFP_2007.jpg" width="250" height="275"></td>
<td><img alt="Martin Hellman" src="https://upload.wikimedia.org/wikipedia/commons/d/d4/Martin-Hellman.jpg" width="235" height="275"></td>
</tr>
<tr><td>Whitfield Diffie</td><td>Martin Hellman</td></tr>
</table>

* 密码杂凑函数(Hash function)
  + 也称为Hash函数，散列函数等。
  + 是一种单向函数，将一个不定长的二进制串映射成一个定长的二进制串。密码杂凑函数主要用于消息认证。
* 比较
  + 对称密码通信双方需要通过安全信道共享密钥。对于一个n用户组成系统，当n的值非常大时，密钥的管理就变得非常复杂，每个用户都需要保存n-1份密钥。非对称密码很好的解决了对称密码中密钥分发的难题，由于公钥可以公开，用户只需要保存自身私钥即可。非对称密码另外一个非常重要的应用是数字签名——使用私钥对数据进行加密时。
  + 对称密码的加密速度比非对称密码要快很多，实际系统的应用中都结合使用，取各自的优势。

#### 1.2 常见密码算法
* 对称密码
  + 分组密码：关于是否“轻量”，有些算法可能存在不同的说法。
    - 传统分组密码：[AES], [DES], [MARS], RC5, [RC6], [Serpent], SM1, [SM4], [Twofish]等
    - 轻量级分组密码：[PRESENT], HIGHT, SEA, [LBlock], LED, PRINCE, [SIMON], SPECK, PRIDE, Midori, [RECTANGLE]等。

<table align="center">
<tr><td><img alt="AES Candidates" src="http://1.lpxq.sinaapp.com/images/2015/aes_candidates.jpg" width="65%"></td></tr>
<tr><td>AES Candidates</td></tr>
</table>

  + 流密码：[RC4], 祖冲之序列密码等
* 非对称密码：[RSA], ECC, SM2等

<table align="center">
<tr><td><img alt="AES Candidates" src="http://image.beekka.com/blog/201306/bg2013062702.jpg"></td></tr>
<tr><td>RSA inventors</td></tr>
</table>


* 密码杂凑函数：SHA1, [SHA3], MD4, [MD5], SM3等

<table align="center">
<tr><td><img alt="MD5 Sturcture" src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d8/MD5.svg/300px-MD5.svg.png"></td></tr>
<tr><td>MD5 Sturcture</td></tr>
</table>

### 2. OpenPGP

#### 2.1 OpenPGP简介

OpenPGP是一种数据加解密的标准([RFC 4880])，在通信过程中需要用到对称密码，非对称密码以及密码杂凑函数。它定义了通信的协议，至少应该支持的一些密码算法，不同场景算法的操作顺序，数据传输的格式等。这样，当通信双方都在这种标准下工作，则能相互识别发送的数据进而正常通信。

[PGP]是OpenPGP的一种实现，最早由[Phil Zimmermann]在1991年完成，其中的对称密码BassOmatic是由他自己开发完成。最开始，Zimmermann对代码进行了开源，后来因为NAI的限制停止了开源。也正因此，GNU开发了一个开源的版本GnuPG(简称GPG，注意不要弄混了)。

标准中给出了OpenPGP很多数据以及操作流程的定义，例如加密，解密，数字签名，签名认证等。这里只对加密以及解密进行介绍，详细的内容请参考[RFC 4880].

1) 加密

<table align="center">
<tr><td><img alt="Encryption" src="http://www.pgpi.org/images/figures/fig1-4.gif"></td></tr>
<tr><td>Encryption</td></tr>
</table>

  + 发送方生成明文数据plaintext
  + 发送方产生一个随机密钥key，**密钥key只使用一次**
  + 通过对称密码算法在key的作用下对plaintext加密得到ciphertext
  + 使用接受方的公钥k-pub对密钥key进行加密，得到enck
  + 将enck和ciphertext组装得到message
  + 发送

2) 解密

<table align="center">
<tr><td><img alt="Decryption" src="http://www.pgpi.org/images/figures/fig1-5.gif"></td></tr>
<tr><td>Decryption</td></tr>
</table>

  + 接收方接受消息message
  + 按照协议规定拆分得到enck和ciphertext
  + 使用自身的私钥k-pri对enck进行解密得到key
  + 通过对称密码算法在key的作用下对ciphertext解密得到plaintext

#### 2.2 PGP的应用

下面这段话引用维基百科：

> PGP encryption applications include e-mail and attachments, digital signatures, 
> laptop full disk encryption, file and folder security, protection for IM sessions, 
> batch file transfer encryption, and protection for files and folders stored on 
> network servers and, more recently, encrypted and/or signed HTTP request/responses 
> by means of a client side (Enigform) and a server side (mod openpgp) module.

### 3. 扩展阅读

1. [How PGP works](http://www.pgpi.org/doc/pgpintro/#p10)



[AES]:<http://csrc.nist.gov/archive/aes/rijndael/Rijndael-ammended.pdf#page=1>
[DES]:<https://en.wikipedia.org/wiki/Data_Encryption_Standard>
[Serpent]:<http://cryptosoft.net/docs/Serpent.pdf>
[Twofish]:<https://www.schneier.com/academic/paperfiles/paper-twofish-paper.pdf>
[RC6]:<https://people.csail.mit.edu/rivest/pubs/RRSY98.pdf>
[MARS]:<http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.35.5887&rep=rep1&type=pdf>
[SM4]:<https://en.wikipedia.org/wiki/SM4_Algorithm>
[PRESENT]:<http://www.ist-ubisecsens.org/publications/present_ches2007.pdf>
[LBlock]:<https://eprint.iacr.org/2011/345.pdf>
[SIMON]:<https://eprint.iacr.org/2013/404.pdf>
[RECTANGLE]:<https://eprint.iacr.org/2014/084.pdf>
[RC4]:<https://en.wikipedia.org/wiki/RC4>
[RSA]:<https://en.wikipedia.org/wiki/RSA_(cryptosystem)>
[SHA3]:<http://csrc.nist.gov/publications/drafts/fips-202/fips_202_draft.pdf>
[MD5]:<https://en.wikipedia.org/wiki/MD5>
[Clifford Cocks]:<http://www.bristol.ac.uk/pace/graduation/honorary-degrees/hondeg08/cocks.html>
[RFC 4880]:<https://tools.ietf.org/html/rfc4880>
[BassOmatic]:<https://en.wikipedia.org/wiki/BassOmatic>
[Phil Zimmermann]:<https://en.wikipedia.org/wiki/Phil_Zimmermann>
[PGP]:<https://en.wikipedia.org/wiki/Pretty_Good_Privacy>
