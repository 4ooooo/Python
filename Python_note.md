# Python笔记

[TOC]



## 第一节 	数据类型

### 1、变量与常量

**变量：**在程序运行过程中会有一些中间值，在稍后的执行中会用到，这时可以将这些中间值赋值给变量，然后在后面的代码中通过调用这些变量名来获取这些值。可以简单的理解为给这些值取一个别名，这个别名就代表这个值。

**命名规则：**

> 1. 由大小写字母 A-Za-z，数字 0-9 和下划线 `_` 组成
> 2. 不能以数字开头
> 3. 不能是关键字
> 4. 变量名大小写敏感

```python
a=2#a是变量，2是常量，该语句意为将2赋给a，也就是令a=2
b=3#同上
c=a#a和c都是变量，该句意为将a的值赋给c，也就是令a=c
```

**赋值运算符：**在 python 中 = 是赋值运算符，而不是数学意义上的等于号。python 解释器会先计算 = 右边的表达式，然后将结果复制给=左边的变量。

**查看变量类型**：type()

```python
type(a)
```

### 2、整数类型(int)

（1）……-2、-1、0、1、2、3、4、5……

​		python 中整数类型的理论取值范围是[-无穷，无穷]，实际取值范围受限于运行 python 程序的计算机内存大小。

（2）进制：

```python
17#十进制
0b10001#0b开头为二进制
0o21#0o开头为八进制
0x11#0x开头为十六进制
```

（3）进制转换

```python
#十进制转换二进制
bin(3)#结果为0b11
#十进制转换八进制
oct(12)#结果为0o14
#十进制转换十六进制
hex(18)#结果为0x12
```

```python
#二进制转换十进制
int('11',2)#结果为3
#八进制转换十进制
int('11',8)#结果为9
#十六进制转换十进制
int('11',16)#结果为17
#注意，转换进制此处没有限制，1、2、3、4、5……都可以
```

### 3、浮点数类型(float)

（1）就是小数

（2）科学计数法

```python
2.1E5 = 2.1*(10**5)#其中 2.1 是尾数，5 是指数。
3.7E-2 = 3.7*(10**(-2))#其中 3.7 是尾数，-2 是指数。
0.5E7 = 0.5*(10**7)#其中 0.5 是尾数，7 是指数。
#e大写或小写都行
```

（3）浮点数与整数之间转换

```python
#浮点型转为整数型
int(13.9)#结果为13，注意不是四舍五入，是直接把小数部分扔掉整数部分不变。
#整数转为浮点数
float(13)#结果为13.0
```

### 4、复数类型(complex)

用的不多

```python
a=12.3+4j
print(a.real)#结果为12.3，a的实部
print(a.imag)#结果为4.0，a的虚部
```

### 5、布尔类型(bool)

0表示假，1表示真，用于逻辑判断。

### 6、字符串类型(char)

（1）使用文本时，就要用字符串类型。用引号包裹起来的可以是字母、数字、汉字。单引号''或双引号""均可。

```python
"学习"
'学习'
```

（2）字符串转义

某些字符不能直接包含在字符串中。例如，双引号不能直接包含在双引号字符串中，这将导致它过早结束。

