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
tu1=(1,2,3)
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



## 第三节 计算

### 1、数值计算

| 符号 | 含义                   | 用法 | 运算结果 |
| ---- | ---------------------- | ---- | -------- |
| +    | 加                     | 1+1  | 2        |
| -    | 减                     | 2-1  | 1        |
| *    | 乘                     | 2*3  | 6        |
| /    | 除                     | 4/2  | 2        |
| **   | 乘方（幂）             | 2**3 | 8        |
| %    | 求余                   | 9%2  | 1        |
| //   | 整除（除后取整数部分） | 3//2 | 1        |

**abs()函数**

取绝对值

```python
abs(-1)=1
```

### 2、字符串运算

| 符号 | 含义         | 用法        | 运算结果 |
| ---- | ------------ | ----------- | -------- |
| +    | 拼接         | 'aaa'+'bbb' | 'aaabbb' |
| *    | 成整数倍延长 | 'aaa'*2     | 'aaaaaa' |

### 3、列表运算

| 符号 | 含义         | 用法        | 运算结果  |
| ---- | ------------ | ----------- | --------- |
| +    | 拼接         | [1,2,3]+[4] | [1,2,3,4] |
| *    | 成整数倍延长 | [1,2]*2     | [1,2,1,2] |

### 4、元组运算

| 符号 | 含义 | 用法      | 运算结果 |
| ---- | ---- | --------- | -------- |
| +    | 拼接 | (1,2)+(3) | (1,2,3)  |

> 1、字符串和列表运算的*后跟正整数是正常的倍数延长。跟e和负整数会清空列表
>
> 2、元组运算没有*
>
> 3、集合没有运算符

### 5、比较运算符

返回bool类型变量，用True或False表示

| 符号 | 含义     | 用法 | 结果  |
| ---- | -------- | ---- | ----- |
| >    | 大于     | 1>2  | False |
| <    | 小于     | 1<2  | True  |
| >=   | 大于等于 | 3>=3 | True  |
| <=   | 小于等于 | 3<=4 | True  |
| ==   | 等于     | 2==3 | False |
| !=   | 不等于   | 2!=3 | True  |

### 6、赋值运算符

| 符号 | 含义         | 用法（预先设a=2） | 运行结果 |
| ---- | ------------ | ----------------- | -------- |
| =    | 普通赋值     | a=3               | a=3      |
| +=   | 先加后赋值   | a+=3              | a=5      |
| -=   | 先减后赋值   | a-=3              | a=-1     |
| *=   | 先乘后赋值   |                   |          |
| /=   | 先除后赋值   |                   |          |
| %=   | 先求余后赋值 |                   |          |
| **=  | 先乘方后赋值 |                   |          |
| //=  | 先整除后赋值 |                   |          |

### 7、逻辑运算符

| 符号 | 含义 | 用法           | 运行结果 |
| ---- | ---- | -------------- | -------- |
| and  | 与   | True and False | False    |
| or   | 或   | True or False  | True     |
| not  | 非   | not True       | False    |

### 8、成员运算符

| 符号   | 含义 | 用法                        | 运行结果 |
| ------ | ---- | --------------------------- | -------- |
| in     | 在   | 'xxx' in 'aaabxxxbbccc'     | True     |
| not in | 不在 | 'xxx' not in 'aaaxbbbxcccx' | True     |



## 第四节 条件判断

### If结构

```python
if 判断条件:
    判断为真时执行的代码块
    ...
else:
    判断为假时执行的代码块
    ...
```

**if语句可以嵌套，如下**

```python
if a>b:
	if c>d:
        print(1)
    else:#这是c>d这个if的else
        print(2)
else:#这是a>b的else
    print(3)
```

### match结构(3.10版本以后才有)

```python
match 表达式:
    case 结果1:
        表达式结果等于结果1则运行该部分代码
        ...
    case 结果2:
        ...
    ...
```

**match里同样可以嵌套match，也可以嵌套if**

### 例题

