# 关于GEO数据库学习



##文章信息：

Series：GSE188545

题目：人类大脑颞中回的单细胞图谱揭示了阿尔茨海默病中“性别特异性”和“细胞类型特异性”的基因表达调控

Tips大脑颞中回：一个受阿尔茨海默病强烈影响的大脑皮质区域

数据来源：对死后冷冻的人类颞中回脑组织进行了无偏性的大规模平行单核RNA测序。

样本来源：6位AD患者(AD,V/VI)与6位年龄匹配的健康(HC,I/II)对照



## 关于上游分析和下游分析：

上游分析：原始数据-表达矩阵

Step：1、环境配置

​			2、下载数据文件 SRA Toolkit：利用软件，下载sra文件（压缩文件）解压后是fastq(原始数据)

​			3、cell ranger软件：处理fastq数据：下载软件——修改文件名——建立参考基因组——获得表达矩阵

下游分析：表达矩阵分析



## 关于Supplementary file：

上游分析的数据都在SRA里，最原始的数据就是测序出来的序列；

![image-20230426231134628](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230426231134628.png)



下游分析是经过上游分析得到的表达矩阵，每个样本的数据的由三个文件组成：

![image-20230426230315346](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230426230315346.png)

barconses.tsv：每个细胞的代码

![image-20230426233402364](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230426233402364.png)



gene.tsv：基因的ensembl ID和symbol（gene.tsv比features.tsv会多一行gene expression）

![image-20230426233446126](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230426233446126.png)



matrix.mtx：每个细胞不同基因的表达矩阵

![image-20230426233113200](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230426233113200.png)

第一列：gene.ID，匹配gene.tsv

第二列：细胞的编号，匹配barconses.tsv

第三列：基因的表达量



## 下载supplement file：

1、直接copy link：发现下载的文件无法打开也无法使用

![image-20230427095930131](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230427095930131.png)

```
wget https://www.ncbi.nlm.nih.gov/geo/download/?acc=GSE188545&format=file
```

![](/Users/gorgeous/Library/Application Support/typora-user-images/image-20230427100033292.png)



2、需要将copy link转化为url格式：

tips：wget <option> <url>-软件版本信息

利用https://tool.lu/urlconvert/网站转换获取真实网址，将真实网址在新页面打开：

<img src="/Users/gorgeous/Library/Application Support/typora-user-images/image-20230427101903196.png" alt="image-20230427101903196" style="zoom:50%;" />

3、输入代码下载：

```R
wget --no-check-certificate https://ftp.ncbi.nlm.nih.gov/geo/series/GSE188nnn/GSE188545/suppl/GSE188545_RAW.tar
```

4、对文件进行解打包：

```R
tar -xvf GSE188545_RAW.tar.2
```





Tips:我的数据管理：

GSE188545:电脑端下载，直接传入+单个样本

ges188545:服务器下载，解打包后的文件
