---
layout: post
title: Lightweight block cipher history
date: 2016.06.14
discription: 常见轻量级分组密码算法简介
---

# Basic Info of Some Block Ciphers

* Block size and key size are in bit
* "Whiten key" to indicate whether the cipher has a last round key-eor after the loop

|   Cipher   | Block Size | Key Size |        Authors	              | Rounds        | Whiten Key | Structure | Published    |
| ---------- | ---------- |----------|-----------------------         |--------       |------------|-----------|-----------   |
| [MISTY]    |    64      |   128    |      Mitsuru Matsui            |  8            |   No       |  Feistel  |  FSE'97      |
| [HIGHT]    |    64      |   128    |      Deukjo Hong et al.        |  32           |   Yes      |  GFS      |  CHES'06     |
| [SEA]      |    96      |   96     |Francois-Xavier Standaert et al.|  ?            |   No       |  Feistel  |  SCRAA'06    |
| [CLEFIA]   |    128     |128<br>192<br>256|   Taizo Shirai et al.   |18<br>22<br>26 |   ?        |  GFN      |  FSE'07      |
| [PRESENT]  |    64      | 80<br>128|   A. Bogdanov et al.           |  31           |   Yes      |  SPN      |  CHES'07     |
| [KTANTAN]<br>[KATAN]| 32<br>48<br>64 | 80 | Christophe De Canniere et al. | 254     |          |stream cipher like |CHES'09 |
| [LBlock]   |    64      | 80       |      Wu Wenling et al.         |  32           |   No       |  Feistel  |  ACNS'11     |
| [LED]      |    64      | 64<br>128|      Guo Jian et al.           |  32<br>48     |            |  SPN      |  CHES'11     |
| [Piccolo]  |    64      | 80<br>128|      Kyoji Shibutani et al.    |  25<br>31     |            |  GFN      |  CHES'11     |
| [TWINE]    |    64      | 80<br>128|      Tomoyasu Suzaki et al.    |  36           |            |  GFN      |Workshop on LC'11|
| [KLEIN]    |    64 | 64<br>80<br>96|      Zheng Gong et al.         | 12<br>16<br>20|            |  SPN      |  SaP'12      |
| [PRINCE]   |    64      |   128    |      Julia Borghoff et al.     |  10           |            |  SPN      |ASIACRYPT'12  |
| [LEA]      | 128| 128<br>192<br>256|      Deukjo Hong et al.        | 24<br>28<br>32|            |  GFN      |  WISA'13     |
| [SIMON]    | 64         |96<br>128 |      Ray Beaulieu et al.       | 42<br>44      |   No       |  Feistel  |eprint.eacr'13|
| [SPECK]    | 64         |96<br>128 |      Ray Beaulieu et al.       | 26<br>27      |   No       |  ARX      |eprint.eacr'13|
| [Chaskey]  | 128        |  128     |      Nicky Mouha et al.        | 8             |   Yes      |  ARX      |  SAC'14      |
| [Fantomas] | 128        |  128     |      Vincent Grosso et al.     | 12            |            |  SPN      |  FSE'14      |
| [PRIDE]    | 64         | 128      |      Martin R. Albrechts et al.| 20            |            |  SPN      |  CRYPTO'14   |
| [Robin]    | 128        | 128      |      Vincent Grosso et al.     | 16            |            |  SPN      |  FSE'14      |
| [Midori]   | 64<br>128  | 128      |      Subhadeep Banik et al.    | 16<br>20      |            |  SPN      |Asiacrypt'15  |
| [RECTANGLE]| 64         | 80<br>128|      Zhang Wentao et al.       | 25            |   Yes      |  SPN      |sci China'15  |
|[RoadRunneR]| 64         | 80<br>128|      Adnan Baysal et al.       | 10<br>12      |            |  Feistel  |  LightSec'15 |
| [SIMECK]   |32<br>48<br>64 | 64<br>96<br>128 | Gangqiang Yang et al.|32<br>36<br>44 |   No       |  Feistel  |  CHES'15     |

<!-- mCrypton, Mysterion, PrintCipher, XTEA, Zorro -->
* MISTY: Has two different versions MISTY1 and MISTY2.
* SEA: Has many other versions. A letter in the name of the author is wrong.
* CLEFIA: Designed by Sony Corperation.
* KATAN: A letter in the name of the author is wrong.
* SIMON and SPECK have many versions. Only the versions with 64-bit block size are given here

[//]: #

  [MISTY]: <http://dx.doi.org/10.1007/BFb0052334>
  [HIGHT]: <https://www.iacr.org/archive/ches2006/04/04.pdf>
  [SEA]: <http://dx.doi.org/10.1007/11733447_16>
  [CLEFIA]: <http://dx.doi.org/10.1007/978-3-540-74619-5_12>
  [PRESENT]: <>
  [KTANTAN]: <>
  [KATAN]: <>
  [LBlock]: <>
  [LED]: <>
  [Piccolo]: <>
  [TWINE]: <>
  [KLEIN]: <>
  [PRINCE]: <>
  [LEA]: <>
  [SIMON]: <>
  [SPECK]: <>
  [Chaskey]: <>
  [Fantomas]: <>
  [PRIDE]: <>
  [Robin]: <>
  [Midori]: <>
  [RECTANGLE]: <>
  [RoadRunneR]: <>
  [SIMECK]: <>
