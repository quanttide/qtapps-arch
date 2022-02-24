# 容器化Web服务

基本等同于Docker容器化部署，后续容器调度流程由云托管内部实现。

Docker容器化部署Django项目过程详见，https://www.dusaiphoto.com/article/76/。

部署流程中作为脚手架已经无需进行的步骤：
- 本地打包Docker。速度太慢，打包了也不可以直接在本地使用。
- 直接上传到云托管。速度同样比较慢，并且不方便复用配置的环境变量，Coding的CI流程可以代替。

