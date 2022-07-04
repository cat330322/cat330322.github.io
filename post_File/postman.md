postman

```
使用PostMan测试WebService接口
一、操作步骤
1、设置URL
2、设置请求模式：Post
3、设置Header：添加 Content-Type ，值为 text/xml;charset=utf-8
4、设置Body：勾选raw
5、输入Body内容：（详见 二）
二、请求WebService时的Body结构
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
　　<soap:Body>
　　　　<getWeather xmlns="http://WebXml.com.cn/">
　　　　　　<theCityCode>string</theCityCode>
　　　　　　<theUserID>string</theUserID>
　　　　</getWeather>
　　</soap:Body>
</soap:Envelope>
详细说明：
（1） getWeather是方法名。
（2）theCityCode、theUserID是方法参数。
三、WebService响应时的Body结构
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
　　<soap:Body>
　　　　<getWeatherResponse xmlns="http://WebXml.com.cn/">
　　　　　　<getWeatherResult>
　　　　　　　　<string>string</string>
　　　　　　　　<string>string</string>
　　　　　　</getWeatherResult>
　　　　</getWeatherResponse>
　　</soap:Body>
</soap:Envelope>
（1）getWeatherResult是方法的返回值。
```

```
POST:http://xxxxxx.asmx
<?xml version="1.0" encoding="utf-8"?>
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
  <soap:Body>
    <runservice xmlns="http://tempuri.org/">
      <TradeMsg><![CDATA[<?xml version="1.0" encoding="utf-8"?>xxxxxxxx</TradeMsg>
    </runservice>
  </soap:Body>
</soap:Envelope>
```

