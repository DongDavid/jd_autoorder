# 京东预约商品抢购

借鉴了[https://github.com/Lasx/jd_mask](https://github.com/Lasx/jd_mask)的代码
十分感谢原作者！  

本来其实是准备直接下载下来用的， 但是跑了一下， 失败了， 因为送货地址取不到。然后自己改了一下代码。  

在2022/12/26晚上用来抢了一单抗原，它能自动下单成功， 下单成功后需要你去点开订单手动支付。

```
2022-12-26 20:15:00,335 INFO: 时间到达，开始执行……
2022-12-26 20:15:00,534 INFO: 抢购链接获取失败，%s不是抢购商品或抢购页面暂未刷新，1秒后重试
2022-12-26 20:15:01,735 INFO: 抢购链接获取成功: https://marathon.jd.com/captcha.html?skuId=xxxxx
2022-12-26 20:15:01,735 INFO: 访问商品的抢购连接...
2022-12-26 20:15:01,980 INFO: 访问抢购订单结算页面...
2022-12-26 20:15:02,064 INFO: 生成提交抢购订单所需参数...
2022-12-26 20:15:02,064 INFO: 获取秒杀初始化信息...
2022-12-26 20:15:02,254 INFO: 提交抢购订单...
2022-12-26 20:15:02,505 INFO: 抢购成功，订单号:***, 总价:**.90, 电脑端付款链接:https://sko.jd.com/success/success.action?orderId=xx
```
## 主要功能

- 登陆京东商城（[www.jd.com](http://www.jd.com/)）
  - cookies登录 (需要自己手动获取)
- 预约商品
  - 定时自动预约
- 秒杀预约后等待抢购的商品
  - 定时开始自动抢购

## 运行环境

- [Python 3](https://www.python.org/)

## 第三方库

- [Requests](http://docs.python-requests.org/en/master/)

## 使用教程

程序主入口在 `main.py`

在config.ini文件填入config里面对应的内容
eid,和fp找个普通商品随便下单,然后抓包就能看到,这两个值可以填固定的(在京东订单结算页面，F12 console里面输入`_JdTdudfp`就会返回一个json对象，里面就有)
cookies_string,sku_id,DEFAULT_USER_AGENT(和cookie获取同一个地方就会看到.直接复制进去就可以了),以上都是必填的.

启动时按照提示操作输入需要的功能即可

## 更新记录


## 备注

- 使用的时候需要注意一下本机的时间是否和标准时间是一致的，一开始我用的wsl来跑， 结果发现wsl和windows的时间不同步，贼尴尬。