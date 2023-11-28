# 数据云

## 数据集管理

### 动机

- 统一表达结构化和半结构化数据，用以打通人工标记和代码处理流程。
- 抽象出业务意义的单元，以方便统一流程的语言、进而方便编排和DataOps。

### 数据记录

主要被[`records`库](https://pypi.org/project/records/)和[`dataset`库](https://dataset.readthedocs.io/en/latest/)启发，提供统一的读写和转换接口。

一种可能的路线是参考JSON（或者YAML）的格式统一的半结构化数据。

## 数据编排

### 数据工作流

例如：

爬虫1（Python） -> 爬虫2 -> 人工标记（Flutter全平台/Web应用 -> Django） -> 交叉验证（Python） - (交付) -> 预处理(R) -> 计量模型(Stata) -> 可视化（Stata/Excel）


