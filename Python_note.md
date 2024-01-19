## Python爬虫基础

### 一、Request库

#### 1、request库安装

①同时按下win+R，输入cmd，打开命令行。

②输入`pip install requests`

③输入python，启动python，再输入`import requests`。若不报错则安装成功。

#### 2、Requests库的7个主要方法

requests.request()：构造一个请求，支撑一下各方法的基础方法。

requests.get()：获取html网页的主要方法，对应于http的get。

requests.head()：获取html网页头信息的方法，对应于http的head。

requests.post()：向html网页提交post请求的方法，对应于http的post。

requests.put()：向html网页提交put请求的方法，对应于http的put。

requests.patch()：向html网页提交patch请求的方法，对应于http的patch。

requests.delete()：向html页面提交删除请求，对应于http的DELETE。

#### 3、Response对象的属性

r.status_code：http请求的返回状态，200表示连接成功，404表示失败。

r.text：http响应内容的字符串形式，即url对应的页面内容。

r.encoding：从http header中猜测的相应内容编码方式

r.apprent_encoding：从内容中分析出的响应内容编码方式（备选编码方式）。

r.content：http响应内容的二进制形式。

#### 4、Requests库异常

requests.ConnectionError：网络连接错误异常，如DNS查询失败、拒绝连接等。

requests.HTTPError：HTTP错误异常。

requests.URLRequired：URL缺失异常。

requests.TooManyRedirects：超过最大重定向次数，产生重定向异常。

requests.ConnectTimeout：连接远程服务器超时异常。

requests.Timeout：请求URL超时，产生超时异常。

#### 5、理解Requests库的异常

r.raise_for_status()：如果不是200，产生异常requests.HTTPError。

#### 6、http协议

URL格式：`http://host[:port][path]`

host：合法的Internet主机域名或IP地址。

port：端口号，可不写，默认为80。

path：请求资源的路径。

### 二、Beautiful Soup库

#### 1、安装

打开cmd，输入`pip3 install beautifulsoup4`。

#### 2、使用

```
from bs4 import BeautifulSoup
soup=BeautifulSoup(data,'html.parser')
```

其中data为爬取的网页源代码，html.parser为对data的解释器。

#### 3、基本元素

bs4库的理解

bs4库是解析、遍历、维护“标签树”的功能书。

```html
<p class="title">..</p>
<p>..</p>是以p为名称的标签类型。
```

class=“title”是该标签的属性域，是一个键值对。

引用方式

```
from bs4 import BeautifulSoup
import bs4
```

解析器

bs4的HTML解析器：BeautifulSoup(mk,'html.parser') 需安装bs4库。

lxml的HTML解析器：BeautifulSoup(mk,'lxml')需`pip install lxml`。

lxml的XML解析器：BeautifulSoup(mk,'xml')需`pip install lxml`。

html5lib的解析器：BeautifulSoup(mk,'html5lib')需`pip install html5lib`。

BeautifulSoup类的基本元素

Tag：标签，最基本的信息组织单元，分别用<>和</>标明开头或结尾。

Name：标签的名字，<p>...</p>的名字是p，格式：<tag>.name。

Attributes：标签的属性，字典形式组织，格式：<tag>.attrs

NavigableString：标签内非属性字符串，<>...</>中字符串，格式为<tag>.string。

Comment：标签内字符串的注释部分，一种特殊的Comment类型。

#### 4、基于bs4库的HTML内容遍历方法

标签树下行遍历

.contents：子节点的列表，将<tag>所有儿子节点存入列表。

.children：子节点的**迭代类型**，与.content类似，用于循环遍历儿子节点。

.descendants：子孙节点的**迭代类型**，包含所有子孙节点，用于循环遍历。

标签树的上行遍历

.parent：节点的父亲标签

.parents：节点先辈（不止父亲）标签的迭代类型，用于循环遍历先辈节点。

标签树的平行遍历

.next_sibling：返回按照html文本顺序的下一个平行节点标签。

.previous_sibling：返回按照html文本顺序的上一个平行节点标签。

.next_siblings：**迭代类型**，返回按照html文本顺序的后续所有平行节点标签。

.previous_siblings：**迭代类型**，返回按照html文本顺序的前序所有平行节点标签。

遍历后续节点

```python
for sibling in soup.a.next_siblings:
	print(sibling)
```

