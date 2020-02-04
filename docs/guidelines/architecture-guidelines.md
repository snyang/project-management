# 架构设计规范

## 产出物
- 开发的环境、工具、技术栈、组件、生产环境的管理
- 开发规范
- 架构设计
- 架构使用说明

## 什么是架构
> 架构 = 基础架构 + 关键的业务架构

## 基础架构设计点
- 软件的层次与结构
- 授权和认证(authorization/authentication)
  - 用户和组
  - 业务功能的权限控制
  - 业务数据的权限控制（记录级）
  - 业务数据的权限控制（字段级）
  - UI上不可见
  - SDK上不可用
- 数据访问(Data Access)
- 打印(print)
- 报表(report)
- 导入(import)
- 导出(export)
- 异常(exception)
- 安全(security)
  - 加密
  - 防止SQL注入
  - 防止代码注入
  - 不能暴露关键数据
    - 服务器的信息
    - 密码
  - 安全领域的定义
  - 可以永久删除个人隐私数据
- 性能(performance)
- 指数测量(instrument)
- 审核(audit)
- 日志(logging)
- 缓存(cache)
- 本地化(localization)
- 全球化(globalization)
- 无障碍性(accessibility)
- 异步处理(asynchronous processing)
- 并发处理(concurrent processing)
- 消息机制(message mechanism)
- 工作流(workflow)
- 用户行为跟踪(user behavior tracking)
- 用户行为分析(user behavior analysis)
- 单元测试(unit tests)
- 自动测试(automation tests)
- 第三方组件是否需要封装
- 检测调用弃用方法的警告
- 自动升级(upgrade)
- 版本管理规范(version management)
  - 产品版本
  - 文件版本
  - API的版本
  - 数据库schema的版本
  - 初始数据的版本
- 运维(Operation)
- 部署(Deployment)

## 业务架构的设计点
- 常见的功能
- 相同或相似的交互模式
- 不同特性之间的共通性。
  如果两个特性被两个不同开发者负责的话，任何一位开发者都有极大的可能性忽略共同的问题，而只埋头实现
- 新特性对已有架构的影响。
- 性能关键的功能
- 关键业务分析
- 高难度的功能
