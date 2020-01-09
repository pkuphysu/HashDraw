# HashDraw
用哈希抽奖，先胡个提案，如果可行就使用这个仓库

## 导语
众所周知，抽奖程序一度不会拥有很高的信任度。尤其是当 js 的`Math.random()`在抽奖过程中的有限次实验中，出现了一些“统计性”偏差时，很显然会遭到质疑。

## 新方案
使用哈希抽奖，就可以一定程度上避免质疑暗箱操作的情况。

可行性：
- 作为物院同学，即使不知道哈希的概念，进行节目现场普及，也是很容易就能理解的

难点：
- 一二三等奖最好要使用不同的算法
    - 而且最好是三二一逐步加强
    - 但这就要求三等奖不能太弱，否则会遭质疑；也不能太强，要给一等奖留有空间，不能过于复杂
- 如何制造一个惊心动魄的抽奖体验
- 如何通过随机性、可验证性来使人信服
- 什么时候公布奖项的算法会收到好的效果

## 参考资料
<https://softwareengineering.stackexchange.com/a/145633>
```
Hash           Lowercase      Random UUID  Numbers
=============  =============  ===========  ==============
Murmur            145 ns      259 ns          92 ns
                    6 collis    5 collis       0 collis
FNV-1a            152 ns      504 ns          86 ns
                    4 collis    4 collis       0 collis
FNV-1             184 ns      730 ns          92 ns
                    1 collis    5 collis       0 collis▪
DBJ2a             158 ns      443 ns          91 ns
                    5 collis    6 collis       0 collis▪▪▪
DJB2              156 ns      437 ns          93 ns
                    7 collis    6 collis       0 collis▪▪▪
SDBM              148 ns      484 ns          90 ns
                    4 collis    6 collis       0 collis**
SuperFastHash     164 ns      344 ns         118 ns
                   85 collis    4 collis   18742 collis
CRC32             250 ns      946 ns         130 ns
                    2 collis    0 collis       0 collis
LoseLose          338 ns        -             -
               215178 collis
```

## 随机源及身份源的选择
- 弹幕内容
- 弹幕发送时间（只能精确到分，否则又会引起争议）
- 微信头像
- 微信昵称
- 晚会进程（抽奖环节开始时间）

### 投点的实现方式
在每个人的身份源后，有规律地添加其权重个数，分别求哈希，投入奖池。

... To be continued ...
