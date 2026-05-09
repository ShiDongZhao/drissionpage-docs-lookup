---
name: drissionpage-docs-lookup
description: 在编写 DrissionPage 代码时查询最新的官方文档。适用于需要获取 DrissionPage 浏览器控制、元素操作、配置等最新 API 和使用方法的场景。包含文档地址、常用模块和查询策略。
---

# DrissionPage 文档查询技能

## 何时使用此技能

在以下场景中使用此技能：
- 编写或调试 DrissionPage 相关代码时
- 需要查询 DrissionPage 的最新 API 用法
- 不确定某个功能的正确使用方法
- 文档可能已更新，需要获取最新信息
- 需要了解浏览器控制、元素操作、配置选项等

## 何时不使用此技能

以下情况不应使用此技能：
- 处理其他 Python 库或框架（使用对应的文档查询方法）
- 已经明确知道 API 用法且不需要验证
- 项目不涉及 DrissionPage

## DrissionPage 官方文档

**主站：** https://www.drissionpage.cn/

**核心文档模块：**
- 浏览器控制入门：https://www.drissionpage.cn/browser_control/intro
- 元素操作：https://www.drissionpage.cn/browser_control/element
- 页面对象：https://www.drissionpage.cn/browser_control/page
- 配置选项：https://www.drissionpage.cn/browser_control/config
- 等待与超时：https://www.drissionpage.cn/browser_control/wait
- 标签页管理：https://www.drissionpage.cn/browser_control/tabs
- 表单操作：https://www.drissionpage.cn/browser_control/form
- JavaScript 执行：https://www.drissionpage.cn/browser_control/javascript
- 下载管理：https://www.drissionpage.cn/browser_control/download
- 混合模式：https://www.drissionpage.cn/browser_control/mixed_mode

## 工作流程

### 1. 识别需求
确定用户需要查询的具体功能或模块：
- 浏览器启动和配置
- 元素定位和操作
- 页面导航和交互
- 表单填写和提交
- JavaScript 执行
- 文件下载
- 其他特定功能

### 2. 构建查询策略
根据需求选择合适的文档页面：
- **基础操作** → 从浏览器控制入门开始
- **元素相关** → 查询元素操作文档
- **配置问题** → 查询配置选项文档
- **性能优化** → 查询等待与超时文档
- **多标签页** → 查询标签页管理文档

### 3. 获取最新文档
使用 web 相关工具访问对应的文档页面：
```
访问 https://www.drissionpage.cn/browser_control/<模块名>
```

### 4. 提取关键信息
从文档中提取：
- API 方法签名和参数
- 使用示例代码
- 注意事项和最佳实践
- 版本要求和兼容性说明

### 5. 应用到代码
将获取的最新用法应用到用户的代码中：
- 使用正确的导入语句
- 遵循文档中的参数格式
- 参考示例代码结构
- 注意错误处理

## 常见使用场景示例

### 场景 1：初始化浏览器
**需求：** 用户想要启动一个 Chrome 浏览器实例
**查询：** 访问浏览器控制入门文档
**关键点：** ChromiumPage 类的初始化参数、配置选项

### 场景 2：元素定位
**需求：** 用户需要定位页面上的特定元素
**查询：** 访问元素操作文档
**关键点：** 定位器语法、ele() 和 eles() 方法、CSS 选择器和 XPath

### 场景 3：表单填写
**需求：** 用户需要自动填写表单
**查询：** 访问表单操作文档
**关键点：** input() 方法、select 选择、checkbox 操作

### 场景 4：等待元素加载
**需求：** 用户需要等待动态内容加载
**查询：** 访问等待与超时文档
**关键点：** wait.ele_displayed()、wait.load_start() 等方法

## 故障排除

### 文档无法访问
- 检查网络连接
- 尝试访问主站 https://www.drissionpage.cn/
- 如果主站可访问但特定页面不可访问，可能是文档结构调整，尝试从主站导航

### API 用法与文档不符
- 确认 DrissionPage 版本（文档通常针对最新版本）
- 检查是否有版本说明或迁移指南
- 考虑升级到最新版本

### 找不到特定功能
- 使用文档站内搜索功能
- 查看 API 参考或完整方法列表
- 检查是否在其他相关模块中

## 参考文件

详细的文档模块映射和查询策略，请参阅：
- [`references/doc-modules.md`](references/doc-modules.md) - 完整的文档模块列表和 URL 映射
- [`references/common-apis.md`](references/common-apis.md) - 常用 API 速查表

## 注意事项

1. **文档时效性：** DrissionPage 文档更新较快，始终优先使用在线文档而非缓存信息
2. **版本兼容性：** 注意文档中的版本说明，确保代码与安装的版本兼容
3. **示例代码：** 文档中的示例代码是最佳实践，建议直接参考
4. **中文文档：** DrissionPage 提供中文文档，无需翻译
