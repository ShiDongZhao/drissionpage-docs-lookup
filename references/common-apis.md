# DrissionPage 常用 API 速查表

本文档提供 DrissionPage 最常用的 API 快速参考，用于快速查找常见操作的方法名和基本用法。

## 目录
- [页面对象初始化](#页面对象初始化)
- [页面导航](#页面导航)
- [元素定位](#元素定位)
- [元素操作](#元素操作)
- [等待机制](#等待机制)
- [标签页管理](#标签页管理)
- [JavaScript 执行](#javascript-执行)

---

## 页面对象初始化

### ChromiumPage
```python
from DrissionPage import ChromiumPage

# 基本初始化
page = ChromiumPage()

# 使用配置初始化
from DrissionPage import ChromiumOptions
options = ChromiumOptions()
options.headless(True)
page = ChromiumPage(options)
```

**文档链接：** https://www.drissionpage.cn/browser_control/page

---

## 页面导航

| 方法 | 说明 | 示例 |
|------|------|------|
| `get(url)` | 访问 URL | `page.get('https://example.com')` |
| `back()` | 后退 | `page.back()` |
| `forward()` | 前进 | `page.forward()` |
| `refresh()` | 刷新 | `page.refresh()` |
| `url` | 获取当前 URL | `current_url = page.url` |
| `title` | 获取页面标题 | `title = page.title` |

**文档链接：** https://www.drissionpage.cn/browser_control/navigation

---

## 元素定位

### 定位单个元素
```python
# CSS 选择器
ele = page.ele('css:#button')
ele = page.ele('#button')

# XPath
ele = page.ele('xpath://button[@id="submit"]')

# 文本定位
ele = page.ele('text:提交')
ele = page.ele('text=提交')  # 精确匹配

# 属性定位
ele = page.ele('@id=button')
```

### 定位多个元素
```python
# 返回元素列表
eles = page.eles('css:.item')
eles = page.eles('.item')
```

### 链式定位
```python
# 在元素内部继续定位
container = page.ele('#container')
button = container.ele('.button')
```

**文档链接：** https://www.drissionpage.cn/browser_control/element

---

## 元素操作

### 点击和输入
| 方法 | 说明 | 示例 |
|------|------|------|
| `click()` | 点击元素 | `ele.click()` |
| `input(text)` | 输入文本 | `ele.input('hello')` |
| `clear()` | 清空输入框 | `ele.clear()` |
| `hover()` | 鼠标悬停 | `ele.hover()` |

### 获取信息
| 属性/方法 | 说明 | 示例 |
|-----------|------|------|
| `text` | 获取文本 | `text = ele.text` |
| `html` | 获取 HTML | `html = ele.html` |
| `attr(name)` | 获取属性 | `href = ele.attr('href')` |
| `attrs` | 获取所有属性 | `attrs = ele.attrs` |
| `value` | 获取表单值 | `val = ele.value` |

### 状态检查
| 方法 | 说明 | 示例 |
|------|------|------|
| `is_displayed()` | 是否可见 | `if ele.is_displayed():` |
| `is_enabled()` | 是否可用 | `if ele.is_enabled():` |
| `is_selected()` | 是否选中 | `if ele.is_selected():` |

**文档链接：** https://www.drissionpage.cn/browser_control/interaction

---

## 等待机制

### 等待元素
```python
# 等待元素出现
page.wait.ele_displayed('#button')

# 等待元素消失
page.wait.ele_hidden('#loading')

# 等待元素可点击
page.wait.ele_clickable('#submit')

# 设置超时时间（秒）
page.wait.ele_displayed('#button', timeout=10)
```

### 等待页面加载
```python
# 等待页面加载开始
page.wait.load_start()

# 等待页面加载完成
page.wait.load_complete()
```

**文档链接：** https://www.drissionpage.cn/browser_control/wait

---

## 标签页管理

| 方法 | 说明 | 示例 |
|------|------|------|
| `new_tab(url)` | 新建标签页 | `page.new_tab('https://example.com')` |
| `close_tab()` | 关闭当前标签页 | `page.close_tab()` |
| `get_tab(index)` | 切换到指定标签页 | `page.get_tab(1)` |
| `tabs` | 获取所有标签页 | `tabs = page.tabs` |
| `tab_count` | 标签页数量 | `count = page.tab_count` |

**文档链接：** https://www.drissionpage.cn/browser_control/tabs

---

## JavaScript 执行

```python
# 执行 JavaScript
result = page.run_js('return document.title')

# 执行带参数的 JS
result = page.run_js('return arguments[0] + arguments[1]', 1, 2)

# 在元素上执行 JS
ele.run_js('this.style.border = "2px solid red"')
```

**文档链接：** https://www.drissionpage.cn/browser_control/javascript

---

## 表单操作

### 输入框
```python
input_ele = page.ele('#username')
input_ele.input('myusername')
input_ele.clear()
```

### 下拉框
```python
select_ele = page.ele('select#country')
select_ele.select('China')  # 按文本选择
select_ele.select.by_value('cn')  # 按值选择
select_ele.select.by_index(0)  # 按索引选择
```

### 复选框和单选框
```python
checkbox = page.ele('input[type="checkbox"]')
checkbox.click()  # 切换状态
is_checked = checkbox.is_selected()
```

**文档链接：** https://www.drissionpage.cn/browser_control/form

---

## 配置选项

### ChromiumOptions 常用配置
```python
from DrissionPage import ChromiumOptions

options = ChromiumOptions()

# 无头模式
options.headless(True)

# 设置代理
options.set_proxy('http://proxy.example.com:8080')

# 设置用户数据目录
options.set_user_data_path('path/to/user_data')

# 禁用图片加载
options.set_argument('--blink-settings=imagesEnabled=false')

# 设置窗口大小
options.set_window_size(1920, 1080)
```

**文档链接：** https://www.drissionpage.cn/browser_control/config

---

## 查询建议

当需要查询具体 API 时：
1. 先在本速查表中查找常用方法
2. 如果找不到，根据功能类别访问对应的文档链接
3. 使用文档站内搜索功能查找特定方法
4. 参考文档中的完整示例代码
