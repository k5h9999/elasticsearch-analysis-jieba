基于 [jieba](https://github.com/fxsjy/jieba) 的 [elasticsearch](https://www.elastic.co/products/elasticsearch) 中文分词插件。

感谢：
https://github.com/huaban/elasticsearch-analysis-jieba


```
把release/elasticsearch-analysis-jieba-{version}.zip文件解压到 elasticsearch 的 plugins 目录下，重启elasticsearch即可。

创建字段：
```bash

curl -XPOST http://localhost:9200/index/type/_mapping -d'
{
        "properties": {
            "content": {
                "type": "text",
                "analyzer": "jieba",
                "search_analyzer": "jieba"
            }
        }
    }
}'
```


直接使用Tokenizer分词
=======
可直接使用 `com.github.hongfuli.jieba.Tokenizer` 对文本字符进行分词，方法参数完全和 [jieba python](https://github.com/fxsjy/jieba) 一致。

```java
imort com.github.hongfuli.jieba.Tokenizer

Tokenizer t = new Tokenizer();
t.cut("这是一个伸手不见五指的黑夜。我叫孙悟空，我爱北京，我爱Python和C++。", false, true);
```



```
本插件包括 jieba analyzer、jieba tokenizer、jieba token filter，有三种模式供选择。

index 主要用于索引分词，分词粒度较细
search 主要用于查询分词，分词粒度较粗
other 全角转半角、大写转小写、字符分词
```