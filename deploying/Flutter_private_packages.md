# Flutter私有依赖打包

## 备选方案

- （优先）Git地址公开访问，最简单但有一定的安全隐患。可以暂时先用着等待新方案。
- Git子模块，可行但有使用门槛。这就完全脱离了Flutter的限制，但同样对于开发者有一定的使用门槛。
- SSH，可以但有使用门槛。官方明确支持， https://dart.dev/tools/pub/dependencies#git-packages ；注意需要注意以ssh协议访问， https://stackoverflow.com/questions/54565354/。how-to-access-private-repo-packages-in-flutter-using-ssh ；Coding也支持SSH密钥。主要问题是SSH对开发者使用门槛比较高，需要开发者在本地进行一系列配置以后才可以使用私有库，相对比较麻烦。
- （优先）Deploy Token，不一定可行但优雅。需要和Coding确认是否有相关feature，不一定现在能用；还需要确定Flutter框架有没有管理密钥的方法。
- 本地打包，可行且安全但流程破碎。 https://dart.dev/tools/pub/dependencies#path-packages 
- （优先）制品库，不一定可行但简单。不确定是否可以托管Flutter包，看Coding的支持目前不像有，自己搭私有仓库有一定成本，已经问Coding确认了。
- 自建私有Pub仓库，可行但性价比低。效果约等于Git地址公开访问，还需要自建和维护仓库，性价比比较低。


## 暂定方案及流程

Git地址公开访问。

具体操作步骤见：https://dart.dev/tools/pub/dependencies#git-packages。