遍历前序节点

```python
for sibling in soup.a.previous_siblings:
	print(sibling)
```

**\#迭代类型只能用在循环中！！！**

基于bs4库的HTML格式化和编码

**格式化**

.prettify()：为标签添加换行符。

编码：UTF-8，支持中文。

基于bs4库的HTML内容查找方法

.find_all(name,attrs,recursive,string,**kwargs)

name：对标签名称的检索字符串。

attrs：对标签属性值的检索字符串，可标注属性检索。

recursive：是否对子孙所有节点进行搜索，默认为true。

string：<>...</>中字符串区域的检索字符串。

简写：

<tag>(...)等价于<tag>.find_all(...)

soup(...)等价于soup.find_all(...)

扩展方法

<>.find()：搜索且只返回一个结果，字符串类型，同.find_all()参数。

<>.find_parents()：在先辈节点中搜索，返回列表类型，同.find_all()参数。

<>.find_parent()：在先辈节点中返回一个结果，字符串类型，同.find()参数。

<>.find_next_siblings()：在后续平行节点中搜索，返回列表类型，同.find_all()参数。

<>.find_next_sibling()：在后续平行节点中返回一个结果，字符串类型，同.find()参数。

<>.find_previous_siblings()：在前序平行节点中搜索，返回列表类型，同.find_all()参数。

<>.find_previous_sibling()：在前序平行节点中返回一个结果，字符串类型，同.find()参数。

### 三、正则表达式

```
([\w]+(\.[\w]+)*@[\w]+(\.[\w])+)
```

### 1、正则表达式的概念

用来表达字符串的简洁方式。

通用的字符串表达框架。

字符串匹配。

#### 2、正则表达式的语法

正则表达式长常用操作符

`.`：表示任何单个字符。

`[]`：字符集，对单个字符给出取值范围。[abc]表示a,b,c，[a-z]表示a到z的单个字符。

`[^ ]`：非字符集，对单个字符给出排除范围。`[^abc]`表示非a或非b或非c的单个字符。

`*`：前一个字符出现0次或无限次扩展。`abc*`表示ab，abc，abcc，abccc等。

`+`：前一个字符1次或无限次扩展。abc+表示abc，abcc，abcc等

`?`：前一个字符0次或1次扩展。abc?表示ab、abc。

`|`：左右表达式任意一个。abc|def表示abc、def。

{m}：表示扩展前一个字符m次。ab{2}c表示abbc。

{m,n}：扩展前一个字符m至n次（含n），ab{1,2}c表示abc、abbc。

`^`：匹配字符串开头。^abc表示abc且在一个字符串的开头。

`$`：匹配字符串结尾。abc$表示abc且在一个字符串的结尾。

`()`：分组标记，内部只能使用|操作符。(abc)表示abc，(abc|def)表示abc、def。

`\d`：数字，等价于[0-9]。

`\w`：单词字符，等价于[A-Za-z0-9_]。

`\#`匹配中文字符串：[\u4e00-\u9fa5]

匹配IP地址的正则表达式

IP地址分4段，每段0-255。

(([1-9]?\d|1\d{2}|2[0-4]\d|25[0-5]).){3}([1-9]?\d|1\d{2}|2[0-4]\d|25[0-5])

#### 3、Re库的基本使用

Re库介绍

Re库是python标准库，主要用于字符串的匹配。

调用方式：`import re`

正则表达式的表示类型

**raw string类型（原生字符串类型）**

用法：r''。即在字符串前面加一个r。

原生字符串：不含转义符\的字符串。

**string类型**

即不加r，是平时用的字符串，更繁琐。

需用`\\`来表示\。

Re库主要功能函数

**re.search(pattern,string,flags=0)**：

在一个字符串中搜索匹配正则表达式的第一个位置，返回match对象。

pattern：正则表达式的字符串或原生字符串表示。

string：待匹配字符串。

flags：使用时的控制标记。

re.I | re.IGNORECASE：忽略正则表达式的大小写，[A-Z]能够匹配小写字符。

re.M | re.MULTILINE：正则表达式种的^操作符能够将给定字符串的每行当作匹配开始。

re.S | re.DOTALL：正则表达式种的.操作符能够匹配所有字符，默认匹配除换行外的所有字符。

**re.match(pattern,string,flags=0)**：

