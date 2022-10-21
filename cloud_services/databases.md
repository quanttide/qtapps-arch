# 数据库

## 选型

（2022-10-22更新）计划从腾讯云TDSQL-C MySQL版迁移到PostgreSQL版。

选择PostgreSQL的主要原因是使用schema支持多租户。

## 划分和命名

一个环境使用一个实例，命名为`qtapps-<environment>`，目前有`testing`和`production`两个实例。

一个微服务使用一个数据库，命名同微服务，使用下划线代替横线，比如`qtclass_admin`。

一个租户使用一个schema。

一个Django数据模型使用一个表，一个领域模型使用一个或者多个表，由Django的migration生成。