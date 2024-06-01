### 爬取数据的字段不按照顺序，解决方法

- 在settings.py中加入：

```python
FEED_EXPORT_FIELDS = ["name", "title", "info"] #列表中改成你想要输出的字段顺序
```



### 爬取商品网站价格符号问题

如果你的爬取结果中的价格数据带有其他符号，例如货币符号、千位分隔符等，可以使用Python内置的字符串方法进行处理。一种常用的方法是使用正则表达式来匹配数字，并去除无关符号。下面是一个示例代码：

```python
pythonCopy codeimport re

def parse(self, response):
    for x in response.xpath('//ul[@class="bigimg cloth_shoplist"]'):
        for item in x.xpath('li'):
            name = ...
            title = ...

            # 处理价格
            price_str = item.xpath('p[@class="price"]/span/text()').extract_first().strip()
            price = re.search(r'\d+(\.\d+)?', price_str).group()

            yield {
                'name': name,
                'title': title,
                'price': price
            }
```

在这个示例中，我们首先使用`re.search()`函数和正则表达式`\d+(\.\d+)?`来匹配价格值，其中`\d+`表示匹配一个或多个数字，`\.`表示匹配小数点（需要转义），`\d+`表示匹配一个或多个数字（即小数部分），而`(\.\d+)?`表示小数部分是可选的（即价格可能为整数）。最后，我们使用`.group()`方法获取匹配到的数字部分，作为最终的价格值。

需要注意的是，如果你的价格数据中包含多个数字，例如“¥ 1,234.56”，上述正则表达式只会匹配到第一个数字“1”，因此需要根据具体情况进行修改。