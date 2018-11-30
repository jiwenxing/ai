# Elasticsearch Introduction
---


[Elasticsearch](https://www.elastic.co/) 是一个基于 Lucene 的分布式、可扩展、近实时的搜索与数据分析引擎。具有实时搜索、稳定、可靠、快速、安装使用方便等特点。Elasticsearch 可以横向扩展至数百（甚至数千）的服务器节点，同时可以处理 PB 级数据。


## Application Examples

- Wikipedia 使用 Elasticsearch 提供带有高亮片段的全文搜索，还有 search-as-you-type 和 did-you-mean 的建议
- Stack Overflow 将地理位置查询融入全文检索中去，并且使用 more-like-this 接口去查找相关的问题与答案
- GitHub 使用 Elasticsearch 对 1300 亿行代码进行查询


## Lucene vs Solar vs Elasticsearch



**Lucene** 是一套信息检索工具包，并不包含搜索引擎系统，它包含了索引结构、读写索引工具、相关性工具、排序等功能，Lucene 的核心 jar 包只有一个文件，而且不依赖任何第三方 jar 包。因此在使用 Lucene 时仍需要关注搜索引擎系统，例如数据获取、解析、分词等方面的东西。而 solr 和 elasticsearch 都是基于该工具包做的一些封装。他们之间的关系可以很形象的理解为汽车（solr、elasticsearch）和发动机（Lucene）。

**Solr** 是一个有 HTTP 接口的基于 Lucene 的查询服务器，封装了很多 Lucene 细节，自己的应用可以直接利用诸如 .../solr?q=abc 这样的 HTTP GET/POST 请求去查询，维护修改索引。

Lucene 使用上更加灵活，但是你需要自己处理搜素引擎系统架构，以及其他附加功能的实现。因此严格意义上来讲，它只是一个工具包，并不是一个完整的搜索引擎系统，下面主要介绍一下它的两个开源实现 Solar 和 Elasticsearch 的区别，便于针对业务特点进行技术选型。

![](http://pgdgu8c3d.bkt.clouddn.com/201810121813_508.png)


当单纯的对已有数据进行搜索时，Solr 更快，因为实时建立索引时, Solr 会产生 io 阻塞，查询性能较差, 这方面 Elasticsearch 具有明显的优势。另外随着数据量的增加，Solr 的搜索效率会变得更低，而 Elasticsearch 却没有明显的变化。总体而言，Elasticsearch 更适用于新兴的实时搜索应用，再加上其更加易用的特点，这些决定了Elasticsearch 将变得越来越受欢迎。

## 简单概括一下 Elasticsearch 搜索原理




MySQL 与 elasticsearch 的概念对应关系

![](http://pgdgu8c3d.bkt.clouddn.com/201810101945_809.png)


>qshell account G4T2TrlRFLf2-Da-IUrHJK
SbVYbJTGpcwBVFbz3D 0wgbpmquurY_BndFuPvDGqzlnfWHCdL8YHjz_fHJ

>qshell listbucket forblog blog.txt

>qshell batchmove -force -overwrite forblog temp blog.txt
