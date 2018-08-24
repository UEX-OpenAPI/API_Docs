# UEX OpenAPI文档


## 通用规则
  
**_apikey_ 和 _secret_ 的获取，在UEX "[API管理](https://www.uex.com/my_open_api.html)"页面中生成获得。**

**Base url：** https://open-api.uex.com

**sign签名：**  
请求参数按照字典排序，然后以keyvalue的形式拼接成字符串string，最后sign=MD5(string+secretKey)。  
注意：如果请求参数中value为NULL的情况，则在拼接字符串时不计入签名字符串。    

 示例如下   
```python
def sign (data, apikey, secret):
    data = copy.deepcopy(data)
    data['time'] = int(time.time())
    data['api_key'] = apikey
    keys = list(data.keys())
    keys.sort()
    part = []
    for key in keys:
        val = data[key]
        if val is None:
            continue
        part.append(str(key) + str(val))
    text = ''.join(part)
    text = (text + secret).encode('utf-8')
    data['sign'] = hashlib.md5(text).hexdigest()
    return data 
```	

<br>
  
## POST请求参数采用表单格式提交数据
**content-type:application/x-www-form-urlencoded**

<br>

## 文档目录

[Home](https://github.com/UEX-OpenAPI/API_Docs/wiki)

[/open/api/all_order-获取全部委托](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E8%8E%B7%E5%8F%96%E5%85%A8%E9%83%A8%E5%A7%94%E6%89%98)

[/open/api/all_trade-获取全部成交记录](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E8%8E%B7%E5%8F%96%E5%85%A8%E9%83%A8%E6%88%90%E4%BA%A4%E8%AE%B0%E5%BD%95)

[/open/api/cancel_order-取消委托单](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E5%8F%96%E6%B6%88%E5%A7%94%E6%89%98%E5%8D%95)

[/open/api/common/symbols 查询系统支持的所有交易对及精度](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E6%9F%A5%E8%AF%A2%E7%B3%BB%E7%BB%9F%E6%94%AF%E6%8C%81%E7%9A%84%E6%89%80%E6%9C%89%E4%BA%A4%E6%98%93%E5%AF%B9%E5%8F%8A%E7%B2%BE%E5%BA%A6)

[/open/api/create_order-创建订单](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E5%88%9B%E5%BB%BA%E8%AE%A2%E5%8D%95)

[/open/api/get_records 获取K线数据](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E8%8E%B7%E5%8F%96K%E7%BA%BF%E6%95%B0%E6%8D%AE)

[/open/api/get_ticker 获取当前行情](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E8%A1%8C%E6%83%85)

[/open/api/get_trades 获取行情成交记录](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E8%8E%B7%E5%8F%96%E8%A1%8C%E6%83%85%E6%88%90%E4%BA%A4%E8%AE%B0%E5%BD%95)

[/open/api/market_dept 查询买卖盘深度](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E6%9F%A5%E8%AF%A2%E4%B9%B0%E5%8D%96%E7%9B%98%E6%B7%B1%E5%BA%A6)

[/open/api/market-获取各个币对的最新成交价](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E8%8E%B7%E5%8F%96%E5%90%84%E4%B8%AA%E5%B8%81%E5%AF%B9%E7%9A%84%E6%9C%80%E6%96%B0%E6%88%90%E4%BA%A4%E4%BB%B7)

[/open/api/new_order-获取当前委托](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E8%8E%B7%E5%8F%96%E5%BD%93%E5%89%8D%E5%A7%94%E6%89%98)

[/open/api/order_info-获取订单详情](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E8%8E%B7%E5%8F%96%E8%AE%A2%E5%8D%95%E8%AF%A6%E6%83%85)

[/open/api/user/account-资产余额](https://github.com/UEX-OpenAPI/API_Docs/wiki/%E8%B5%84%E4%BA%A7%E4%BD%99%E9%A2%9D)


