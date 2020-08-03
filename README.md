# Literature-Clustering-Bert
使用开源的Bert-as-Service预训练生成文档特征向量，基于k-means对COVID-19文献聚类，t-SNE可视化数据，通过LDA为每个簇生成主题关键词，画Bokeh图实现按簇、关键词搜索和筛选数据。

一、数据：
数据集包括 CSV 文件和 JSON 文件两种类型：
（1）metadata.csv 文件：每条数据代表一篇文献，包含 44000 条，18 个属性。
（2）pdf_json和pmc_json路径下含有 113933 个 JSON 文件：每个 JSON 文件代表一篇文献，包含 paper_id, title, authors, abstract, body_text 等属性。

二、目录：
1.加载数据
2.预处理
3.向量化
4.PCA & 聚类
5.t-SNE降维
6.每个集群的主题建模
7.分类
8.绘制图
9.如何使用绘制图?
10.结论
11.Citation/Sources

三、方法：
1.使用自然语言处理（NLP）解析每个文档正文中的文本。
2.使用Bert-as-Service将每个文档实例𝑑𝑖转换为特征向量𝑋𝑖。
3.利用t-分布随机邻域嵌入（t-SNE）对每个特征向量𝑋𝑖进行降维，在二维平面𝑋嵌入𝑌1上聚类相似的研究文献。
4.使用主成分分析（PCA）将嵌入的𝑌2中的噪声和异常值去除时，将𝑋的维数投影到保留.95方差的若干维数。
5.在𝑌2上应用k-means聚类，其中𝑘为20，以在𝑌1上标记每个簇。
6.在𝑋上应用主题建模，使用隐狄利克雷分配模型（LDA，一种用于离散数据集合（如文本语料库）的生成概率模型。）从每个集群中发现关键字。
7.在图上直观地调查聚类，根据需要缩小到特定的文章，并使用随机梯度下降（SGD）进行分类。
