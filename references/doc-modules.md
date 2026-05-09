# DrissionPage 文档模块完整映射

本文档提供 DrissionPage 官方文档的完整模块列表和 URL 映射，用于快速定位所需文档。

## 目录
- [核心模块](#核心模块)
- [高级功能](#高级功能)
- [工具和辅助](#工具和辅助)
- [URL 构建规则](#url-构建规则)

---

## 核心模块

### 浏览器控制
| 模块 | URL | 主要内容 |
|------|-----|----------|
| 入门介绍 | https://www.drissionpage.cn/browser_control/intro | 基本概念、安装、快速开始 |
| 页面对象 | https://www.drissionpage.cn/browser_control/page | ChromiumPage、WebPage 类 |
| 浏览器配置 | https://www.drissionpage.cn/browser_control/config | ChromiumOptions、启动参数 |
| 页面导航 | https://www.drissionpage.cn/browser_control/navigation | get()、back()、forward()、refresh() |

### 元素操作
| 模块 | URL | 主要内容 |
|------|-----|----------|
| 元素定位 | https://www.drissionpage.cn/browser_control/element | ele()、eles()、定位器语法 |
| 元素交互 | https://www.drissionpage.cn/browser_control/interaction | click()、input()、hover() |
| 元素属性 | https://www.drissionpage.cn/browser_control/attributes | text、html、attrs、property |

### 表单和输入
| 模块 | URL | 主要内容 |
|------|-----|----------|
| 表单操作 | https://www.drissionpage.cn/browser_control/form | 输入框、下拉框、复选框、单选框 |
| 文件上传 | https://www.drissionpage.cn/browser_control/upload | input[type=file] 处理 |

---

## 高级功能

### 标签页和窗口
| 模块 | URL | 主要内容 |
|------|-----|----------|
| 标签页管理 | https://www.drissionpage.cn/browser_control/tabs | 新建、切换、关闭标签页 |
| 多窗口处理 | https://www.drissionpage.cn/browser_control/windows | 窗口句柄、弹窗处理 |

### 等待和同步
| 模块 | URL | 主要内容 |
|------|-----|----------|
| 等待机制 | https://www.drissionpage.cn/browser_control/wait | wait.ele_displayed()、超时设置 |
| 页面加载 | https://www.drissionpage.cn/browser_control/loading | 加载状态检测、load_start() |

### JavaScript
| 模块 | URL | 主要内容 |
|------|-----|----------|
| JS 执行 | https://www.drissionpage.cn/browser_control/javascript | run_js()、run_js_loaded() |
| JS 注入 | https://www.drissionpage.cn/browser_control/injection | 页面脚本注入 |

### 下载和资源
| 模块 | URL | 主要内容 |
|------|-----|----------|
| 下载管理 | https://www.drissionpage.cn/browser_control/download | 下载设置、下载监控 |
| 资源拦截 | https://www.drissionpage.cn/browser_control/intercept | 请求拦截、响应修改 |

---

## 工具和辅助

### 混合模式
| 模块 | URL | 主要内容 |
|------|-----|----------|
| 混合模式 | https://www.drissionpage.cn/browser_control/mixed_mode | Chromium + requests 混合使用 |
| 模式切换 | https://www.drissionpage.cn/browser_control/mode_switch | change_mode() |

### 调试和工具
| 模块 | URL | 主要内容 |
|------|-----|----------|
| 调试工具 | https://www.drissionpage.cn/browser_control/debug | 截图、日志、调试模式 |
| 性能优化 | https://www.drissionpage.cn/browser_control/performance | 无头模式、资源禁用 |

---

## URL 构建规则

DrissionPage 文档遵循以下 URL 模式：

```
https://www.drissionpage.cn/<分类>/<模块名>
```

**常见分类：**
- `browser_control` - 浏览器控制相关
- `session_mode` - Session 模式相关
- `api` - API 参考
- `guide` - 使用指南

**查询策略：**
1. 确定功能所属分类（大多数在 `browser_control`）
2. 根据功能关键词推断模块名（通常是英文小写，用下划线分隔）
3. 构建完整 URL 并访问
4. 如果 404，尝试从主站导航或搜索

**示例：**
- 需要查询"如何点击元素" → `browser_control/interaction`
- 需要查询"如何配置代理" → `browser_control/config`
- 需要查询"如何等待元素" → `browser_control/wait`