> 1、做一个成绩判定系统，输入一个成绩(0-100分之间)，若学生成绩得分在[85,100]之间，输出A，在[75,85)之间，输出B，在[60,75)之间，输出C，在[0,60)之间，输出D，分别用if结构和match结构实现，看哪个更方便。
>
> ```python
> #非嵌套
> score = eval(input())
> if 85<=score<=100:
>  print("A")
> if 75<=score<85:
>  print("B")
> if 60<=score<75:
>  print("C")
> if 0<=score<60:
>  print("B")
> #嵌套
> score = eval(input())
> if 85<=score<=100:
>  print('A')
> else:
>  if score>=75:
>      print("B")
>  else:
>      if score>=60:
>          print("C")
>      else:
>          print("D")
> ```
>
> 2、还是这个系统，但是反过来，输入是A,B,C,D中的一个，你需要打印出每个等级所对应的分数区间。分别用if结构和match结构实现，看哪个更方便。

## 第五节 循环

https://www.runoob.com/python/python-for-loop.html

### 1、for循环

Python for循环可以遍历任何序列的项目，如一个列表或者一个字符串。

```python
#进行普通的循环取值
for i in range(1,100):#从1至99循环，python的特性是()是左闭右开区间，即左端点可取到，右端点取不到
    print(i)
    
#遍历字符串
for i in "python":
    print(i)#输出结果为单个的'p'、'y'、't'……

#遍历列表
list1=[1,2,'a']
for i in list1:
    print(i)#依次输出列表中的元素，数据类型和列表中对应的数据类型一致，结果为1、2、'a

#通过序列索引迭代
fruits = ['banana', 'apple',  'mango']
for index in range(len(fruits)):
   print ('当前水果 : %s' % fruits[index])

#循环使用 else 语句
#在python 中，for … else 表示这样的意思，for 中的语句和普通的没有区别，else 中的语句会在循环正常执行完（即 for 不是通过 break 跳出而中断的）的情况下执行
for num in range(10,20):  # 迭代 10 到 20 之间的数字
   for i in range(2,num): # 根据因子迭代
      if num%i == 0:      # 确定第一个因子
         j=num/i          # 计算第二个因子
         print ('%d 等于 %d * %d' % (num,i,j))
         break            # 跳出当前循环
   else:                  # 循环的 else 部分
      print ('%d 是一个质数' % num)
```

### 2、while循环

Python 编程中 while 语句用于循环执行程序，即在某条件下，循环执行某段程序，以处理需要重复处理的相同任务。

```python
count = -3
while count < 9:
   print('The count is:', count)
   count = count + 1

#while加else，和if相同
count = 0
while count < 5:
   print(count, " is  less than 5")
   count = count + 1
else:
   print(count, " is not less than 5")

#无限循环
while True:
    print("停不下来啦")
```

## 第六节 异常处理-try except

https://www.runoob.com/python/python-exceptions.html

```python
try:
   正常的操作……
except(Exception1[, Exception2[,...ExceptionN]]):
   发生以上多个异常中的一个，执行这块代码……
else:
    如果没有异常执行这块代码
finally:
<语句>    #退出try时总会执行
```

## 练习题

1、(内置函数) 用变量表示一个人的名字，分别以小写、大写、首字母大写并且除首字母外小写方式显示这个人名。提示:用string函数。

```python
a=input()
print(a.lower())
print(a.upper())
print(a[0].upper()+a[1:])
```

2、(内置函数)用format方法输出如下样式`*****北京欢迎您*****`

```python
print("*****{}*****".format("北京欢迎您"))
```

3、(循环结构) 恺撒密码: 凯撒密码是古罗马凯撒大帝用来对军事情报进行加密的算法，它采用了替换方法对信息中的每一个英文字符循环替换为字母表序列该字符后面第三个字符，对应关系如下:

原文：ABCDEFGHIJKLMNOPQRSTUVWXYZ

密文：DEFGHIJKLMNOPQRSTUVWXYZABC

原文字符p，其密文字符c满足如下条件:c=(p+3) mod 26解密方法反之，满足:p=(c-3) mod 26

plain text明文

cipher text：密文

注:加密、解密功能分别实现。

```python
a=input("请输入加密或解密:\nA.加密\nB.解密\n")
plain=''
cipher=''
if a == "A":
    plain = input("请输入明文：")
    for s in plain:
        if s >'W':
            cipher = cipher + chr(ord(s)+ 3 - 26)
        else:
            cipher = cipher + chr(ord(s) + 3)
    print("密文是:{}".format(cipher))
if a=='B':
    cipher=input("请输入密文：")
    for s in cipher:
        if s<'D':
            plain=plain+chr(ord(s)-3+26)
        else:
            plain=plain+chr(ord(s)-3)
    print("明文是{}".format(plain))
```

