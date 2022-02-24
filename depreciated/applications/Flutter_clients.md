# Flutter客户端架构

本文档主要介绍量潮应用体系下的Flutter应用之间的依赖关系，帮助开发者和架构师组织Flutter客户端软件工程。

根据Flutter框架提供的项目分类，量潮应用系统的Flutter项目可以分为以下三类：
- Flutter应用（Flutter Applications）：用户使用的客户端应用，包括**量潮课堂APP**、**量潮企业后台**及其子应用。
- Flutter包（Flutter Packages）：Flutter项目依赖的纯Dart包。
- Flutter插件（Flutter Plugins）：Flutter项目依赖的有原生平台（下面简称Native）代码的包。

其中，各个Flutter应用资源在相关的前后台应用项目管理，Flutter包和插件在内部公共依赖（私有）和开源项目（公开）两个管理公共依赖的项目中管理。我们只需要明确Flutter应用依赖的自建包和插件及使用的主要特性，即可建立项目之间的工程依赖关系。

以下以一个Flutter应用或者一组关联Flutter依赖为单位，介绍Flutter项目之间的依赖关系。

## 量潮课堂APP

前台应用。

项目代码：https://quanttide.coding.net/p/qtclass-app/d/qtclass-client-flutter/git
依赖自建项目：
- 量潮用户SDK
- 视频播放器SDK


## 量潮企业后台

后台应用。


## 量潮用户SDK

私有依赖。尚未创建项目。


## 视频播放器SDK

开源依赖。系列项目文档：https://quanttide.coding.net/p/opensource/wiki/7。

从顶层至底层依次为：
1. 腾讯云云点播视频播放器：https://quanttide.coding.net/p/opensource/d/qcloud-vod-player-flutter/git
2. 视频点播组件库：https://quanttide.coding.net/p/opensource/d/video-on-demand-flutter/git
3. 视频播放器桌面端：https://quanttide.coding.net/p/opensource/d/video-player-desktop-flutter/git

其中云点播SDK可能依赖自建的加解密算法库（尚未创建项目）。