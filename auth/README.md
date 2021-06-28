# 量潮用户认证和权限体系

本部分文档统一说明系统层面的用户认证（Auth）和用户权限（Permission）机制。

本部分文档的主要目标阅读用户是架构师，用以帮助架构师理解整个系统层面的用户认证和权限的设计逻辑。负责前后台的工程师们只需要关注各个项目的接入目标、方式和API即可，通常在各个项目自己的文档里，整体思路在本文档的前台和后台应用部分；负责中台的工程师主要关注各个中台服务和公共依赖项目的实现思路，即关注中台部分和公共依赖部分。


## 相关项目

生产者：中台服务
- [用户服务（qtuser-server-django）](../middle-end/qtuser/README.md)：提供用户信息和认证的OpenAPI。

消费者：语言和框架级插件
- [Django用户认证库（django-qtauth）](../requirements/django/django-qtauth/README.md)：为Django服务提供开箱即用的用户认证和权限SDK。
- [Flutter用户组件库的认证模块（qtuser-flutter）](../requirements/flutter/qtuser-flutter/auth.md)：为Flutter应用提供开箱即用的客户端用户认证和权限SDK。