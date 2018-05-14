基于 [jieba](https://github.com/fxsjy/jieba) 的 [elasticsearch](https://www.elastic.co/products/elasticsearch) 中文分词插件。

感谢：
https://github.com/huaban/elasticsearch-analysis-jieba 的作者

结巴分词 ElasticSearch 插件
===========================

集成 Lucene / Jieba Analyzer，支持自定义词典。




> 本插件包括 `jieba analyzer`、`jieba tokenizer`、`jieba token filter`，有三种模式供选择。

-	index 主要用于索引分词，分词粒度较细
-	search 主要用于查询分词，分词粒度较粗
-	other 全角转半角、大写转小写、字符分词

安装
----


> 本版本为es5.5.3，如果需要修改，可直接修改对应的pom.xml版本的es版本号就可以了，通用支持es 5X版本号，具体安装参考
https://github.com/huaban/elasticsearch-analysis-jieba
另外不明白可以参考es-ik的安装版本


