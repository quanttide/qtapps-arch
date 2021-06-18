# Flutter私有依赖打包

## 初步方案及流程

方案：访问Git公开仓库。

步骤：
1. Coding设置项目访问为“公开”，并获取公开访问地址。
2. 在Flutter项目的`pubspec.yaml`文件设置Git下载，详见：https://dart.dev/tools/pub/dependencies#git-packages。


## 备选方案

- （优先）Git地址公开访问，最简单但有一定的安全隐患。可以暂时先用着等待新方案。
- Git子模块，可行但有使用门槛。这就完全脱离了Flutter的限制，但同样对于开发者有一定的使用门槛。
- SSH，可以但有使用门槛。官方明确支持， https://dart.dev/tools/pub/dependencies#git-packages ；注意需要注意以ssh协议访问， https://stackoverflow.com/questions/54565354/how-to-access-private-repo-packages-in-flutter-using-ssh ；Coding也支持SSH密钥。主要问题是SSH对开发者使用门槛比较高，需要开发者在本地进行一系列配置以后才可以使用私有库，相对比较麻烦。
- Deploy Token，不可行但优雅。具体方案为：https://medium.com/flutter-community/flutter-pubspec-and-private-gitlab-repositories-d092a4648639；Coding可以使用个人令牌（https://help.coding.net/docs/member/tokens.html#利用令牌访问代码仓库）实现；Flutter框架不支持给pubspec.yaml注入环境变量且官方不打算支持（https://github.com/dart-lang/pub/issues/1358）。
- 本地打包，可行且安全但流程破碎。 https://dart.dev/tools/pub/dependencies#path-packages 
- 制品库，不可行。Coding暂不支持。
- 自建私有Pub仓库，可行但性价比低。效果约等于Git地址公开访问，还需要自建和维护仓库，性价比比较低。
