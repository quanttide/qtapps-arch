# GitLab Workflow

基于GitLab Workflow的旧方案（供新方案参考）：
1. PyCharm直接运行Django服务通过。
    - 环境变量以.env的形式配置，通过PyCharm插件配置给本地环境
2. 上传本地代码到代码仓库，对master进行构建和部署测试。
    - 环境变量.env和.env.dev复制黏贴到构建任务中
3. 合并上一步代码到pre-production分支，对其进行构建部署测试。
    - 环境变量.env复制黏贴到构建任务的环境变量中，从本Wiki中取出预生产环境配置复制黏贴
4. 合并上一步代码到production分支，对其进行构建部署测试。  
    - 同上一步