![img](https://img.jbzj.com/file_images/article/202009/2020090314165647.jpg)

（3）字符串相关函数

```python
s='abcdefg'
#取字符串中的第i位(i从0开始)，支持负数，负数即为倒着数
x=s[i]
print(s[-1])#结果为g
#取字符串中的一个片段(从第m位开始，到第n位)，隔l位取一位，若n不填则取到结尾(包括最后一位)，若m不填则从头开始取，l不填默认为1
x=s[m:n:l]#左闭右开，包含第m位，不包含第n位
x=s[:n]
x=s[m:]
print(s[1:5:2])#结果为bd
#获得字符串长度
length=len(s)
#大小写转换
s.lower()#将s中的所有字母变为小写
s.upper()#将s中的所有字母变为大写
#去掉(左右)两边指定的的字符b，b是一个自定义的字符串变量，b为空时默认去掉空格
s.strip(b)#去掉s中两侧的b
s.strip('a')#结果为bcdefg
s.lstrip(b)#去掉左边的
s.rstrip(b)#去掉右边的
```

python3关于字符串的详细知识点：https://m.runoob.com/python3/python3-string.html

### 7、列表类型(list)

（1）类似于数组。

```python
list1=[1,2,3,4,5]
list2=['a','b','c','d']
list3=['abfcd','adsfasdfasd',13123,'asdfasd']
list4=[list1,list2,list3]
```

（2）相关函数

```python
list0=['a',1,'b',2,'c',3]
#截取语法与字符串完全相同，其含义只是将字符串中的第几个字符改为列表中的第几个单元的值。
#获取列表长度
len(list0)#结果为6
#列表中添加项
list0.append(x)#x为要添加的值，添加到列表的末尾
#取列表中最大值
max(list0)
#取最小值
min(list0)
#将字符串以指定字符x为间隔拆分成列表
s.split(x)
s='a,b,c,d,e'
list1=s.split(',')#list1为['a','b','c','d','e']
#元组、集合x转换为列表
list0=list(x)
```

### 8、元组类型

用()包裹，截取语法类似于列表。

**特点：不可修改**

```python
#创建元组，括号内一定要以逗号结尾
tu=(,)#空元组
tu1=(1,2,3,)
#列表转换元组
tuple(list0)
```

### 9、集合类型

用{}包裹，截取语法类似于列表，可修改。

**特点：与数学中的集合类似，确定性、无序性、互异性。无序性体现在即输出一个集合三次，看到的集合内部顺序可能不一样**

```python
#创建集合
a=set()#空集合
a={'a','bcc','d'}
#字符串去重
b=set('abcbddeeffg')#b为('a','b','c','d','e','f','g')
#集合中添加元素x
a.add(x)
#列表去重
list0=['a','b','a','c']
b=set(list0)#b为('a','b','c')
list0=list(b)#list0为['a','b','c']
```

### 10、字典类型

键值对[key:value]

```python
#形如
zd={key1:value1,key2:value2,key3:value3}
#创建空字典
zd={}
#取value1的值
zd[key1]
#修改信息
zd[key2]=value_test
#添加信息
zd[key4]=value4
```

## 第二节 I/O操作

### 1、键盘输入

```python
a=input('提示信息')
```

### 2、文件读取

#### ①读取文件

##### Ⅰ、txt文件

使用with open命令，bug不容易出现，尽量少使用open

```python
with open('路径/文件名','权限') as f:#打开文件，路径/文件名为要打开的文件的路径和文件名。权限见下图
    for i in f.readlines():
        list.append(i)
f.close()#关闭文件，使用with open时可以不写这一行
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210312112329568.png)

```python
#例1
with open('C:\\a.txt','r') as f:
    for i in f.readlines():
        list.append(i)
f.close()
```

> 读取方法：
>
> read()  ： 一次性读取整个文件内容。推荐使用read(size)方法，size越大运行时间越长
>
> readline()  ：每次读取一行内容。内存不够时使用，一般不太用
>
> readlines()  ：一次性读取整个文件内容，并按行返回到list，方便我们遍历

##### Ⅱ、csv文件

###### 按行读取

```python
import csv
with open('file.csv','r'，encoding=“utf-8”) as csvfile:
    reader = csv.reader(csvfile)
    rows = [row for row in reader]
```

###### 读取某一列

```python
with open(filename,encoding="utf-8") as f:
    reader = csv.reader(f)
    header_row = next(reader)
    datas = []
    for row in reader:
        print(row[2])
```

#### ②写入文件

##### Ⅰ、txt文件

```python
with open('a.txt','a') as f:
    f.write('内容')
f.close()
```

##### Ⅱ、csv文件

```python
list=['a','b','c']
with open('1.csv', 'a',newline='') as f:
    csv_writer = csv.writer(f)
    csv_writer.writerows([list])#将列表按行写入
f.close()
```

### 3、输出

#### 屏幕打印

```python
a=123
print('打印内容')
print(123)
print(a)
```

##### 格式化

```python
a=123
print('{}'.format(a))#输出结果为字符串类型的123
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210128110318187.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl81MTAxMjkzNw==,size_16,color_FFFFFF,t_70)

#### 文件输出

即写入文件，方法之前说过了。参照2-②。
