---
layout: post
title:  "scrapy note"
date:   2014-11-09	10:34:18
categories: [python]
tags: [scrapy,tutorial]

---

[http://doc.scrapy.org](http://doc.scrapy.org/en/latest/intro/tutorial.html)

install `pip` [click here](https://pip.pypa.io/en/latest/installing.html#install-pip)

## install scrapy

	
```
sudo pip install scrapy 
or
sudo easy_install Scrapy
```
	

## tutorial project 


* set up a new Scrapy project
	
```
scrapy startproject proName
```

* This will create a tutorial directory with the following contents:

```
tutorial/
   	scrapy.cfg
   	tutorial/
        __init__.py
        items.py
        pipelines.py
        settings.py
        spiders/
            __init__.py
           ...
```
* we edit items.py, found in the tutorial directory. Our Item class looks like this:

```
import scrapy

class DmozItem(scrapy.Item):
    title = scrapy.Field()
    link = scrapy.Field()
    desc = scrapy.Field()
```
	
## xpath	

1. `/html/head/title` : selects the `<title>` element, inside the `<head>` element of a HTML document
 
2. `/html/head/title/text()` : selects the text inside the aforementioned `<title>` element
 
3. `//td` : selectes all the `<td>` elements
 
4. `//div[@class="mine"]` : selects all `<div>` elements which contains an 	attribute `class="mine"`
 

* This is the code for our first Spider; save it in a file named `dmoz_spider.py` under the `tutorial/spiders` directory:


```
	import scrapy

	from tutorial.items import DmozItem
	
	class DmozSpider(scrapy.Spider):
	    name = "dmoz"
	    allowed_domains = ["dmoz.org"]
	    start_urls = [
	        "http://www.dmoz.org/Computers/Programming/Languages/Python/Books/",
	        "http://www.dmoz.org/Computers/Programming/Languages/Python/Resources/"
	    ]
	
	    def parse(self, response):
	        for sel in response.xpath('//ul/li'):
	            item = DmozItem()
	            item['title'] = sel.xpath('a/text()').extract()
	            item['link'] = sel.xpath('a/@href').extract()
	            item['desc'] = sel.xpath('text()').extract()
            yield item
```


* Storing the scraped data


```
scrapy crawl dmoz -o items.json
```

## Trying Selectors in the Shell
	

```			
scrapy shell "http://www.dmoz.org/Computers/Programming/Languages/Python/Books/"		
```