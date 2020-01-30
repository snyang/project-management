# 架构设计规范

## 责任人
开发者

## 产出物
- 技术栈
- 组件的版本记录
- 产品环境的前提需求
- 开发规范

## 架构设计点
- 软件的层次与结构
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
  - 证的许可后，才能收集个人隐私数据
  - 可以永久删除个人隐私数据
- 自动升级(upgrade)
- 授权和认证(authorization/authentication)
  - 用户和组
  - 业务功能的权限控制
  - 业务数据的权限控制（记录级）
  - 业务数据的权限控制（字段级）
  - UI上不可见
  - SDK上不可用
- 版本管理规范(version management)
- 性能(performance)
- 指数测量(instrument)
- 审核(audit)
- 日志(logging)
- 缓存(cache)
- 本地化(localization)
- 全球化(globalization)
- 适用性(accessibility)
- 单元测试(unit tests)
- 自动测试(automation tests)
- 第三方组件是否需要封装
- 检测调用弃用方法的警告

## 业务架构的设计点
- 常见的功能
- 相同的交互模式
- 跨Feature的共通性。
  如果两个Feature被两个不同开发者负责的话，任何一位开发者都有极大的可能性忽略共同的问题，而只埋头实现
- 新Feature对已有架构的影响。
- 性能关键的功能
- 关键业务分析
- 高难度的功能
