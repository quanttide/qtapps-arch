# 量潮用户鉴权体系

[//]: （2021-08-09）从项目里复制，还未维护。

本部分文档统一说明系统层面的用户鉴权（Authorization）机制。在DRF框架下包括用户认证（Authentication）和用户权限（Permission）两个部分。

本部分文档的主要目标阅读用户是架构师，用以帮助架构师理解整个系统层面的用户认证和权限的设计逻辑。负责前后台的工程师们只需要关注各个项目的接入目标、方式和API即可，通常在各个项目自己的文档里，整体思路在本文档的前台和后台应用部分；负责中台的工程师主要关注各个中台服务和公共依赖项目的实现思路，即关注中台部分和公共依赖部分。

## 相关项目

生产者：中台服务
- [用户服务（qtuser-server-django）](../middle-end/qtuser/README.md)：提供用户信息和认证的OpenAPI。

消费者：语言和框架级插件
- [DRF微服务鉴权库（drf-remote-auth）](../requirements/django/django-qtauth/README.md)：为DRF服务提供开箱即用的用户鉴权。
- [Flutter用户组件库的认证模块（qtuser-flutter）](../requirements/flutter/qtuser-flutter/auth.md)：为Flutter应用提供开箱即用的客户端用户鉴权。

## 实现思路

### Authentication和Permission

遵循"Global Authentication, Local Permission"的思路。简单地说，`Authentication`发送到统一用户鉴权服务验证（使用Token时有可能把验证放在本地，但Global层面看起来依然是统一的），`Permission`通过本地代码规定权限。

对于Django，Auth使用自定义Auth类，实现思路见官方文档：https://www.django-rest-framework.org/api-guide/authentication/；Permission使用自定义Permission类，实现思路见官方文档：https://www.django-rest-framework.org/api-guide/permissions/。将会以 “Django公共依赖”的`django_qtauth`包实现以上自定义Auth类和Permission类，在其他服务中接入使用，以`qtuser`服务提供Auth服务。

对于各个服务的权限控制问题如下：
- 前中台应用：IsAuthenticationed即可，部分API需要AnyAllowed。
- 后台应用：默认IsStaff即可，不同的子应用需要授权拥有Staff身份用户的一部分。
  - 财务平台：授权管理层和财务部。
  - 法务平台：授权管理层和法务部，必要时授权业务部门、人力资源部门、财务部不同的访问权限。
  - 人力资源平台：授权管理层和人力资源部门，必要授权业务负责人。

后台应用的权限控制需要细粒度更高的方案，DRF的Permission类一般对API控制，也可能需要考虑Django原生的用户级Permission控制（https://docs.djangoproject.com/en/3.1/topics/auth/），或者DRF的Object-level权限控制方案（https://www.django-rest-framework.org/api-guide/permissions/#djangoobjectpermissions）。

## 具体实现

由于计划使用腾讯云的数字身份管控平台（IDAM）的公众版（CIAM）和员工版（EIAM）作为用户鉴权服务，原设计的用户服务（qtuser）计划整体冻结，drf-remote-auth也因此改变方向。本项目计划分为以下几层：
- 协议层：Authentication类负责根据标准协议鉴权和解析用户信息。
- Django层：Models、Serializers、Permission按照Django规范设计。

目前Authentication类有两种方向：
1. 定制Django腾讯云SDK，即为CIAM和EIAM分别实现Authentication类。这样就必须要使用两个库，而且需要考虑两个库之间的兼容性问题；当然也可以干脆把drf-remote-auth合并到IDAM模块，整体放弃掉drf-remote-auth目前的代码，这样的长期结果是我们和腾讯云更加深度绑定，需要决定是不是把这条路继续走到黑。
2. 重构开源社区代码到drf-remote-auth。这套路目前的思路已经乱了，看起来似乎并不太可行。

由于技术方向无法确定，此项目必须要暂停讨论清楚。

## 参考资料

### 社区Authentication

可以用于qtclass初步接入CIAM或EIAM使用以完成初期迭代。
- OAuth2：https://github.com/jpadilla/django-rest-framework-oauth/
- OIDC：https://github.com/ByteInternet/drf-oidc-auth

### 协议Python实现

计划使用authlib库、放弃oauthlib。总体来说authlib的标准协议实现地更加全面，主要缺点是文档不清楚、需要从上述代码或者authlib源码里搞清楚API和用法。

https://docs.authlib.org/en/latest/index.html

### 标准协议

- OAuth2: https://datatracker.ietf.org/doc/html/rfc6749
- OIDC：https://openid.net/connect/

### 腾讯云IDAM

- 公众版：https://cloud.tencent.com/document/product/1441/54960
- 员工版：https://console.cloud.tencent.com/eiam

