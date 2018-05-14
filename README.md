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





测试
----

```sh
curl -XPUT 127.0.0.1:9200/test -d '{
    "settings" : {
        "number_of_shards" : 1,
        "number_of_replicas" : 0

    },
    "mappings" : {
        "test" : {
            "_all" : { "enabled" : false },
            "properties" : {
                "name" : { "type" : "string", "analyzer" : "jieba_index", "search_analyzer" : "jieba_search" }
            }
        }
    }
}';echo



curl 'http://127.0.0.1:9200/test/_analyze?analyzer=jieba_index' -d '中华人民共和国';echo
curl 'http://127.0.0.1:9200/test/_analyze?analyzer=jieba_search' -d '中华人民共和国';echo
curl 'http://127.0.0.1:9200/test/_analyze?analyzer=jieba_other' -d '中华人民共和国 HelLo';echo
```

如何发布一个版本
------


```
github-release release \
    --user huaban \
    --repo elasticsearch-analysis-jieba \
    --tag v2.3.5 \
    --name "v2.3.5" \
    --description "支持 ES v2.3.5"

github-release upload \
    --user huaban \
    --repo elasticsearch-analysis-jieba \
    --tag v2.3.5 \
    --name "elasticsearch-analysis-jieba-2.3.5-bin.zip" \
    --label "plugin.zip" \
    --file target/releases/elasticsearch-analysis-jieba-2.3.5-bin.zip
```


