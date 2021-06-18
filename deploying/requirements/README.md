# 公共依赖

## 可选方案

- Git子模块：更及时，适合管理需要反复迭代的重要依赖（i.e. Auth类）。可以利用子母项目的一些机制同步公共依赖的迭代进展。
- 私有仓库：更低耦合，适合管理工具包和成熟的依赖。

## 基于Git子模块的渐进式拆分依赖

对于已有应用，尝试此演进式方案：
1. 根据项目本身的情况在本项目内分模块管理；
2. 为此模块创建一个新Git仓库，用Git子模块管理原项目内的子项目；
3. 成熟以后以私有仓库的方式引入，和原项目彻底解耦。

举个例子：
1. Django课堂服务（业务方）创建qtauth应用，或者用户服务（验证方）创建；
2. qtauth注册为子模块，创建一个新的Git仓库管理，例如django-qtauth；
3. qtauth开发成熟以后解耦。

## 用制品库管理公共依赖

我们的公共依赖主要存在两个项目：
- 本项目，一般都是私有仓库，对团队内部可拉取、项目内部可推送；
- 开源项目，一般都是开源项目，对所有人可拉取、项目内部可以推送；

这两个项目一般会放几乎所有人，所以基本不存在内部访问限制问题；此外，外包项目主要在数据服务项目里，制品库放在这里就可以。
- 团队级制品库方案详见：https://help.coding.net/docs/artifacts/practices/team-share.html；
- 权限控制详见：https://help.coding.net/docs/artifacts/permission.html。

在相关流程尚未跑通之前，可以先把**代码仓库开源**，使用Git下载的方式下载Python依赖或者Flutter依赖，作为**临时解决方案**。

### Django服务端项目

使用pypi制品库：https://help.coding.net/docs/artifacts/quick-start/pypi.html

### Flutter客户端项目

使用Generic制品库：https://help.coding.net/docs/artifacts/quick-start/generic.html