从一个字符串的开始位置起匹配正则表达式，返回match对象。

参数含义同re.search。

**re.findall(pattern,string,flags=0)**：

搜索字符串，以列表类型返回全部能匹配的字串。

参数含义同re.search。

**re.splite(pattern,string,maxsplit=0,flags=0)**：

将一个字符串按照正则表达式匹配结果进行分割，返回列表类型。

参数含义同re.search。

maxsplit：最大分割数，剩余部分作为最后一个元素输出。

**re.finditer(pattern,string,flags=0)**：

搜索字符串，返回一个匹配结果的迭代类型，每个迭代元素是match对象。

参数含义同re.search。

**re.sub(pattern,repl,string,count=0,flags=0)**：

在一个字符串中替换所有匹配正则表达式的子串，返回替换后的子串。

参数含义同re.search。

repl：替换匹配字符串的字符串。

count：匹配的最大替换次数。

\#re.compile：面向对象。

rst=re.search(r'[1-9]\d{5},'BIT 100081")

等价于

pat=re.compile(r'[1-9]\d{5}')

rst=pat.search('BIT 100081')

\#**re.compile(pattern,flags=0)**：

将正则表达式的字符串形式编译成正则表达式对象。

#### 4、Re库的match对象

Match对象的属性

.string：待匹配的文本。

.re：匹配时使用的pattern对象（正则表达式）。

.pos：正则表达式搜索文本的开始位置。

.endpos：正则表达式搜索文本的结束位置。

Match对象的方法

.group(0)：获得匹配后的字符串。

.start()：匹配字符串在原始字符串的开始位置。

.end()：匹配字符串在原始字符串的结束位置。

.span()：返回(.start(),.end())

#### 5、Re库的贪婪匹配和最小匹配

贪婪匹配

Re库默认采用贪婪匹配，即输出匹配最长的子串。

最小匹配操作符

*?：前一个字符0次或无限次扩展，最小匹配。

+?：前一个字符1次或无限次扩展，最小匹配。

??：前一个字符0次或1次，最小匹配。

{m,n}?：扩展前一个字符m至n次(含n)，最小匹配。

### 四、Scrapy框架

https://www.icourse163.org/course/BIT-1001870001?from=searchPage&outVendor=zw_mooc_pcssjg_

#### 1、Scrapy库安装

打开cmd输入`pip install scrapy`。

#### 2、Scrapy爬虫框架结构

5+2结构、数据流

![img](https://img-blog.csdnimg.cn/125fe04f486c42438122dd5c18ad56f6.JPG?x-oss-process=image/watermark,type_ZHJvaWRzYW5zZmFsbGJhY2s,shadow_50,text_Q1NETiBALkFE6ZKZLg==,size_20,color_FFFFFF,t_70,g_se,x_16)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑

#### 3、Scarpy爬虫框架解析

**ENGINE:**

控制所有模块之间的数据流。

根据条件触发事件。

不需要用户修改。

**DOWNLOADER:**

根据请求下载网页。

不需要修改。

**SCHEDULER:**

对所有爬取请求进行调度管理。

不需要用户修改

**DOWNLOADER MIDDLEWARE**

downloader和engine两个模块之间的中间键。

目的：实施Engine、Scheduler和Downloader之间进行用户可配置的控制。

功能：修改、丢弃、新增请求或响应。

用户可以编写代码修改。

**Spider：**

解析Downloader返回的响应（Response）。

产生爬取项（scraped item）。

产生额外的爬取请求（Request）。

需要用户编写配置代码。

**Item Pipelines:**

以流水线方式处理Spider产生的爬取项。

由一组操作顺序组成，类似流水线，每个操作是一个Item Pipeline类型。

可能操作包括：清理、检验和查重爬取项中的HTML数据、将数据存储到数据库。

需要用户编写配置代码。

**Spider Middleware**

Spider和Engine之间的中间键。

目的：对请求和爬取项的再处理。

功能：修改、丢弃、新增请求或爬取项。

用户可以编写配置代码。

#### 4、Scrapy爬虫的常用命令

Scrapy命令行(cmd)

**startproject**

创建一个新工程。

scrapy startproject<name>[dir]

**genspider**

创建一个爬虫。

scrapy genspider[options]<name><domain>

**settings**

获得爬虫配置信息。

scrapy settings[options]

**crawl**

运行一个爬虫。

scrapy crawl<spider>

**list**

列出工程中所有爬虫。

scrapy list

**shell**

启动url调试命令行。

scrapy shell[url]

操作步骤

**1、建立一个Scrapy爬虫工程**

①、打开命令行，切换到自己希望存储的目录。

②、输入`scrapy startproject 文件名`。

③、生成工程目录

文件夹：外层目录

scrapy.cfg：部署scrapy爬虫的配置文件。

文件夹：scrapy框架的用户自定义python代码。

`_init_.py`：初始化脚本

`item.py`：Items代码模板（继承类）

`middlewares.py`：Middlewares代码模板（继承类）

`pipelines.py`：pipelines代码模板（继承类）

`settings.py`：scrapy爬虫的配置文件

`spiders/`：spiders代码模板目录（继承类）

`_init_.py`：初始文件，无需修改。

`_pycache_/`：缓存目录，无需修改。

**2、在工程中产生一个Scrapy爬虫**

命令行中输入`scrapy genspider 文件名 爬取网站网址`

**3、配置产生的spider爬虫**

```python
#例子
import scrapy


class DemoSpider(scrapy.Spider):
    name = 'demo'
    #allowed_domains = ['python123.io']
    start_urls = ['http://python123.io/ws/demo.html']

    def parse(self, response):
        fname=response.url.split('/')[-1]
        with open(fname,'wb') as f:
            f.write(response.body)
        self.log('Saved file %s.' % name)
        pass
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

**4、运行爬虫，获取网页**

#### 5、yield关键词使用

**yeild<-->生成器**

1、生成器是一个不断产生值的函数。

2、包含yield语句的函数是一个生成器。

3、生成器每次产生一个值（yield语句），函数被冻结，被唤醒后再产生一个值。

**实例**

生成器写法

```python
def gen(n):
    for j in range(n):
        yield j**2
#产生所有小于n的数的平方值，运行到yield这一行时，运算i**2的值并返回，然后函数被冻结。
for i in gen(5):
    print(i, " ", end="")
#>>>输出结果：0  1  4  9  16
#这块儿只可意会不可言传，大概解释一下就是，进入主函数的for循环的时候，先运行gen(5)，此时进入gen函数，第一次走gen里的循环，j=0，经过yield，返回0给i，此时i为0。第一次i循环结束。走第二次，再次调用gen，此时gen里的j=1，重复上述。按我的说法就是，yield是一个有记录状态功能的return。
```

#### 6、Scrapy爬虫的基本使用

Scrapy爬虫的使用步骤：

1、创建一个工程和Spider模板

2、编写Spider

3、编写Item Pipeline

4、优化配置策略

Scrapy爬虫的数据类型：

**Request类**

```
class scrapy.http.Request()
```

Request对象表示一个HTTP请求。

由Spider生成，由Downloader执行。

属性或方法：

.url：Request对应的请求URL地址。

.method：对应的请求方法，'GET''POST'等。

.headers：字典类型风格的请求头。

.body：请求内容主体，字符串类型。

.meta：用户添加的扩展信息，在Scrapy内部模块间传递信息使用。

.copy()：复制该请求。

**Response类**

```
class scrapy.http.Response()
```

Response对象表示一个HTTP响应。

由Downloader生成，由Spider处理。

属性或方法：

.url：Response对应的url地址。

.status：HTTP状态码，200、404、403……

.headers：Response对应的头部信息。

.body：Response对应的内容信息，字符串类型。

.flags：一组标记。

.request：产生Response类型对应的Request对象。

.copy()：复制该响应。

**Item类**

```
class scrapy.item.Item()
```

Item对象表示一个从HTML页面中提取的信息内容。

由Spider生成，由Item Pipeline处理。

Item类似字典类型，可以按照字典类型操作。

Scrapy爬虫支持的HTML信息提取方法

Beautiful Soup

lxml

re

XPath Selector

**CSS Selector**

使用格式：`<html>.css('a::attr(href)').extract()`

### 五、Selenium

参考：https://blog.csdn.net/kobepaul123/article/details/128796839

#### 1、selenium库安装

```bash
pip3 install selenium 
```

#### 2、浏览器驱动安装

找到自己的浏览器 谷歌/火狐 的版本

下载对应版本的驱动

[Chrome-driver][https://chromedriver.storage.googleapis.com/index.html]：谷歌要对应好版本

[Firefox-driver][https://github.com/mozilla/geckodriver/releases]：火狐没有特别死的版本要求，具体见下表

![img](https://img-blog.csdnimg.cn/20190531112848316.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3lpbnNodWlsYW4=,size_16,color_FFFFFF,t_70)

#### 3.对页面进行操作

##### 3.1 初始化浏览器对象

前期我们将Chrome驱动添加到环境变量了，所以我们可以直接初始化界面。（或者也可以通过指定绝对路径的方式）

```python
from selenium import webdriver
# 初始化浏览器为chrome浏览器
browser = webdriver.Chrome()
# 指定绝对路径的方式（可选）
path = r'C:\\Users\\Gdc\\.wdm\\drivers\\chromedriver\\win32\\96.0.4664.45\\chromedriver.exe'
browser = webdriver.Chrome(path)
# 关闭浏览器
browser.close()
```

##### 3.2 访问页面

进行页面访问使用的是get方法，传入参数为待访问页面的URL地址即可。

```python
from selenium import webdriver
# 初始化浏览器为chrome浏览器
browser = webdriver.Chrome()
# 访问百度首页
browser.get(r'https://www.baidu.com/')
# 关闭浏览器
browser.close()
```

##### 3.3 设置浏览器大小

set_window_size()方法可以用来设置浏览器大小（就是分辨率），而maximize_window则是设置浏览器为全屏。

```python
from selenium import webdriver
import time  

browser = webdriver.Chrome()

# 设置浏览器大小：全屏
browser.maximize_window()   
browser.get('https://www.baidu.com')  
time.sleep(2)

# 设置分辨率 500*500
browser.set_window_size(500,500)  
time.sleep(2)

# 关闭浏览器
browser.close()
```

##### 3.4 前进后退

前进后退也是我们在使用浏览器时非常常见的操作，这里forward()方法可以用来实现前进，back()可以用来实现后退。

```python
from selenium import webdriver
import time  

browser = webdriver.Firefox()

# 设置浏览器全屏
browser.maximize_window()   
browser.get('https://www.baidu.com')  
time.sleep(2)

# 打开淘宝页面
browser.get('https://www.bilibili.com/')  
time.sleep(2)

# 后退到百度页面
browser.back()  
time.sleep(2)

# 前进的淘宝页面
browser.forward() 
time.sleep(2)

# 关闭浏览器
browser.close()
```

##### 3.5 获取页面基础属性

当我们用selenium打开某个页面，有一些基础属性如网页标题、网址、浏览器名称、页面源码等信息

```python
from selenium import webdriver

browser = webdriver.Firefox()
browser.get('https://www.baidu.com') 

# 网页标题
print(browser.title)
# 当前网址
print(browser.current_url)
# 浏览器名称
print(browser.name)
# 网页源码
print(browser.page_source)
```

#### 4.定位页面元素

```python
from selenium.webdriver.common.by import By
```

| 属性              | 函数                                            |
| ----------------- | ----------------------------------------------- |
| CLASS             | find_element(by=By.CLASS_NAME, value=‘’)        |
| XPATH             | find_element(by=By.XPATH, value=‘’)             |
| LINK_TEXT         | find_element(by=By.LINK_TEXT, value=‘’)         |
| PARTIAL_LINK_TEXT | find_element(by=By.PARTIAL_LINK_TEXT, value=‘’) |
| TAG               | find_element(by=By.TAG_NAME, value=‘’)          |
| CSS               | find_element(by=By.CSS_SELECTOR, value=‘’)      |
| ID                | find_element(by=By.ID, value=‘’)                |

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()
driver.get('https://www.baidu.com') 
element=browser.find_element(by=By.CLASS_NAME,value='s_ipt')
element=browser.find_element(by=By.ID,value='kw')
```

#### 5.模拟鼠标操作

需要导入ActionChains 类。

> click(on_element=None) ——单击鼠标左键
>
> click_and_hold(on_element=None) ——点击鼠标左键，不松开
>
> context_click(on_element=None) ——点击鼠标右键
>
> double_click(on_element=None) ——双击鼠标左键
>
> drag_and_drop(source, target) ——拖拽到某个元素然后松开
>
> drag_and_drop_by_offset(source, xoffset, yoffset) ——拖拽到某个坐标然后松开
>
> key_down(value, element=None) ——按下某个键盘上的键
>
> key_up(value, element=None) ——松开某个键
>
> move_by_offset(xoffset, yoffset) ——鼠标从当前位置移动到某个坐标
>
> move_to_element(to_element) ——鼠标移动到某个元素
>
> move_to_element_with_offset(to_element, xoffset, yoffset) ——移动到距某个元素（左上角坐标）多少距离的位置
>
> perform() ——执行链中的所有动作
>
> release(on_element=None) ——在某个元素位置松开鼠标左键
>
> send_keys(*keys_to_send) ——发送某个键到当前焦点的元素
>
> send_keys_to_element(element, *keys_to_send) ——发送某个键到指定元素

```python
from selenium.webdriver.common.action_chains import ActionChains

element = browser.find_element(by=By.XPATH, value='//*[@id="i_cecream"]/div[2]/div[1]/div[3]/div[2]/div[1]/a[1]')
element.click()
```

#### 6.模拟键盘操作

```python
from selenium.webdriver.common.keys import Keys
```

| 操作   | 函数                       |
| ------ | -------------------------- |
| 删除键 | send_keys(Keys.BACK_SPACE) |
| 空格键 | send_keys(Keys.SPACE)      |
| 制表键 | send_keys(Keys.TAB)        |
| 回退键 | send_keys(Keys.ESCAPE)     |
| 回车   | send_keys(Keys.ENTER)      |
| 全选   | send_keys(Keys.CONTRL,‘a’) |
| 复制   | send_keys(Keys.CONTRL,‘c’) |
| 剪切   | send_keys(Keys.CONTRL,‘x’) |
| 粘贴   | send_keys(Keys.CONTRL,‘x’) |
| 键盘F1 | send_keys(Keys.F1)         |

#### 7.延时等待

如果遇到使用`ajax`加载的网页，页面元素可能不是同时加载出来的，这个时候尝试在get方法执行完成时获取网页源代码可能并非浏览器完全加载完成的页面。所以，这种情况下需要设置延时等待一定时间，确保全部节点都加载出来。
三种方式：强制等待、隐式等待和显式等待

**强制等待**
就很简单了，直接time.sleep(n)强制等待n秒，在执行get方法之后执行。

**隐式等待**
implicitly_wait()设置等待时间，如果到时间有元素节点没有加载出来，就会抛出异常。

**显式等待**
设置一个等待时间和一个条件，在规定时间内，每隔一段时间查看下条件是否成立，如果成立那么程序就继续执行，否则就抛出一个超时异常。

WebDriverWait的参数说明：`WebDriverWait(driver,timeout,poll_frequency=0.5,ignored_exceptions=None)`

> driver: 浏览器驱动
>
> timeout: 超时时间，等待的最长时间（同时要考虑隐性等待时间）
>
> poll_frequency: 每次检测的间隔时间，默认是0.5秒
>
> ignored_exceptions:超时后的异常信息，默认情况下抛出NoSuchElementException异常
>
> until(method,message=‘’)
>
> method: 在等待期间，每隔一段时间调用这个传入的方法，直到返回值不是False
>
> message: 如果超时，抛出TimeoutException，将message传入异常
>
> until_not(method,message=‘’): 与until相反，until是当某元素出现或什么条件成立则继续执行，until_not是当某元素消失或什么条件不成立则继续执行，参数也相同。

#### 8.切换操作

**窗口切换**
在 selenium 操作页面的时候，可能会因为点击某个链接而跳转到一个新的页面（打开了一个新标签页），这时候 selenium 实际还是处于上一个页面的，需要我们进行切换才能够定位最新页面上的元素。

窗口切换需要使用 switch_to.windows() 方法。

首先我们先看看下面的代码。

上面代码在点击跳转后，使用`switch_to`切换窗口，`window_handles`返回的`handle`列表是按照页面出现时间进行排序的，最新打开的页面肯定是最后一个，这样用`driver.window_handles[-1]`+`switch_to`即可跳转到最新打开的页面了。

那如果打开的窗口有多个，如何跳转到之前打开的窗口，如果确实有这个需求，那么打开窗口是就需要记录每一个窗口的 key(别名) 与 value(handle)，保存到字典中，后续根据 key 来取 handle 。

**表单切换**
很多页面也会用带 frame/iframe 表单嵌套，对于这种内嵌的页面 selenium 是无法直接定位的，需要使用 switch_to.frame() 方法将当前操作的对象切换成 frame/iframe 内嵌的页面。

switch_to.frame() 默认可以用的 id 或 name 属性直接定位，但如果 iframe 没有 id 或 name ，这时就需要使用 xpath 进行定位。下面先写一个包含 iframe 的页面做测试用。

#### 9.对Cookie操作

cookies 是识别用户登录与否的关键，爬虫中常常使用 selenium + requests 实现 cookie持久化，即先用 selenium 模拟登陆获取 cookie ，再通过 requests 携带 cookie 进行请求。

webdriver 提供 cookies 的几种操作：读取、添加删除。

> get_cookies：以字典的形式返回当前会话中可见的 cookie 信息。
>
> get_cookie(name)：返回 cookie 字典中key == name 的 cookie 信息
>
> add_cookie(cookie_dict)：将 cookie 添加到当前会话中
>
> delete_cookie(name)：删除指定名称的单个 cookie
>
> delete_all_cookies()：删除会话范围内的所有cookie

```python
from selenium import webdriver
browser = webdriver.Chrome()
# 知乎发现页
browser.get('https://www.zhihu.com/explore')
# 获取cookie
print(f'Cookies的值：{browser.get_cookies()}')
# 添加cookie
browser.add_cookie({'name':'才哥', 'value':'帅哥'})
print(f'添加后Cookies的值：{browser.get_cookies()}')
# 删除cookie
browser.delete_all_cookies()
print(f'删除后Cookies的值：{browser.get_cookies()}')
# 总结
```

#### 10.xpath方法

XPath是一门在XML文档中查找信息的语言，被用于在XML文档中通过元素和属性进行导航。有七种类型的节点：元素、属性、文本、命名空间、处理指令、注释以及文档（根）节点。

XPath路径表达式

| 表达式   | 描述                          |
| -------- | ----------------------------- |
| nodename | 选取此节点的所有子节点（div） |
| /        | 从根节点选取                  |
| //       | 选择任意位置的某个节点        |
| .        | 选取当前节点                  |
| …        | 选取当前节点的父节点          |
| @        | 选取属性                      |

通配符	描述

| 通配符 | 描述             |
| ------ | ---------------- |
| *      | 匹配任何元素节点 |
| @*     | 匹配任何属性节点 |
| node() | 匹配任何类型节点 |

**文本定位**

使用text()元素的text内容 如：//button[text()=“登录”]

**模糊定位**

使用contains() 包含函数 如：//button[contains(text(),“登录”)]、//button[contains(@class,“btn”)]
匹配以xx结尾的属性值 如：//input[starts-with(@id,“login-”)]、//input[ends-with(@id,“ogin-email”)]

**逻辑定位**

使用逻辑运算符 – and、or；如：//input[@name=“phone” and @datatype=“m”] 可以根据一个元素的多个属性进行定位，确保唯一性

**轴定位**

轴定位是根据父节点，兄弟节点等节点来定位本节点，使用语法： 轴名称 :: 节点名称，使用较多场景：页面显示为一个表格样式的数据列

| 描述                           | 表达式                                                       |
| ------------------------------ | ------------------------------------------------------------ |
| 定位当前节点后的所有节点       | //标签名[@属性=属性值]/follow::标签名[@属性=属性值]          |
| 定位同一节点后的所有同级节点   | //标签名[@属性=属性值]/follow-sibling::标签名[@属性=属性值]  |
| 定位当前节点的所有子节点       | //标签名[@属性=属性值]/child::标签名[@属性=属性值]           |
| 定位当前节点前的所有节点       | //标签名[@属性=属性值]/preceding::标签名[@属性=属性值]       |
| 定位同一个节点前的所有同级节点 | //标签名[@属性=属性值]/preceding-sibling::标签名[@属性=属性值] |
| 定位当前节点的所有父节点       | //标签名[@属性=属性值]/parent::标签名[@属性=属性值]          |
| 定位当前节点的所有祖父节点     | //标签名[@属性=属性值]/ancestor::标签名[@属性=属性值]        |

