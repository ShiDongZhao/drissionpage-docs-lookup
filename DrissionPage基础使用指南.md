# DrissionPage 基础使用指南

> 基于 DrissionPage 官方文档整理。当前官方文档提示适用于 DrissionPage 4.1.1.2。
>
> 官方站点：https://www.drissionpage.cn/

## 1. DrissionPage 是什么

DrissionPage 是一个 Python 网页自动化工具，常用于：

- 自动打开和控制 Chromium / Chrome 浏览器
- 自动访问网页、点击按钮、输入文本
- 定位页面元素并提取文本、链接、属性
- 处理等待、标签页、表单、截图、JavaScript 执行等任务

它的常用入口类是 `ChromiumPage`，用于控制 Chromium 内核浏览器。

---

## 2. 安装

```bash
pip install DrissionPage
```

安装完成后，可以在 Python 中导入：

```python
from DrissionPage import ChromiumPage
```

---

## 3. 最基础示例：打开网页并获取标题

```python
from DrissionPage import ChromiumPage

# 创建浏览器页面对象，会自动启动或接管浏览器
page = ChromiumPage()

# 打开网页
page.get('https://www.baidu.com')

# 获取页面标题
print(page.title)

# 获取当前网址
print(page.url)

# 关闭浏览器
page.quit()
```

---

## 4. 页面访问与导航

```python
from DrissionPage import ChromiumPage

page = ChromiumPage()

# 打开网页
page.get('https://example.com')

# 刷新页面
page.refresh()

# 后退
page.back()

# 前进
page.forward()

# 输出当前页面信息
print('标题：', page.title)
print('网址：', page.url)

page.quit()
```

常用方法：

| 方法 / 属性 | 说明 |
| --- | --- |
| `page.get(url)` | 访问指定网址 |
| `page.refresh()` | 刷新页面 |
| `page.back()` | 浏览器后退 |
| `page.forward()` | 浏览器前进 |
| `page.title` | 获取页面标题 |
| `page.url` | 获取当前网址 |

---

## 5. 元素定位

DrissionPage 使用 `ele()` 获取单个元素，使用 `eles()` 获取多个元素。

```python
# 按 id 定位
search_box = page.ele('#kw')

# 按 class 定位
button = page.ele('.btn')

# 使用 CSS 选择器
input_ele = page.ele('css:input[name="wd"]')

# 使用 XPath
link = page.ele('xpath://a[@href]')

# 按文本定位
login_btn = page.ele('text:登录')

# 获取多个元素
items = page.eles('.item')
```

常见定位写法：

| 写法 | 含义 |
| --- | --- |
| `#id值` | 通过 id 定位 |
| `.class值` | 通过 class 定位 |
| `css:选择器` | 使用 CSS 选择器 |
| `xpath:路径` | 使用 XPath |
| `text:文本` | 按文本定位 |
| `@属性名=属性值` | 按属性定位 |

---

## 6. 元素操作

```python
# 找到输入框
input_box = page.ele('#kw')

# 输入内容
input_box.input('DrissionPage')

# 清空输入框
input_box.clear()

# 找到按钮并点击
button = page.ele('#su')
button.click()

# 获取元素文本
text = button.text
print(text)

# 获取元素属性
value = button.attr('value')
print(value)
```

常用元素方法和属性：

| 方法 / 属性 | 说明 |
| --- | --- |
| `ele.click()` | 点击元素 |
| `ele.input(text)` | 输入文本 |
| `ele.clear()` | 清空输入框 |
| `ele.hover()` | 鼠标悬停 |
| `ele.text` | 获取元素文本 |
| `ele.html` | 获取元素 HTML |
| `ele.attr(name)` | 获取元素属性 |
| `ele.attrs` | 获取所有属性 |
| `ele.value` | 获取表单值 |
| `ele.is_displayed()` | 判断是否可见 |
| `ele.is_enabled()` | 判断是否可用 |
| `ele.is_selected()` | 判断是否选中 |

---

## 7. 等待页面或元素

网页自动化中，不建议完全依赖固定 `time.sleep()`，优先使用等待方法。

```python
from DrissionPage import ChromiumPage

page = ChromiumPage()
page.get('https://www.baidu.com')

# 等待搜索框显示，最多等 10 秒
page.wait.ele_displayed('#kw', timeout=10)

# 输入并点击
page.ele('#kw').input('DrissionPage')
page.ele('#su').click()

# 等待结果区域出现
page.wait.ele_displayed('#content_left', timeout=10)

print(page.title)
page.quit()
```

常用等待：

| 方法 | 说明 |
| --- | --- |
| `page.wait.ele_displayed(locator, timeout=秒数)` | 等待元素显示 |
| `page.wait.ele_hidden(locator, timeout=秒数)` | 等待元素隐藏 |
| `page.wait.ele_clickable(locator, timeout=秒数)` | 等待元素可点击 |
| `page.wait.load_start()` | 等待页面开始加载 |
| `page.wait.load_complete()` | 等待页面加载完成 |

---

## 8. 表单填写

```python
from DrissionPage import ChromiumPage

page = ChromiumPage()
page.get('https://example.com/login')

# 输入用户名和密码
page.ele('#username').input('admin')
page.ele('#password').input('123456')

# 勾选复选框
page.ele('input[type="checkbox"]').click()

# 点击提交按钮
page.ele('#submit').click()

page.quit()
```

下拉框示例：

```python
select_ele = page.ele('select#country')

# 按显示文本选择
select_ele.select('China')

# 按 value 选择
select_ele.select.by_value('cn')

# 按索引选择
select_ele.select.by_index(0)
```

