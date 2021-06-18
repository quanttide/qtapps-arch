# 设备服务

## 使用场景

- 在微信支付服务里需要根据设备情况自定确定微信支付类型。


## 标签类型

### 操作系统定义

可以通过解析UA获取，Python有相关库可以处理。
- 操作系统：iOS，Android，macOS，Windows
- 设备类型：Mobile，Tablet，Desktop
- 渲染类型：Native，Web（浏览器）

### 框架定义

- Flutter类型：iOS，Android，Web，macOS，Windows
- 微信类型：native，APP，H5，etc
- 自定义类型（QtDeviceLabel）：根据内部系统需求定义。

## 参考资料

设备唯一性识别可以参考：https://cloud.tencent.com/developer/article/1475342

