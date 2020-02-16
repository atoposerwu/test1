
# 1.SNP   
学习自：
https://cloud.tencent.com/developer/article/1446939 ：定义；类型；发生位置；命名
https://cloud.tencent.com/developer/article/1447204 ：两个数据库 dbSNP HGVS
https://cloud.tencent.com/developer/article/1447229 ：一个数据库 TCGA数据（要翻墙）
https://cloud.tencent.com/developer/article/1451304 ：cBioportal数据库（要翻墙）  UCSC-XENA工具
https://cloud.tencent.com/developer/article/1465029 ：SNP数据下载的最后一讲Fire Browse工具。
https://cloud.tencent.com/developer/article/1468786 ：用maftools对maf文件进行处理
https://cloud.tencent.com/developer/article/1484937 ：画图


## 1.1 定义：

SNP（single nucleotide polymorphism），单核苷酸多态性，在基因组上由单个核苷酸变异形成的遗传标记，一般指变异频率大于1％的单核苷酸变异。If more than 1% of a population does not carry the same nucleotide at a specific position in the DNA sequence, then this variation can be classified as a SNP.

因此，在人类基因组中大概每1000个碱基就有一个SNP, 人类基因组上的SNP 总量大概是3 ×10^6 个。因此，SNP成为第三代遗传标志，人体许多表型差异、对药物或疾病的易感性等等都可能与SNP有关。

## 1.2 SNP发生的类型：

SNP发生包括转换、颠换、插入和缺失，理论上每个位点都可以有4种形式的变异，但是实际上发生的只有转换和颠换两种，据说发生转换和颠换频率是2:1。如果你注意到了，你会发现在发生的转换中总是A突变成G，C突变成T，而且即使是转换，C>T的概率也要大于A>G的概率，这就是为什么研究的SNP为啥会经常是C>T或者A>G了。

补充一下：AT结合与CG结合中结合键是不同的：CG之间是三键结合，AT之间是双键结合，因此CG的结合力要比AT强，也就是说需要更高的温度，才能使得CG解链，这个温度相对应的关键参数就是Tm值，也就是解链一半时候的温度
## 1.3 SNP发生的位置：

SNP可以发生基因组的任何位置，基因编码区/基因非编码区/基因间区等，具体机制其实说也说不清，因为大多数SNP不是在外显子上的。基本上都是进化过程中的一些基因的突变，所以一般都不会是特别关键的位置。当然也不能说完全没有功能，有的会导致可变剪接，或者有的会导致表观上的变化。所以SNP的研究面会比较广，所以会有GWAS这样的项目。关系如下：

### 发生在编码区 

先补充一个概念：密码子简并性（氨基酸对应三联密码子），所以发生SNP不一定会引起编码氨基酸的改变，这就引入了Synonymous SNP（同义突变，不引起任何变化） 和Non-Synonymous SNP（非同义突变，大家关注的焦点）概念。对于不引起编码氨基酸变化的即为同义突变，引起氨基酸变化的则为非同义突变。

非同义突变又可分为错义突变和无义突变

错义突变：编码的某种氨基酸的密码子变成另一种氨基酸密码子，从而多肽链的氨基酸种类和序列发生改变，错义突变通常会使多肽链丧失原有功能。

无义突变：编码某一氨基酸的密码子变成UAA、UGA或UAG（终止密码子），导致多肽链翻译的中止，从而形成一条不完整的多肽链。


### 发生在基因非编码区或基因间区

可能会影响转录因子与DNA结合、影响非编码RNA序列、影响基因的剪接、mRNA的降解等。

## 1.4 SNP的命名

SNP的命名是很混乱的，你会看到RS1800947或者NG_000004.3以及CYP3A5*3。其实不同的组织机构命名不一样，并且坚持自己的命名方法。关于snp位点的命名其实并不统一，大家在文献中一般用的都是习惯或者说惯用名称。具体表现在以下几种形式：
### 01 RS命名法

RS命名法也被称为GenBank官方的refSNP ID单核苷酸多态性命名法，其是相对比较完善的命名体系，命名方法是rs+6/7位阿拉伯数字，包括前后序列，位置信息，分布频率等。如果已知一个SNP的refSNP ID，那么就可以在GenBank的SNP数据库中搜索到相关的信息和在基因组中的位置了。

网址：http://www.ncbi.nlm.nih.gov/snp/

### 02 突变信息之间加上位置信息

主要有三种方式

突变信息之间+cDNA的位置，如C188T；
突变信息之间加上DNA的位置，如A2546G；
突变氨基酸信息之间加上氨基酸位置，如Glu145Lys.

### 03 按发现顺序或频率顺序拟定的惯用名称：
按发现顺序或频率顺序拟定的惯用名称：
发现顺序或频率顺序拟定的惯用名称：

用*表示的，如CYP2D6*10,CYP2C9*3等。

前面加个m，表示突变的，如cyp2c19m2等，

还有一些也可以在文献中见到，如 CYP2E1的c1>c2的突变等等。其实这就是一种非常不正规的用HGVS Names标注SNP位置的方法，很明显，由于缺少引用核酸序列的接受号，因此读者无法从这样的表示在GenBank中查到对应的信息。

### 04 HGVS命名法

HGVS是Human Genome Variation Society (人类基因组变异协会) 的简称，是一个非政府的民间学术组织，其官方网站的网址：http://www.hgvs.org/。

HGVS命名SNP法的规则是标出引用的核酸序列号（Reference Sequence，RefSeq）和SNP在该核酸序列中的位置，例如：NG_000004.3:g.247167G>A，其中红色的部分是核酸序列接受号，绿色的部分是该单核苷酸多态性位点在该核酸序列中的位置，G>A表示原始碱基是G，突变碱基是A。这样的命名方法有利于找出所在基因序列中的位置。

# 2.SNP数据库
SNP的基础知识和数据库使用
https://cloud.tencent.com/developer/article/1447204

- dbSNP 网址：https://www.ncbi.nlm.nih.gov/snp/    
- HGVS 网址：http://www.hgvs.org/  

SNP数据的下载
https://cloud.tencent.com/developer/article/1447229
TCGA网址亮出：https://portal.gdc.cancer.gov/ 
https://cloud.tencent.com/developer/article/1451304
cBioportal数据库
UCSC-XENA工具

- 分享关于TCGA_SNP下载的知识，还记得我们之前推文说过的，在TCGA的武林里，总有一个出类拔萃的佼佼者的神包——TCGAbiolinks，链接：手把手教你用R语言下载TCGA数据库：TCGAbiolinks

复习一下该包TCGAbiolinks，它是GDC官方推荐了一款第三方工具，通过GDC官方API下载数据，保证数据的及时性和准确性，同时也提供数据整理、聚类分析、差异分析、富集分析等功能。