---

## 9. 执行 JavaScript

```python
from DrissionPage import ChromiumPage

page = ChromiumPage()
page.get('https://example.com')

# 获取网页标题
title = page.run_js('return document.title')
print(title)

# 滚动到底部
page.run_js('window.scrollTo(0, document.body.scrollHeight)')

# 给元素加边框，方便调试
page.ele('body').run_js('this.style.border = "3px solid red"')

page.quit()
```

---

## 10. 标签页管理

```python
from DrissionPage import ChromiumPage

page = ChromiumPage()
page.get('https://example.com')

# 新建标签页
new_tab = page.new_tab('https://www.baidu.com')

# 获取所有标签页
print(page.tabs)

# 获取标签页数量
print(page.tab_count)

# 关闭当前标签页
page.close_tab()

page.quit()
```

常用方法：

| 方法 / 属性 | 说明 |
| --- | --- |
| `page.new_tab(url)` | 新建标签页 |
| `page.close_tab()` | 关闭当前标签页 |
| `page.get_tab(index)` | 获取指定标签页 |
| `page.tabs` | 获取所有标签页 |
| `page.tab_count` | 获取标签页数量 |

---

## 11. 浏览器配置

可以使用 `ChromiumOptions` 配置浏览器启动参数。

```python
from DrissionPage import ChromiumPage, ChromiumOptions

options = ChromiumOptions()

# 开启无头模式，不显示浏览器窗口
options.headless(True)

# 设置浏览器窗口大小
options.set_window_size(1920, 1080)

# 禁用图片加载，提高速度
options.set_argument('--blink-settings=imagesEnabled=false')

# 使用配置创建页面对象
page = ChromiumPage(options)

page.get('https://example.com')
print(page.title)

page.quit()
```

常用配置：

| 配置 | 说明 |
| --- | --- |
| `options.headless(True)` | 开启无头模式 |
| `options.set_proxy(proxy)` | 设置代理 |
| `options.set_user_data_path(path)` | 设置用户数据目录 |
| `options.set_window_size(width, height)` | 设置窗口大小 |
| `options.set_argument(arg)` | 添加 Chromium 启动参数 |

---

## 12. 实战示例：百度搜索并读取结果

```python
from DrissionPage import ChromiumPage

page = ChromiumPage()

try:
    # 打开百度
    page.get('https://www.baidu.com')

    # 等待搜索框出现
    page.wait.ele_displayed('#kw', timeout=10)

    # 输入关键词
    page.ele('#kw').input('DrissionPage')

    # 点击搜索按钮
    page.ele('#su').click()

    # 等待搜索结果区域显示
    page.wait.ele_displayed('#content_left', timeout=10)

    # 获取搜索结果标题
    results = page.eles('css:#content_left h3')

    for index, result in enumerate(results[:5], start=1):
        print(f'{index}. {result.text}')

finally:
    page.quit()
```

---

## 13. 实战示例：采集列表数据

```python
from DrissionPage import ChromiumPage

page = ChromiumPage()

try:
    page.get('https://example.com/products')

    # 等待商品列表加载
    page.wait.ele_displayed('.product-item', timeout=10)

    products = []
    items = page.eles('.product-item')

    for item in items:
        name = item.ele('.product-name').text
        price = item.ele('.product-price').text
        link = item.ele('a').attr('href')

        products.append({
            'name': name,
            'price': price,
            'link': link,
        })

    for product in products:
        print(product)

finally:
    page.quit()
```

---

## 14. 初学者常见问题

### 14.1 找不到元素怎么办

优先检查：

1. 选择器是否正确。
2. 元素是否在 iframe 中。
3. 元素是否需要登录后才出现。
4. 元素是否是异步加载，需要先等待。

示例：

```python
page.wait.ele_displayed('#target', timeout=10)
ele = page.ele('#target')
```

### 14.2 为什么点击没有效果

可能原因：

- 元素还没加载完成
- 元素被遮挡
- 点击的不是实际可点击元素
- 页面有前端框架异步渲染

可以先等待可点击：

```python
page.wait.ele_clickable('#submit', timeout=10)
page.ele('#submit').click()
```

### 14.3 是否一定要关闭浏览器

建议在脚本结束时调用：

```python
page.quit()
```

更稳妥的写法是使用 `try...finally`：

```python
page = ChromiumPage()

try:
    page.get('https://example.com')
    print(page.title)
finally:
    page.quit()
```

---

## 15. 推荐学习顺序

1. 学会创建 `ChromiumPage` 和打开网页。
2. 学会使用 `ele()`、`eles()` 定位元素。
3. 学会 `click()`、`input()`、`text`、`attr()`。
4. 学会等待元素出现和页面加载。
5. 学会表单、标签页、截图、JavaScript 执行。
6. 再学习代理、无头模式、下载、拦截、混合模式等进阶功能。

---

## 16. 官方文档链接

- DrissionPage 官网：https://www.drissionpage.cn/
- 浏览器控制入门：https://www.drissionpage.cn/browser_control/intro/
- 页面对象：https://www.drissionpage.cn/browser_control/page/
- 元素定位：https://www.drissionpage.cn/browser_control/element/
- 元素交互：https://www.drissionpage.cn/browser_control/interaction/
- 表单操作：https://www.drissionpage.cn/browser_control/form/
- 等待机制：https://www.drissionpage.cn/browser_control/wait/
- 标签页管理：https://www.drissionpage.cn/browser_control/tabs/
- JavaScript 执行：https://www.drissionpage.cn/browser_control/javascript/
- 浏览器配置：https://www.drissionpage.cn/browser_control/config/
