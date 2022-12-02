> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.52pojie.cn](https://www.52pojie.cn/thread-1721431-1-1.html)

> [md]# python 学习 ## 字符串类型 ### 1. 字符串内型表示 ```pythonprint('内容使用" 我 "')print(" 内容'我'")print('''三引号表示'我'和" 她 " 还 ........

![](https://avatar.52pojie.cn/images/noavatar_middle.gif)haoerapython 学习
=========

字符串类型
-----

### 1. 字符串内型表示

```
print('内容使用"我"')
print("内容'我'")
print('''三引号表示'我'和"她"还有换行''')
'''

内容使用"我"
内容'我'
三引号表示'我'和"她"还有换行

```

```
name = "woaipython"
print(name[0:2])<字符串可以直接当做列表去检索>
print(name)
"wo"
"woaipython"
print("ab\ncde\tfj\\ihfw\"ei\'") <!\n:换行   \t:（tab）  \”：" \':'>
ab
ncde  \ ihfw"ei'

name = "woaipython"
print(name[0:2])<字符串可以当作列表去检索>

'wo'

```

内置字符串处理函数

```
len(x) # <返还字符串长度>
str(x) <将任意类型返还为对应字符串类型>
hex(x) <将整形返还为16进制小写字符串>
hex(255)
'0xff'
oct(x) <将整形返还为8进制小写字符串>

ord(x)<单字符的unicode编码>
chr(x)<unicode编码的单字符>

str.lower()<返还str全小写>
str.upper()<返还str全为大写>

```

format() 函数的使用

```
s = 'PYTHON'
print("{1},{2},{4},{3}".format('e','s','sd','e'))<排序输出>
运行结果：'e','s','e','sd'
print("{0:30}.format(s))<默认左对齐>
{0:>30}.format(s)<右对齐>
{0:*^30}.format(s)<居中并使用*补齐>

     print("{:>15s}:{:<8.2f}".format("Length",2342.4342))
       运行结果：    Length:2342.43 

{0:.2f}.format()<对于浮点数小数部分保留两位有效数字>
{0:.4}.format(s)<对于字符串输出最大长度4>
{0:b}.format(int)<输出整形的二进制数>  <b2,cUnicode,d10,o8,x16(小写)，X16(大写)>     

```

print 的一些简单用法

```
a = '*'*9
print(a)
#运行结果*********
#print()默认换行，print(x,end="")结尾以空

```

程序控制结构
------

### 1. 分支结构

分支结构 if - elif-else

```
'''
基本语法：if 判断条件 ：
             执行内容
          elif 判断条件 ：
             执行内容
          ......
        else ：
             执行内容
 '''
#学生成绩评级
a =  eval(input("请输入成绩："))
if 60 <= a <= 70:
    print("D")
elif 70 < a <= 80:
    print("C")
elif  80 < a <= 90:
    print("B")
elif 90 < a <=100:
    print("A")
elif a > 100 or a < 0:
    print("你在逗我玩？")
else:
    print("不及格重修")

```

### 2. 程序循环结构

for 循环

```
'''
基本语法：for <循环变量> in <遍历结构>
             <循环的语句块>
'''
x = "i"
for x in  "python":
     print(x)
'''
     运行结果：p
             y
             t
             h
             o
             n
x相当于遍历了一遍"python"
'''


```

无限循环：while

```
'''
while <条件>:
   <语句块>
'''

```

### 3. 循环保留字

break 与 contine

```
''''''
break只能跳出最内层循环
continue跳出当前这一次循环
''''''
for s in "python":
    if s == 't':
        break
    print(s,end="")
print("\n")
for s in "python":
    if s == 't':
        continue
    print(s,end="")
''''''
运行结果：py

        pyhon


```

### 4.random 库

```
''''''
random库引用：
            import random
        或
            from random import*
常用函数：
      seed(a=None)：初始化种子，种子相同每次生成的数也相同
      random():生成一个[0.0,1.0）的随机小数
      randint(a,b):生成一个[a,b]的整数
      getrandbits(k):生成一个kbit长的整数
      rangrange(start,stop,[,step])：生成一个[start,stop)之中step为步长的整数
      uniform(a,b):生成一个[a,b]间的小数
      choic(seq)；生成一个从序列类型（列表）中的一个元素
      shuffle(seq):将序列的元素随机打乱生成一个新序列
      sample(pop,k):在pop类型中随机取k个元素并以列表类型返回
''''''
from random import* 
seed(213)                                         
a_list = ['apple','pear','peach','orange']
print(choice(a_list))                                         
#运行结果为四个元素中随机一个并且不管重试几次都不变  

```

### 5. 程序异常处理

异常处理：try-except 语句

```
'''
基本语法：
try :
    <语句块1>

except <异常类型>:
    <语句块2>

---------
except:
---------

注：程序的异常和错误是不同的，错误表现在语法上，
'''
try :
    name = 'python'
    numbers = eval(input("请输入一个整数"))
    print(name[numbers])
except NameError:
    print("输入错误，请输入一个整数")

except:
    print("其他错误")
'''
当用户输入的不是整数时错误被except NameError:捕获到
如：
请输入一个整数python
输入错误，请输入一个整数
当用户输入的整数超出[0,5]时错误被except:捕获
如：
请输入一个整数32
其他错误

异常语句还可以与 else 和 finally 配合使用
try :
    <语句块1>

except <异常类型>:
    <语句块2>
else:
    <语句块3>
finally:
    <语句块4>

其中else是try中语句执行结束且没有发现异常才执行，而finally是一定会执行的用于对try的一些收尾工作（关闭文件或是打开文件） 


```

函数和代码的复用
--------

### 1. 函数的基本使用

```
'''
def <函数名> (<参数列表>):
    <函数体>
    return<返回值列表>
    当我们定义一个全局变量时，在函数中还要声明global n
'''


```

### 2.lambda 函数

```
'''
<函数名> = lambda <参数列表>: <表达式>
lambda函数简单来说就是能在一行内定义的函数

'''
f = lambda x,t:x*t
print(f(2,3))
#运行结果为：6

```

### 3.datetime 库的使用

```
'''
datetime库是python提供的一个事件处理标准库
datetime.date:年月日
datetime.time:时分秒毫秒
datetime.datetime:date+time
datetime.timedelta:时间间隔有关的类
datetime.tzinfo:时区有关类
调用方式：from datetime import datetime
'''
from datetime import datetime
today =datetime.now()
print(today)
#返还现在的时间精确到微秒：2022-1-11 22:21:07.698629
#即返还一个datetime(year,month,day,hour,minute,second,microsecond)
#datetime.utcnow()返还世界标准时间utc

'''
我们也可以直接创建datetime对象
datetime(2022,1,11,22,21,07,6829822)
为了区分datetime库名用sometimed代替
sometime = datetime(.......)
sometime.<小时、年、分......所需，或min最小时间对象max最大时间对象> = sometime

格式化：
someday.isoformat()采用ISO 8601标准显示时间
someday.isoweekday()返还星期几
someday.strftime(format)格式化显示
如：someday.strftime("%Y-%m-%d %H:%M:%S)（区分大小写）
输出：年-月-日 时：分：秒
'''
from datetime import datetime
today =datetime.now()
sometime = datetime.now()
print(sometime.year)

print(sometime.day)
print(today)

''''
输出
2022
11
2022-11-11 22:32:48.191624
'''


```

### 4.turtle 库的简单学习

```
'''
turtle库是python中的一个直观图形绘制函数库

turtle.setup(窗口宽，窗口高，x轴，y轴)
画笔控制函数：
turtle.up() = turtle.penup(无) =turtle.pu()<提起画笔，之后移动画笔不会绘制形状>

turtle.down() = turtle.pendown(无) =turtle.pd<落下画笔，之后移动画笔将会绘制形状>

turtle.pensize() = turtle.width() <设置画笔尺寸>

turtle.pencolor("blue")<设定画笔颜色，无参数时返回当前画笔颜色>

形状绘制函数：
turtle.fd(distance) = turtle.forward(distance)<向小海龟当前方向前进distance距离>
turtle.seth("角度逆时针为正")<设置小海龟当前前进方向>
turtle.circle(弧形半径，绘制的弧形角度无参画整圆)<绘制弧形>

turtle.speed(速度)<画笔速度>

turtle.done():暂停运行结果
turtle.mainloop():用于维持窗口,为了解决画完闪退

fillcolor("red"):设置填充色为红色
left(90)<左转90度>
setheading( to_angle)，功能时设置海龟的朝向为 to_angle。

turtle.write(arg(信息),move(可选：ture/false),align(可选：left/center/right表示信息对齐方式),font=('字体','字体','字体')（可选）)<在乌龟当前位置写入信息>

'''

from turtle import*             #调用turtle库
from datetime import datetime   #调用datetime库
import math                      # 调用math库
import time

tracer(False)  #tracer(False)的时候，我们关闭了轨迹。也就是说，它的整个爬行的过程对程序员是不可见的
title("时钟") #主题
penup()#保持画笔抬起

#画点
left(90)
for a in range(60):
    x = 250*math.sin(a/30*math.pi)
    y = 250*math.cos(a/30*math.pi)
    goto(x,y)
    dot(7)

#画杠
setheading(60)
pensize(10)

for a in range(1,13):
    x = 250*math.sin(a/6*math.pi)
    y = 250*math.cos(a/6*math.pi)
    goto(x,y)

    pendown()
    forward(20)
    penup()

    write(a , font = ('Times New Roman',20,'normal','bold'))
    right(30)

setheading(0)

#刷新的指针

while True:
    T = datetime.now()
    hour = 30*T.hour + T.minute/2 + T.second/120
    minute = 6*T.minute + T.second/10
    second = 6*T.second

    #时
    goto(0,0)
    setheading(90-hour)
    pendown()
    pensize(7)
    forward(120)
    penup()

    #分
    goto(0,0)
    setheading(90-minute)
    pendown()
    pensize(7)
    forward(150)
    penup()

    #秒
    goto(0,0)
    setheading(90-second)
    pendown()
    pensize(2)
    forward(170)
    penup()

    goto(0,-160)
    day = T.strftime("%Y-%m-%d %H:%M:%S")
    write(day,align = 'center',font = ('Time New Roman',20,'normal'))

    #刷新
    update()
    time.sleep(0.1)
    for a in range(18):
        undo()

mainloop()
done()


```

python 中 goto() 语句可以在代码之间随意的跳来跳去,(在 turtle 中可以理解为跳到这个坐标)，不要轻易使用 goto，因为 goto 会使你的代码逻辑变的极其混乱。但是有时候我们不得不用它，因为它太高效了。比如进入循环内部深层一个 goto 就能回到最上层，还有可以定位到代码的任意一个位置，很是高效方便。但是也不要所有的代码都用 goto，那样你的代码就变得像量子世界那样诡异，连你自己都控制不了。最后一句忠告，能不用 goto 最好就不用。

### 5. 函数的递归

``` 递归的定义  
函数可以被其他函数调用，当然也可以被自己调用即递归

```
```python
def sum(n):
    if n == 0:
        return 0
    else:
        return n + sum(n-1)
num = eval(input("请输入一个整数"))#在Python3中，input()函数接受一个标准输入数据，返回为string类型。使用eval()将其转化为 
#一个可执行的数据
print(sum(abs(int(num))))
'''
运行结果：
请输入一个整数12
78
'''

```

[https://www.runoob.com/python/python-built-in-functions.html](https://www.runoob.com/python/python-built-in-functions.html)

组合数据类型
------

### 1. 序列类型

``` 序列类型  
相当于一维元素向量，存在先后顺序，可通过序号访问

```
#### 元组（tuple）

元组是较为特殊的序列，它一旦创建就不能去更改或是删除

```python
num = ('1','wefwe','124','411w')
print(num)         #可直接输出
color = num *2     #将num复制两遍
print(color)
he = color + num   #可直接连接
print(he)   
dis = '1' in he    #可直接查找
print(dis)
print(he.count('1'))#使用count()计算出现次数
print(he.index('1',1,7))#使用index()第一次出现该元素的位置
print(min(num))      #计算出元素的最小值
print(max(num))    #计算出元素的最大值

'''
运行结果：
('1', 'wefwe', '124', '411w')
('1', 'wefwe', '124', '411w', '1', 'wefwe', '124', '411w')
('1', 'wefwe', '124', '411w', '1', 'wefwe', '124', '411w', '1', 'wefwe', '124', '411w')
True
3
4
1
wefwe
'''

```

```
#当一个元组是另一个元组的元素时
s = (1,2,32,'23',23,23)
sn = (1,2,3,s)
print(sn[-1][2])#输出s元组的三个元素即输出32
snn = s[0:5:2]#对元组0~5进行切片且步长为2(1, 32, 23)

```

#### 字符串与列表

操作与元组差不多，只是可以去增减修改，列表与元组一样它们可以是由不同数据类型组成并且元素可以是相同的有序的

"ehweuifhuwui"<字符串>

[1,2,3,3,4,4]< 列表 >

```
s = [1,2,3,4,5]
z = s
del s[0:1]     #删除0~1之间的元素
print(s)   
del s[0:2:2]   #删除0~2之间以2为步长的元素
print(s)
z.append(6)    #在z尾加上元素6

print(z)
y = s.copy()   #将s复制给y
print(y)

s.clear()      #清除s中的元素
print(z)
print(y)
y.insert(0,100)#在0这个位置上加上元素100
print(y)
y.pop(0)       #删除0这个位置上的元素
print(y)
y.remove(6)   #删除第一个出现的6
print(y)
y.reverse()   #反转列表
print(y)

'''
[2, 3, 4, 5]
[3, 4, 5]
[3, 4, 5, 6]
[3, 4, 5, 6]
[]
[3, 4, 5, 6]
[100, 3, 4, 5, 6]
[3, 4, 5, 6]
[3, 4, 5]
[5, 4, 3]
'''


```

注意：当我们直接将 a = s 时这里我们的 s 与 a 是等价的改变 a 或 s 另一个会跟着变，而 y = s.copy() 则是建立了一个新的个体 s 的变化与 y 无关

```
a = [1,2,3,4,5]
s = a
y = a.copy()
s.append(1000)
print(a)
print(y)
'''
[1, 2, 3, 4, 5, 1000]
[1, 2, 3, 4, 5]
'''

```

### 2. 集合类型

``` 集合  
集合是有数据类型固定（整数、浮点数、字符串、元组等）且元素不可重复的由 0 或多个元素组成的无序可变组合，用 {} 表示

```
```python
#python提供了set（集合）数据类型
w = set("apple")#set(x)函数生成任意无重复无序的集合
print(w)
#运行结果{'a', 'l', 'p', 'e'}
'''
操作符
    S-T或S.difference(T) 返回一个新集合在S但不在T
    S-=T或S.difference(T)更新集合S取在S但不在T的元素并返回S，
    同理&：集合与   ^:集合求异 |：集合并  <=:判断是否为子集  >=:判断是否为超集
'''

s = {1,2,2,3,4,5,7}
sn = {1,2,3,5}
print(s)#自动剔除相同项
print(s-sn)
z = s.copy()#复制集合
#集合无法像字符串或是列表、元组一样直接将一个集合赋给另一个集合
s-=sn         #s取s与sn的不同元素
print(s)
print(z&sn)   #取同
print(z^sn)   #取异
print(z>=sn)  #判断超集
z.add(9)      #当集合中无x元素则加入
print(z)
z.remove(9)   #当集合中有x元素则删除不在则报错
print(z)
z.discard(1)#当集合中有x元素则删除无也不报错
print(z.pop())      #随即返还一个集合中的元素空则返还异常
z.clear()     #清除集合中所有元素并返还集合类型set()
print(z)

d = [2,2,2,21,2]
z = d
print(z)

'''
运行结果：
{1, 2, 3, 4, 5, 7}
{4, 7}
{4, 7}
{1, 2, 3, 5}
{4, 7}
True
{1, 2, 3, 4, 5, 7, 9}
{1, 2, 3, 4, 5, 7}
2
set()
[2, 2, 2, 21, 2]


```

### 3、字典

字典采用键值对的方式表达：Dcounttry={"北京"："首都，" 中国 ":" 国家 "}

字典的每个键值 key:value 对用冒号 : 分割，每个键值对之间用逗号 , 分割，整个字典包括在花括号 {}

注意：  当我们采用 print 去打印字典时顺序是不一致的，**字典的各个元素没有顺序之分**，我们要保持一个集合的顺序应用列表

```
'''
字典的直接用法：
<值>=<字典变量>[<键>]
'''
Dct = {}
Dct['数字'] = 3#调用时或赋值时键用[]
print(Dct)    #可以直接输出字典
#运行结果：{'数字': 3}

```

**键一般是唯一的，如果重复最后的一个键值对会替换前面的，值不需要唯一。**

**值可以取任何数据类型，但键必须是不可变的，如字符串，数字或元组。**

```
A = 'a'
Dct = {A:2,A:3,A:4}
Dct['数字'] = 3
print(Dct)
#{'a': 4, '数字': 3}

```

#### 字典内置函数 & 方法

Python 字典包含了以下内置函数：

函数及描述  
1、cmp(dict1, dict2)**python3.2.2 之后已删除**  
比较两个字典元素。**先比较字典长度即 len(dict1) 与 len(dict2),1>2 返回正值、1<2 返回负值、1=1 返回 0（比较字典键（先）和值（后）做出判断）**

2、  len(dict)  
计算字典元素个数，即键的总数。  
3、  str(dict)  
输出字典可打印的字符串表示。  
4、  type(variable)  
返回输入的变量类型，如果变量是字典就返回字典类型。

```
dict1 = {'a':1,'b':2,'c':3,'d':4}
dict2 = {'a':1,'b':2,'c':3,'d':4,'e':5}
print(len(dict2))
print(type(dict1))
print(str(dict2))

'''
5
<class 'dict'>
{'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
'''

```

1   dict.clear()  
删除字典内所有元素  
2   dict.copy()  
返回一个字典的浅复制  
3   dict.fromkeys(seq[, val])  
创建一个新字典，以序列 seq 中元素做字典的键，val 为字典所有键对应的初始值  
4   dict.get(key, default=None)  
返回指定键的值，如果值不在字典中返回 default 值  
5   dict.has_key(key)  
如果键在字典 dict 里返回 true，否则返回 false  
6   dict.items()  
以列表返回可遍历的 (键, 值) 元组数组  
7   dict.keys()  
以列表返回一个字典所有的键  
8   dict.setdefault(key, default=None)  
和 get() 类似, 但如果键不存在于字典中，将会添加键并将值设为 default  
9   dict.update(dict2)  
把字典 dict2 的键 / 值对更新到 dict 里  
10  dict.values()  
以列表返回字典中的所有值  
11  pop(key[,default])  
删除字典给定键 key 所对应的值，返回值为被删除的值。key 值必须给出。 否则，返回 default 值。  
12  popitem()  
返回并删除字典中的最后一对键和值。

```
dict1 = {'a':1,'b':2,'c':3,'d':4}
dict2 = {'a':1,'b':2,'c':3,'d':4,'e':5}
print(dict1.keys())   #返回键
print(dict1.values()) #返回值
print(dict1.items())  #返回键值
print(dict1.get('d')) #返回键对应值，不存在则None
dict1.pop('d')        #返回键对应值并删除键值对
print(dict1.get('d')) 
s = 'd' in dict1      #判断键在字典中
dict1.clear()         #清空字典
print(dict1.items())  

'''
dict_keys(['a', 'b', 'c', 'd'])
dict_values([1, 2, 3, 4])
dict_items([('a', 1), ('b', 2), ('c', 3), ('d', 4)])
4
None
dict_items([])
'''

```

**通过 list() 函数将字典转化为列表**

```
dict1 = {'a':1,'b':2,'c':3,'d':4}
dict2 = {'a':1,'b':2,'c':3,'d':4,'e':5}
print(list(dict1.keys()))
print(list(dict1.values()))
print(list(dict1.items()))
for key in dict1:     
    print(dict1[key],end = ' ')
'''
['a', 'b', 'c', 'd']
[1, 2, 3, 4]
[('a', 1), ('b', 2), ('c', 3), ('d', 4)]
1 2 3 4 
'''    

```

### 4、jieba 库的使用

```
'''
对于英文文本："china is a great country"使用split()函数可以提取其中的单词
并转化为列表形式
split()可以将字符串通过空格位间隔分开
'''
str1 = "china is a great country".split()
str2 = "china shi zui liu bi de"
print(str1)
print(str2.split())

'''
运行结果：
['china', 'is', 'a', 'great', 'country']
['china', 's', 'zui', 'liu', 'bi', 'de']
'''

```

对于中文文本，词语间缺少分隔符则要使用结巴库 https://pypi.org/project/jieba/

下载：pip3 install jieba

在 IDLE 中 import jieba 不报错说明安装成功

#### 1.jieba.cut()  jieba.lcut

###### 1.1 精确模式

cut() 返回一个可迭代的数据类型（需要遍历，不能直接 print）

lcut() 返回一个列表

```
import jieba
str1 = "嘿嘿嘿，不吃好的不吃贵的，今天整点嘎嘣脆的"
str2 = jieba.cut(str1)
print(str2)
#运行结果<generator object Tokenizer.cut at 0x000001850CC13EB0>

import jieba
str1 = "嘿嘿嘿，不吃好的不吃贵的，今天整点嘎嘣脆的"
str2 = jieba.cut(str1)
for a in str2:
    print(a,end = ' ')#取消换行，用空格取代

#运行结果 嘿嘿嘿 ， 不吃 好 的 不吃 贵 的 ， 今天 整点 嘎嘣脆 的 


```

###### 1.2 全模式

jieba.cut(str,cut_all = Ture)  jieba.lcut(str,cut_all = Ture)

将所有可能组合都展现出来

```
import jieba
str1 = "我是中国人爱国爱党爱人民"
str2 = jieba.cut(str1,cut_all = True)
for a in str2:
    print(a,end = ' ')#取消换行，用空格取代
#我 是 中国 国人 爱国 爱党 爱人 人民 

```

##### 1.3 搜索引擎模式

lcut_for_search(str)  cut_for_search(str)

将结果精确分开，对较长次二次切分

```
import jieba
str1 = "混沌未分天地乱，茫茫渺渺无人见。自从盘古破鸿蒙，开辟从兹清浊辨。覆载群生仰至仁，发明万物皆成善。欲知造化会元功，须看西游释厄传。"
jieba.add_word("未分")#新增分词
str2 = jieba.lcut_for_search(str1)
for a in str2:
    print(a,end = ' ')#取消换行，用空格取代

```

```
import jieba #导入结巴库
import jieba
str = "你觉得你可以杀死我？木瓜星灵你该死！"
jieba.add_word("星灵")#向分词词典加入新词
print(jieba.lcut(str))#精确模式，返回一个列表
print(jieba.lcut(str,cut_all=True))#全模式返回所有分词，返回一个列表
print(jieba.lcut_for_search(str))#搜索引擎模式，返回一个列表，先做精确模式再对长词进一步分析
'''
Building prefix dict from the default dictionary ...
Loading model from cache C:\Users\SHANGX~1\AppData\Local\Temp\jieba.cache
Loading model cost 0.710 seconds.
Prefix dict has been built successfully.
['你', '觉得', '你', '可以', '杀死', '我', '？', '木瓜', '星灵', '你', '该死', '！']
['你', '觉得', '你', '可以', '杀死', '我', '？', '木瓜', '星灵', '你', '该死', '！']
['你', '觉得', '你', '可以', '杀死', '我', '？', '木瓜', '星灵', '你', '该死', '！']
'''


```

当我们要自组词汇时

```
import jieba
str = "你在干鸡毛"
print(jieba.lcut(str))
jieba.add_word("干鸡毛")#jieba.del_word()删除分词
print(jieba.lcut(str))
'''
Building prefix dict from the default dictionary ...
Loading model from cache C:\Users\SHANGX~1\AppData\Local\Temp\jieba.cache
Loading model cost 1.100 seconds.
Prefix dict has been built successfully.
['你', '在', '干', '鸡毛']
['你', '在', '干鸡毛']
'''

```

文件和数据格式化
--------

### 1. 文件打开与关闭

python 中使用 open(文件名，访问模式) 函数去打开或创建一个文件（文件可以是文本文件、二进制）

如：![image-20221130162118810]([https://img-blog.csdnimg.cn/28d42e21719643f6b36495ce0bb831ea.png](https://img-blog.csdnimg.cn/28d42e21719643f6b36495ce0bb831ea.png)

有则打开无则创建

python 中使用 close() 关闭文件

```
f = open('wuyong.txt','w')
f.close()#关闭此文件


```

##### 1.1 访问模式解释

r : 只读，**指针默认在文件头**

w: 只写，**文件存在则覆盖，文件不存在则创建**

a; 追加，**文件存在则指针在文件尾，即在文件尾写入新内容，若文件不存在则创建后再写入**

rb: **二进制格式**只读

wb：**二进制格式**只写

ab：**二进制格式**追加

r+: 打开一个文件读写，**指针在头**

w+: 打开一个文件并覆盖或创建一个新文件读写

a+: 打开一个文件读写，**有则指针在尾追加无则创建**

rb+: 读写

wb+：读写

ab+：追加

### 2. 文件读写

写用 write（）函数

```
f = open("wuyong.txt",'w')#打开文件，模式为写，不存在则创建
f.write("wo hao xiang bu tai cong ming")
f.close()

```

写入后用 read() 读

```
f = open("wuyong.txt",'r')
str = f.read(123)#一次读取123个字符
print(str)
f.close()#关闭此文件

```

全读出来 readlines() 等同于 read（）无参数

readlines() 返还一个列表

readline（）一次读取一行

```
f = open("wuyong.txt",'w')#打开文件，模式为写，不存在则创建
f.write("wo hao xiang bu tai cong ming")
f.write("ni shuo de dui !")
f.write("ni xiao zi shi qian zhou")

f = open("wuyong.txt",'r')
str = f.read()#一次读取123个字符
str2 = f.readlines()#数据已全被取走，读不出
print(str)
print(str2)
f.close()#关闭此文件
'''
wo hao xiang bu tai cong mingni shuo de dui !ni xiao zi shi qian zhou
[]
'''


```

### 3. 文件其他操作

python 的 os 模块中有一些我常用的文件相关操作如：重名名、删除文件

#### 3.1 文件重命名

使用 rename("被重命名文件名"，"新文件名")

```
import os
rename("wuyong.txt","wuyong1.txt")

```

#### 3.2 文件删除

使用 os 模块的 remove("待删文件名")

```
import os
os.remove("wuyong1.txt")

```

#### 3.3 创建文件夹

使用 os.mkdir("文件夹名")

#### 3.4 获取当前目录、改变默认目录

```
import os
os.getcwd()
os.chdir("../.")

``` ![](https://avatar.52pojie.cn/data/avatar/000/52/81/95_avatar_middle.jpg)yjn866y [Python] _纯文本查看_ _复制代码_

```
s = 'PYTHON'
print("{1},{2},{4},{3}".format('e','s','sd','e'))<排序输出>
运行结果：'e','s','e','sd'

```

这段代码在运行时会出现错误提示，IndexError: Replacement index 4 out of range for positional args tuple  
分析原因是 format() 里，（）内元组的元素个数不够造成的。![](https://avatar.52pojie.cn/images/noavatar_middle.gif)lml521 刚好学习一下 ![](https://avatar.52pojie.cn/data/avatar/000/47/93/36_avatar_middle.jpg)平淡最真 牛的拼音是 niu  
![](https://static.52pojie.cn/static/image/smiley/default/lol.gif) ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) 正在学习，感谢分享 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) bennyt 看看学习 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) xiaoqia0 好东西先收藏了 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif) xszraa 进来学习… 感谢分享![](https://avatar.52pojie.cn/images/noavatar_middle.gif)不会想象的明天 感谢分享![](https://avatar.52pojie.cn/images/noavatar_middle.gif)woajs 感谢分享 ![](https://avatar.52pojie.cn/images/noavatar_middle.gif)zhcj66 学习学习，谢谢分享。![](https://static.52pojie.cn/static/image/smiley/default/17.gif)