4、(循环结构) 输入一个字符串，找出其中最大的字符，输出该字符及其在字符串中的位置。示例运行结果如下:
请输入一串字符: 8wyekindfig
最大字符为: y，其位置为: 2

```python
a=input()
max = a[0]
count=0
num=0
for s in a[1:]:
    count = count + 1
    if s > max:
        max = s
        num = count
print(max)
print(num)
```

5、(循环结构)天天向上续: 每周工作5天，休息2天，休息日水平下降1%，工作日要努力到什么程度一年后的水平才与每天努力1%所取得的效果一样呢？《天天向上的力量》

```python
def dayup(df):    #df表示的的意思为dayfactor 这里为了方便简写了
       dayup=1
       for i in range(365):
              if i % 7 in [6,0]:
                     dayup=dayup*(1-0.01)
              else:
                     dayup=dayup*(1+df)
       return  dayup
              
#上面是定义函数的过程
dayfactor=0.01
while dayup(dayfactor) < 37.78:
       dayfactor+=0.001
print("工作日的期望参数是：{:.3f}".format(dayfactor))
```

6、(顺序结构及分支结构) 汇率兑换程序。以1美元=6人民币的汇率编写一个美元和人民币的双向兑换程序。

```python
Money=input("请输入带有标识的金钱值：")
if Money[-1] in ['r','R']:
    D=eval(Money[0:-1])/6
    print("转换后的美元为{:.2f}".format(D))
elif Money[-1] in ['d','D']:
    R=eval(Money[0:-1])*6
    print("转换后的人民币为{:.2f}".format(R))
else:
    print("输入格式错误")
```

7、(顺序结构及分支结构) 键盘输入三角形的三边长，求三角形周长及面积并输出。(需要考虑三边长是否能够成三角形)

```python
import math
a=eval(input())
b=eval(input())
c=eval(input())

if a+b>c and a+c>b and b+c>a:
    print("周长是{}".format(a+b+c))
    p=(a+b+c)/2
    s=math.sqrt(p * (p - a) * (p - b) * (p - c))
    print("面积是{}".format(s))
else:
    print("无法组成三角形")
```

8、(顺序结构及分支结构) 键盘输入一个三位数，求出其个位数字、十位数字和百位数字并输出。

```python
a=eval(input("请输入一个三位数："))
ge=a%10
shi=a//10%10
bai=a//100
print("个位数字为{}".format(ge))
print("十位数字为{}".format(shi))
print("百位数字为{}".format(bai))
```

## 第七节 函数定义

在python中，本讲义之前编写的代码均未定义函数，因此除循环、条件判断等结构体外，均以从上至下顺序执行，若代码中有一部分代码实现某种特定功能，而在整体代码中需要多次实现这个功能，即可通过定义函数的方式，可以理解为将这部分代码封装为一个函数接口，当主函数（即从上至下顺序执行的代码中）想要实现这个功能时，只需要调用这个函数即可，不需要再重复写一遍实现代码。

```python
#定义一个函数实现两个数求和
def sum(x,y):
    s=x+y
    return s

a=1
b=2
print(sum(a,b))
#print("123")
```

在这段代码中，通过def这个关键字定义了一个函数sum，用来实现两数求和，这两个数在函数中的变量名为x和y，即在函数体中可使用这两个名来使用变量。在执行顺序上，代码会自动跳过所有的def部分。在本代码中即从`a=1`开始执行，执行到第三行print()函数中，发现调用了sum函数，程序会将a，b两变量的值传入sum函数中，调用sum函数部分代码（代码行数第2行到第4行）。最后通过return将变量s返回给主体代码，即给print打印出来。

### 格式

#### 无参数、无返回值

```python
def 函数名():
	代码
```

#### 无参数、有返回值

```python
def 函数名():
	语句
	return 需要返回的数值
```

#### 有参数、无返回值

```python
def 函数名(形参列表):
	语句
```

#### 有参数、有返回值

```python
def 函数名(形参列表):
	语句
	return 需要返回的数值
```

#### 函数使用

