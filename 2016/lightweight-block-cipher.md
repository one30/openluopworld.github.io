---
layout: default
---

# 轻量级分组密码算法
2016.06.14

* Block size and key size are in bit

|   Cipher            | Block Size    | Key Size        | Rounds        | Structure | Published    |
| ---------         - | ----------    |----------       |--------       |-----------|-----------   |
| [MISTY]             |    64         | 128             |  8            |  Feistel  |  FSE'97      |
| [HIGHT]             |    64         | 128             |  32           |  GFS      |  CHES'06     |
| [SEA]               |    96         | 96              |  ?            |  Feistel  |  SCRAA'06    |
| [CLEFIA]            |    128        |128<br>192<br>256|18<br>22<br>26 |  GFN      |  FSE'07      |
| [PRESENT]           |    64         | 80<br>128       |  31           |  SPN      |  CHES'07     |
| [KTANTAN]<br>[KATAN]|32<br>48<br>64 | 80              |  254          |stream cipher like|CHES'09|
| [LBlock]            |    64         | 80              |  32           |  Feistel  |  ACNS'11     |
| [LED]               |    64         | 64<br>128       |  32<br>48     |  SPN      |  CHES'11     |
| [Piccolo]           |    64         | 80<br>128       |  25<br>31     |  GFN      |  CHES'11     |
| [TWINE]             |    64         | 80<br>128       |  36           |  GFN      |Workshop on LC'11|
| [KLEIN]             |    64         | 64<br>80<br>96  | 12<br>16<br>20|  SPN      |  SaP'12      |
| [PRINCE]            |    64         | 128             |  10           |  SPN      |ASIACRYPT'12  |
| [LEA]               | 128           |128<br>192<br>256| 24<br>28<br>32|  GFN      |  WISA'13     |
| [SIMON]             | 64            |96<br>128        | 42<br>44      |  Feistel  |eprint.eacr'13|
| [SPECK]             | 64            |96<br>128        | 26<br>27      |  ARX      |eprint.eacr'13|
| [Chaskey]           | 128           | 128             |  8            |  ARX      |  SAC'14      |
| [Fantomas]          | 128           | 128             |  12           |  SPN      |  FSE'14      |
| [PRIDE]             | 64            | 128             |  20           |  SPN      |  CRYPTO'14   |
| [Robin]             | 128           | 128             |  16           |  SPN      |  FSE'14      |
| [Midori]            | 64<br>128     | 128             |  16<br>20     |  SPN      |Asiacrypt'15  |
| [RECTANGLE]         | 64            | 80<br>128       |  25           |  SPN      |sci China'15  |
|[RoadRunneR]         | 64            | 80<br>128       |  10<br>12     |  Feistel  |  LightSec'15 |
| [SIMECK]            |32<br>48<br>64 | 64<br>96<br>128 |32<br>36<br>44 |  Feistel  |  CHES'15     |

<!-- mCrypton, Mysterion, PrintCipher, XTEA, Zorro, MIBS, TEA -->
* MISTY: Has two different versions MISTY1 and MISTY2.
* SEA: Has many other versions. A letter in the name of the author is wrong.
* CLEFIA: Designed by Sony Corperation.
* KATAN: A letter in the name of the author is wrong.
* SIMON and SPECK have many versions. Only the versions with 64-bit block size are given here

  [MISTY]: <http://dx.doi.org/10.1007/BFb0052334>
  [HIGHT]: <https://www.iacr.org/archive/ches2006/04/04.pdf>
  [SEA]: <http://dx.doi.org/10.1007/11733447_16>
  [CLEFIA]: <http://dx.doi.org/10.1007/978-3-540-74619-5_12>
  [PRESENT]: <https://www.iacr.org/archive/ches2007/47270450/47270450.pdf>
  [KTANTAN]: <http://dx.doi.org/10.1007/978-3-642-04138-9_20>
  [KATAN]: <http://dx.doi.org/10.1007/978-3-642-04138-9_20>
  [LBlock]: <https://eprint.iacr.org/2011/345.pdf>
  [LED]: <https://eprint.iacr.org/2012/600.pdf>
  [Piccolo]: <http://www.iacr.org/archive/ches2011/69170343/69170343.pdf>
  [TWINE]: <http://jpn.nec.com/rd/crl/code/research/image/twine_SAC_full_v5.pdf>
  [KLEIN]: <http://doc.utwente.nl/73129/1/The_KLEIN_Block_Cipher.pdf>
  [PRINCE]: <https://eprint.iacr.org/2014/453.pdf>
  [LEA]: <http://seed.kisa.or.kr/html/egovframework/iwt/ds/ko/ref/LEA%20A%20128-Bit%20Block%20Cipher%20for%20Fast%20Encryption%20on%20Common%20Processors-English.pdf>
  [SIMON]: <https://eprint.iacr.org/2013/404.pdf>
  [SPECK]: <https://eprint.iacr.org/2013/404.pdf>
  [Chaskey]: <https://eprint.iacr.org/2014/386.pdf>
  [PRIDE]: <https://eprint.iacr.org/2014/453.pdf>
  [Midori]: <https://eprint.iacr.org/2015/1142.pdf>
  [RECTANGLE]: <https://eprint.iacr.org/2014/084.pdf>
  [RoadRunneR]: <http://dx.doi.org/10.1007/978-3-319-29078-2_4>
  [SIMECK]: <https://eprint.iacr.org/2015/612>
  [Fantomas]: <http://dx.doi.org/10.1007/978-3-662-46706-0_2>
  [Robin]: <http://dx.doi.org/10.1007/978-3-662-46706-0_2>
