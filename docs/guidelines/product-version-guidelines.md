# 流程：产品版本管理

## 产品的发布类型
主要有3种:
- 主版本
  包含新的特性和缺陷修正。
- Fix Pack
  包含一些缺陷修正。一般定期发布
- Hotfix
  针对数据、安全等方面问题的修正。

> 我们需要将每一次发布都当成一个项目来对待。

## 产品版本号
四段版本号: `<Major>.<Minor>.<Fix Pack>.<Hot Fix>`。
产品版本号会作为数据部署到生成环境的文件或者数据库中。

## Build版本号
三段版本号: `<Major>.<Minor>.<Build>`。
四段版本号: `<Major>.<Minor>.<Fix Pack>.<Build>`。
五段版本号：`<Major>.<Minor>.<Fix Pack>.<Hot Fix>.<Build>`。

Build版本号一般会作为文件版本信息。