```python
#函数的定义
def printinfo():
    print('--'*30)
    print('  人生苦短，我用python  ')
    print('--'*30)

#函数的调用
printinfo()

#带参数的函数
def add2Num(a,b):
    c = a + b
    print(c)
add2Num(11,22)

#带返回值的参数
def add2Num(a,b):
   return a + b
result = add2Num(11,22)
print(result)   #33
print(add2Num(11,22))   #33


# 返回多个值的函数
def divid(a,b):
    shang  = a//b
    yushu  = a%b
    return shang,yushu  #多个返回值用逗号分隔
sh,yu = divid(5,2)  #需要使用多个值来保存返回内容
print('商：%d,余数：%d'%(sh,yu))
```

> 问题1：代码从第几行开始执行
>
> 问题2：第21行，add2Num(11,22)调用了add2Num函数，那11和22在这个函数里的变量名是什么？
>
> 问题3：思考，函数add2Num中的a、b和函数divid中的a、b有什么关系？

## 第八节 面向对象编程

https://www.runoob.com/python/python-object.html

这一部分在非工程编程中几乎可以不用，所以不多赘述，以菜鸟教程代替。

## 第九节 爬虫基础

### 一、Request库

#### 1、request库安装

①同时按下win+R，输入cmd，打开命令行。

②输入`pip install requests`。

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

r.status_code：http请求的返回状态，200表示连接成功，404表示失败，。

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

lxml的HTML解析器：BeautifulSoup(mk,'lxml')需pip install lxml。

lxml的XML解析器：BeautifulSoup(mk,'xml')需pip install lxml。

html5lib的解析器：BeautifulSoup(mk,'html5lib')需pip install html5lib。

BeautifulSoup类的基本元素

Tag：标签，最基本的信息组织单元，分别用<>和</>标明开头或结尾。

Name：标签的名字，<p>...</p>的名字是p，格式：<tag>.name。

Attributes：标签的属性，字典形式组织，格式：<tag>.attrs

NavigableString：标签内非属性字符串，<>...</>中字符串，格式为<tag>.string。

Comment：标签内字符串的注释部分，一种特殊的Comment类型。

#### 4、基于bs4库的HTML内容遍历方法

标签树下行遍历

.contents：子节点的列表，将<tag>所有儿子节点存入列表。

.children：子节点的迭代类型，与.content类似，用于循环遍历儿子节点。

.descendants：子孙节点的迭代类型，包含所有子孙节点，用于循环遍历。

标签树的上行遍历

.parent：节点的父亲标签

.parents：节点先辈（不止父亲）标签的迭代类型，用于循环遍历先辈节点。

标签树的平行遍历

.next_sibling：返回按照html文本顺序的下一个平行节点标签。

.previous_sibling：返回按照html文本顺序的上一个平行节点标签。

.next_siblings：迭代类型，返回按照html文本顺序的后续所有平行节点标签。

.previous_siblings：迭代类型，返回按照html文本顺序的前序所有平行节点标签。

遍历后续节点

```
for sibling in soup.a.next_siblings:
print(sibling)
```

遍历前序节点

```
for sibling in soup.a.previous_siblings:
print(sibling)
```



\#迭代类型只能用在循环中！！！

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

#### 1、正则表达式的概念

用来表达字符串的简洁方式。

通用的字符串表达框架。

字符串匹配。

#### 2、正则表达式的语法

正则表达式长常用操作符

.：表示任何单个字符。

[]：字符集，对单个字符给出取值范围。[abc]表示a,b,c，[a-z]表示a到z的单个字符。

[^ ]：非字符集，对单个字符给出排除范围。`[^abc]`表示非a或非b或非c的单个字符。

*：前一个字符出现0次或无限次扩展。abc`*`表示ab，abc，abcc，abccc等。

+：前一个字符1次或无限次扩展。abc+表示abc，abcc，abcc等

?：前一个字符0次或1次扩展。abc?表示ab、abc。

|：左右表达式任意一个。abc|def表示abc、def。

{m}：表示扩展前一个字符m次。ab{2}c表示abbc。

{m,n}：扩展前一个字符m至n次（含n），ab{1,2}c表示abc、abbc。

^：匹配字符串开头。^abc表示abc且在一个字符串的开头。

$：匹配字符串结尾。abc$表示abc且在一个字符串的结尾。

()：分组标记，内部只能使用|操作符。(abc)表示abc，(abc|def)表示abc、def。

\d：数字，等价于[0-9]。

\w：单词字符，等价于[A-za-z0-9_]。

