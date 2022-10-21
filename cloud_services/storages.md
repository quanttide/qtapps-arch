# 存储

## 选型

使用腾讯云对象存储。

## 划分和命名

一个微服务使用一个存储桶。

存储桶命名为`<service>-<env>`，比如`qtclass-admin-dev`。由于存储桶名称限制在20个字符，因此环境标签使用简写。可选`dev`、`test`、`prod`，再不够可以使用`d`、`t`、`p`。

存储桶标签为`qtapps:<service>`和`env:<environment>`。
