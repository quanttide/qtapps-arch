# Flutter客户端架构

## 分层

为了让开发者更方便地复用已有积累，我们把Flutter的组件库从底层到底层分为以下四层：

1. 应用内组件：Flutter应用内根据需求自定义的组件，通常维护在`lib/widgets`文件夹下。
2. 量潮组件：量潮设计语言指导下的组件及其风格，实现在开源项目部设计工程组负责维护的[`quanttide_design`](https://pub.dev/packages/quanttide_design)库。
3. 社区组件：官方组件、社区组件库和开源项目部Flutter组负责维护的自建开源组件库，相关实践在[量潮Flutter手册](https://quanttide.coding.net/public/quanttide-handbooks/quanttide-handbook-on-flutter/git/files)维护。