\#匹配中文字符串：[\u4e00-\u9fa5]

匹配IP地址的正则表达式

IP地址分4段，每段0-255。

(([1-9]?\d|1\d{2}|2[0-4]\d|25[0-5]).){3}([1-9]?\d|1\d{2}|2[0-4]\d|25[0-5])

#### 3、Re库的基本使用

Re库介绍

Re库是python标准库，主要用于字符串的匹配。

调用方式：import re

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

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

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

## 第十节 数据处理

### 一、numpy库（https://www.runoob.com/numpy/）

#### 安装

```bash
pip3 install numpy scipy matplotlib -i https://pypi.tuna.tsinghua.edu.cn/simple
```

使用时需要先import

```python
import numpy as np 
```

#### 数组属性

| 属性             | 说明                                                         |
| ---------------- | ------------------------------------------------------------ |
| ndarray.ndim     | 秩，即轴的数量或维度的数量                                   |
| ndarray.shape    | 数组的维度，对于矩阵，n 行 m 列                              |
| ndarray.size     | 数组元素的总个数，相当于 .shape 中 n*m 的值                  |
| ndarray.dtype    | ndarray 对象的元素类型                                       |
| ndarray.itemsize | ndarray 对象中每个元素的大小，以字节为单位                   |
| ndarray.flags    | ndarray 对象的内存信息                                       |
| ndarray.real     | ndarray元素的实部                                            |
| ndarray.imag     | ndarray 元素的虚部                                           |
| ndarray.data     | 包含实际数组元素的缓冲区，由于一般通过数组的索引获取元素，所以通常不需要使用这个属性。 |

#### 创建数组

`numpy.array(object, dtype = None, copy = True, order = None, subok = False, ndmin = 0)`

| 名称   | 描述                                                      |
| ------ | --------------------------------------------------------- |
| object | 数组或嵌套的数列                                          |
| dtype  | 数组元素的数据类型，可选                                  |
| copy   | 对象是否需要复制，可选                                    |
| order  | 创建数组的样式，C为行方向，F为列方向，A为任意方向（默认） |
| subok  | 默认返回一个与基类类型一致的数组                          |
| ndmin  | 指定生成数组的最小维度                                    |

```python
import numpy as np 
a = np.array([[1,  2],  [3,  4]])  
print (a)


#输出
#[[1  2] 
# [3  4]]
```

```python
# 最小维度  
import numpy as np 
a = np.array([1, 2, 3, 4, 5], ndmin =  2)  
print (a)
#输出[[1 2 3 4 5]]
```

```python
# dtype 参数  
import numpy as np 
a = np.array([1,  2,  3], dtype = complex)  
print (a)

#输出[1.+0.j 2.+0.j 3.+0.j]
```

`numpy.empty(shape, dtype = float, order = 'C')`

numpy.empty 方法用来创建一个指定形状（shape）、数据类型（dtype）且未初始化的数组.

| 参数  | 描述                                                         |
| ----- | ------------------------------------------------------------ |
| shape | 数组形状                                                     |
| dtype | 数据类型，可选                                               |
| order | 有"C"和"F"两个选项,分别代表，行优先和列优先，在计算机内存中的存储元素的顺序。 |

```python
#创建空数组
import numpy as np 
x = np.empty([3,2], dtype = int) 
print (x)

#输出结果
#[[ 6917529027641081856  5764616291768666155]
# [ 6917529027641081859 -5764598754299804209]
# [          4497473538      844429428932120]]
```

`numpy.zeros(shape, dtype = float, order = 'C')`

| 参数  | 描述                                                |
| ----- | --------------------------------------------------- |
| shape | 数组形状                                            |
| dtype | 数据类型，可选                                      |
| order | 'C' 用于 C 的行数组，或者 'F' 用于 FORTRAN 的列数组 |

```python
import numpy as np
 
# 默认为浮点数
x = np.zeros(5) 
print(x)
 
# 设置类型为整数
y = np.zeros((5,), dtype = int) 
print(y)
 
# 自定义类型
z = np.zeros((2,2), dtype = [('x', 'i4'), ('y', 'i4')])  
print(z)

#输出结果
#[0. 0. 0. 0. 0.]
#[0 0 0 0 0]
#[[(0, 0) (0, 0)]
# [(0, 0) (0, 0)]]
```

`numpy.ones(shape, dtype = None, order = 'C')`

