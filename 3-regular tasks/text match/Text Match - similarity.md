### tools

<https://github.com/taki0112/Vector_Similarity> 

<https://github.com/crownpku/text2vec>



### Summary

- Cosine Similarity

![img](http://note.youdao.com/yws/res/946/WEBRESOURCE3d5765f215b87ace587812a207d3427b)

$Cosine(A,B) = Cosine(A,C) = Cosine(A,D)$

B、C、D的量纲不一样



缺点：

没有考虑量纲，只考虑夹角大小

就词向量而言，量纲在一定程度上表示词语的重要性（词频）



- Euclidean Distance

![img](http://note.youdao.com/yws/res/959/WEBRESOURCE2e55dcb3e0466af74af0ce195d119de6)

$ED(A,B) = \sqrt{\sum\limits^k_{n=1} (A(n) - B(n))^2}$

ED - 差值之平方和的根号

$ED(M,P) = ED(M,Q) = ED(M,R)$

P、Q、R的夹角不一样



缺点：

没有考虑夹角，只考虑量纲



- Triangle’s Area Similarity (TS) - 三角面积

![img](http://note.youdao.com/yws/res/974/WEBRESOURCEc14e714fcd0845dc0a2ddd8d25180bdd)

$TS(A,B) = \frac{|A| \cdot |B| \cdot sin(\theta')}{2}$

$\theta' = cos^{-1}(V) + 10$

(避免向量角度重叠计算失效)



优点：

既考虑夹角，也考虑量纲



缺点：（面积越小，越相似）

TS(A,D) < TS(A,B)，与实际情形不相符。



- Sector’s Area Similairity (SS) - 扇形面积

![img](http://note.youdao.com/yws/res/982/WEBRESOURCE250cfe8dc60f832cb3aedf02a6494bb5)



$MD(A,B) = | \sqrt{\sum\limits^k_{n=1}A^2_n} - \sqrt{\sum\limits^k_{n=1}B^2_n}|$

MD - 平方和之根号的差值之绝对值

$SS(A,B) = \pi \cdot (ED(A,B) + MD(A,B))^2 \cdot (\frac{\theta'}{360})$



- TS-SS

![img](http://note.youdao.com/yws/res/1000/WEBRESOURCEab27708b43a1f0aa8f760cf58efc5e5d)



优点：

不仅具备Triangle’s Area Similarity的优点，也修正了Triangle’s Area Similarity的缺点。