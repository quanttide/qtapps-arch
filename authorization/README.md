---
title: 量潮用户鉴权机制
author: 张果
date: 2021-08-09
---

# 量潮用户鉴权机制

本部分文档统一说明系统层面的用户鉴权（Authorization）机制。

## 架构设计原则

使用标准鉴权协议通信，基于标准协议的自定义用户信息字段自定义权限验证规则。

## 鉴权服务端

使用腾讯云的数字身份管控平台（IDAM）的公众版（CIAM）和员工版（EIAM）作为鉴权服务端。详见：
- 公众版：https://cloud.tencent.com/document/product/1441
- 员工版：https://cloud.tencent.com/document/product/1442

使用基于OAuth2和OpenID Connect标准协议的鉴权服务端API实现鉴权功能。通过拓展协议标准定义的claims实现自定义权限验证规则。

## 鉴权客户端

在DRF框架下包括用户认证（Authentication）和用户权限（Permission）两个部分。鉴权客户端的Django插件分为这两层设计：
- 协议层：`Authentication`类负责根据标准协议鉴权和解析用户信息。
- 框架层：`Permission`类按照Django框架提供的规范设计。

两层之间的转换通过`Model`类和`Serializer`类，`Authentication`类解析服务端设置的用于鉴权的claims，`Permission`类基于自定义的使用规则验证权限。
