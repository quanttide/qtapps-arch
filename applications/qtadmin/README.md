# 量潮企业后台

## 子应用体系

业务数据库后台：
- 连接到各个服务暴露的Admin接口。

内部管理流程：
- [人力资源工作流](./hr_workflow/README.md)
  - [面试工作流](./hr_workflow/interview.md) 
- [财务工作流](./finance_workflow.md)
- [自媒体工作流](./media_workflow.md)

## 技术选型

- 服务端：Django
- 客户端：Flutter，在现有Flutter版本的后台管理系统框架的基础上做二次开发。