# drissionpage-docs-lookup

一个面向 DrissionPage 的文档查询与速查仓库，用于在编写、调试或审查 DrissionPage 自动化代码时，快速定位官方文档、常用 API 和基础示例。

## 项目简介

本仓库围绕 **DrissionPage 官方文档查询** 这一目标进行整理，适合以下场景：

- 编写 DrissionPage 自动化脚本时，快速确认 API 用法
- 调试浏览器控制、元素定位、等待机制等相关代码时查找最新说明
- 在团队内部沉淀一份更容易上手的中文参考资料
- 为 AI Agent、自动化工具或个人知识库提供结构化文档索引

仓库中的内容主要包括：

- 技能定义说明
- 官方文档模块映射
- 常用 API 速查表
- 一份较完整的基础使用指南

## 适用对象

- 初学 DrissionPage 的开发者
- 需要快速回忆 API 的自动化测试工程师
- 维护 DrissionPage 相关脚本的 Python 开发者
- 希望为 AI/Agent 提供文档检索上下文的使用者

## 仓库结构

```text
.
├── SKILL.md
├── DrissionPage基础使用指南.md
├── references/
│   ├── common-apis.md
│   └── doc-modules.md
└── LICENSE
```

### 文件说明

- `SKILL.md`
  - 定义本仓库的核心用途、使用时机、查询流程和参考入口。
  - 适合 AI Agent 或使用者快速理解“何时查、查什么、怎么查”。

- `DrissionPage基础使用指南.md`
  - 提供从安装、页面访问、元素定位、元素操作到等待、表单、标签页、配置等内容的基础说明。
  - 适合作为入门文档和常见场景参考。

- `references/common-apis.md`
  - 汇总高频 API 的简明速查内容。
  - 适合在编码过程中快速翻阅。

- `references/doc-modules.md`
  - 整理 DrissionPage 官方文档模块与 URL 的对应关系。
  - 适合快速跳转到目标官方页面。

## 核心能力

本仓库重点覆盖以下 DrissionPage 常见能力：

- 浏览器启动与页面对象初始化
- 页面访问与导航控制
- 元素定位与链式查找
- 点击、输入、清空、属性读取等元素操作
- 等待机制与页面同步
- 标签页管理
- JavaScript 执行
- 表单处理
- ChromiumOptions 常见配置

## 使用方式

### 1. 作为文档索引仓库使用

如果你只是想快速查资料，可以按下面顺序使用：

1. 先阅读 `references/common-apis.md`，确认是否能直接找到所需方法
2. 如果需要更完整的说明，查看 `DrissionPage基础使用指南.md`
3. 如果需要跳转官方文档，使用 `references/doc-modules.md` 中的 URL 映射
4. 如果要了解本仓库整体定位和检索策略，查看 `SKILL.md`

### 2. 作为 AI Agent 的技能资料使用

如果你在为 AI Agent、自动化助手或内部知识系统提供 DrissionPage 文档支持，本仓库可作为一个轻量知识包使用。

建议流程：

1. 从 `SKILL.md` 中读取技能描述和使用边界
2. 根据用户问题判断属于哪个模块，例如：
   - 页面对象
   - 元素定位
   - 表单操作
   - 等待机制
   - 标签页管理
3. 结合 `references/doc-modules.md` 构建官方文档访问路径
4. 使用 `references/common-apis.md` 补充常见 API 快速说明
5. 必要时参考 `DrissionPage基础使用指南.md` 获取示例代码

## 推荐查询路径

当你遇到一个具体问题时，可以参考下面的查询思路：

| 场景 | 优先查看内容 |
| --- | --- |
| 不知道从哪里开始 | `DrissionPage基础使用指南.md` |
| 只想快速确认 API 名称 | `references/common-apis.md` |
| 想跳转官方文档原始页面 | `references/doc-modules.md` |
| 想了解仓库如何组织检索策略 | `SKILL.md` |

## 官方文档

DrissionPage 官方站点：

- https://www.drissionpage.cn/

常用模块入口示例：

- 浏览器控制入门：https://www.drissionpage.cn/browser_control/intro
- 页面对象：https://www.drissionpage.cn/browser_control/page
- 浏览器配置：https://www.drissionpage.cn/browser_control/config
- 元素操作：https://www.drissionpage.cn/browser_control/element
- 等待机制：https://www.drissionpage.cn/browser_control/wait
- 标签页管理：https://www.drissionpage.cn/browser_control/tabs
- JavaScript 执行：https://www.drissionpage.cn/browser_control/javascript
- 表单操作：https://www.drissionpage.cn/browser_control/form

## 适合解决的问题

你可以使用本仓库辅助解决例如以下问题：

- 如何初始化 `ChromiumPage`
- 如何使用 `ele()` / `eles()` 定位元素
- 如何等待页面或元素加载完成
- 如何填写表单、选择下拉框、处理复选框
- 如何执行 JavaScript
- 如何配置无头模式、代理、窗口大小
- 如何管理多个标签页

## 维护建议

为了保证资料可用性，建议定期进行以下维护：

- 检查官方文档链接是否仍然有效
- 根据 DrissionPage 版本更新补充示例
- 将高频问题沉淀到 `references/common-apis.md`
- 当官方文档结构变化时同步更新 `references/doc-modules.md`

## 许可证

本项目许可证请查看 `LICENSE` 文件。

## 致谢

资料主要基于 DrissionPage 官方文档整理，并结合常见使用场景进行了结构化归纳。