创建指定形状的数组，数组元素以 1 来填充

| 参数  | 描述                                                |
| ----- | --------------------------------------------------- |
| shape | 数组形状                                            |
| dtype | 数据类型，可选                                      |
| order | 'C' 用于 C 的行数组，或者 'F' 用于 FORTRAN 的列数组 |

```python
import numpy as np
 
# 默认为浮点数
x = np.ones(5) 
print(x)
 
# 自定义类型
x = np.ones([2,2], dtype = int)
print(x)

#输出结果
#[1. 1. 1. 1. 1.]
#[[1 1]
# [1 1]]
```

`numpy.zeros_like(a, dtype=None, order='K', subok=True, shape=None)`

numpy.zeros_like 用于创建一个与给定数组具有相同形状的数组，数组元素以 0 来填充。

| 参数  | 描述                                                         |
| ----- | ------------------------------------------------------------ |
| a     | 给定要创建相同形状的数组                                     |
| dtype | 创建的数组的数据类型                                         |
| order | 数组在内存中的存储顺序，可选值为 'C'（按行优先）或 'F'（按列优先），默认为 'K'（保留输入数组的存储顺序） |
| subok | 是否允许返回子类，如果为 True，则返回一个子类对象，否则返回一个与 a 数组具有相同数据类型和存储顺序的数组 |
| shape | 创建的数组的形状，如果不指定，则默认为 a 数组的形状。        |

```python
import numpy as np
 
# 创建一个 3x3 的二维数组
arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
 
# 创建一个与 arr 形状相同的，所有元素都为 0 的数组
zeros_arr = np.zeros_like(arr)
print(zeros_arr)
```

`numpy.ones_like(a, dtype=None, order='K', subok=True, shape=None)`

同numpy.zeros_like，只不过是用1填充。

`numpy.arange(start, stop, step, dtype)`

numpy 包中的使用 arange 函数创建数值范围并返回 ndarray 对象，根据 start 与 stop 指定的范围以及 step 设定的步长，生成一个 ndarray。

| 参数  | 描述                                                         |
| ----- | ------------------------------------------------------------ |
| start | 起始值，默认为0                                              |
| stop  | 终止值（不包含）                                             |
| step  | 步长，默认为1                                                |
| dtype | 返回`ndarray`的数据类型，如果没有提供，则会使用输入数据的类型。 |

```python
#生成 0 到 4 长度为 5 的数组:
import numpy as np
 
x = np.arange(5)  
print (x)

#输出结果：[0  1  2  3  4]
```

```python
#设置了起始值、终止值及步长：
import numpy as np
x = np.arange(10,20,2)  
print (x)

#输出结果：[10  12  14  16  18]
```

`np.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None)`

用于创建一个一维数组，数组是一个等差数列构成的

| 参数       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| `start`    | 序列的起始值                                                 |
| `stop`     | 序列的终止值，如果`endpoint`为`true`，该值包含于数列中       |
| `num`      | 要生成的等步长的样本数量，默认为`50`                         |
| `endpoint` | 该值为 `true` 时，数列中包含`stop`值，反之不包含，默认是True。 |
| `retstep`  | 如果为 True 时，生成的数组中会显示间距，反之不显示。         |
| `dtype`    | `ndarray` 的数据类型                                         |

`np.logspace(start, stop, num=50, endpoint=True, base=10.0, dtype=None)`

创建一个于等比数列

| 参数       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| `start`    | 序列的起始值为：base ** start                                |
| `stop`     | 序列的终止值为：base ** stop。如果`endpoint`为`true`，该值包含于数列中 |
| `num`      | 要生成的等步长的样本数量，默认为`50`                         |
| `endpoint` | 该值为 `true` 时，数列中中包含`stop`值，反之不包含，默认是True。 |
| `base`     | 对数 log 的底数。                                            |
| `dtype`    | `ndarray` 的数据类型                                         |

#### 切片

slice

```python
import numpy as np
 
a = np.arange(10)
s = slice(2,7,2)   # 从索引 2 开始到索引 7 停止，间隔为2
print (a[s])

#输出[2  4  6]
```

直接切

```python
import numpy as np
 
a = np.arange(10)  
b = a[2:7:2]   # 从索引 2 开始到索引 7 停止，间隔为 2
print(b)
#输出：[2  4  6]
```
