---
layout:     post
title:      scrapy框架中如果想在爬虫py文件中各个函数间传递item怎么办？
subtitle:   不同的item在不同层级的网页上的处理方式——meta参数
date:       2018-12-12
author:     WHY
header-img: img/post-bg-universe.jpg
catalog: true
tags:
    - scrapy
    - item
    - meta
---

## 同时传递数据和url

当在一个方法中获取到数据及url后，且需要同时传递数据和url给下一个函数，此时，无法单纯利用return和yield完成，就需要借助meta方法，上代码，看注释部分

```

```

```python
# -*- coding: utf-8 -*-
import scrapy
from Tmiddle.items import TmiddleItem


class TmiddleSpider(scrapy.Spider):
    name = 'tmiddle'
    allowed_domains = ['www.baidu.com']
    start_urls = ['http://www.baidu.com/']


    def parse(self, response):
        item = TmiddleItem()
        print("我是爬虫程序parse函数输出")
        item['n'] = 1
        url = 'http://www.baidu.com/'
        yield scrapy.Request(url,meta={'item': item}, callback=self.getHtml)
#利用meat={'item':item}传递数据
    def getHtml(self, response):
        item = response.meta['item']#利用response.meat接收参数
        item['b'] = 2
        yield item
```