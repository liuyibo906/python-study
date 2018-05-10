# A byte of python note

### 格式化字符串
```
age=20                                          
name='liuyb'                                       
print('{} is {} years old'.format(name,age)) 
```
### 小数点后保留6为小数
```
print('{0:.6f}'.format(1.0/3))
```
### 转义字符
```
print('this is the first line.\nthis is the second line.') 
```
### 原始字符串用r或R
```
print(r'this's a new message')
```
### 如果一个字符串很长，可以使用\来换行
```
s='this is a very \
long story'
```
### 运算符
* / 除
* // 取整
* % 取余
 ### 控制流
 * if 语句
```
number=10
guess=int(input('please input a number'))
if guess==number:
    print('correct')
elif guess<number:
    print('too little')
else:
    print('too large')
print('done')
```
* while 语句
```
number=10
count=0
while True:
    count+=1
    print('this is the',count ,'times')
    guess=int(input('please input a number'))
    if guess==number:
        print('correct')
        break
    elif guess<number:
        print('too little')
    else:
        print('too large')
```
### 函数
```
#无参数函数
def sayhello():
    print('hello world')
sayhello()
#带参数函数
def max(a,b):
    if a>=b:
        print(a)
    else:
        print(b)
max(23,8)

#局部变量
x=5
def fun(x):
    print('x is',x)
    x=2
    print('change x to',x )
fun(5)
print('now x is',x)


#globle 语句
x=5
def fun():
    global x
    print('x is',x)
    x=2
    print('change x to',x )
fun()
print('now x is',x)

#默认参数
def say(message,times=1):
    print(message*times)
say('liuyb')
say('liuyb',5)

#关键字参数
def func(a,b=5,c=10):
    print('a is', a,'b is',b,'c is',c)
func(3,7)
func(10,c=20)
func(c=100,a=200)

# 可变参数
# *pare 标示元组 **para 代表字典
# 调用total.__doc__ 显示行数说明文档
def total(a,*numbers,**phonebook):
'''
this is a Docstring 
'''
    print('a is',a)
    for member in numbers:
        print('member is',member)
    for first_part,second_part in phonebook.items():
        print(first_part,second_part)
total(10,1,2,3,jack=135,rose=125,kay=188)
```

### 模块
```
import sys
print('The command line arguments are:')
print( sys.path)
#导入模块中一个函数
from math import sqrt
print('square root of 16 is',sqrt(16))
```
#### dir函数，返回对象定义的名称列表，如果对象为模块，则返回这一指定模块的名称列表，如果没有指定参数，则返回当前模块的名称列表。

### 数据结构
* python有4中内置的数据结构，list,tuple,dict,set
* 列表list有许多方法，列表使用方括号
```
list1=[9,5,8,7]
list1.append(9) #新增
list1.sort() #排序
len(list1) #list1的长度
del list1[0] #删除元素
```
* 元组tuple,使用括号（括号可以没有），不可改变
```
zoo=('lion','shark','rabit')
len(zoo) #长度
如果元组中只包含一个元素需要如下方式定义
number=(2,)
```
* 字典dict,键值之间通过冒号间隔，每一对键值之间通过逗号间隔，使用花括号包括，字典键不能重复，字典不能排序。
```
ab={'jack':'jack@fsc','rose':'rose@fsc','link':'link@fsc'}
ab['hose']='hose@fsc' #添加键值
del ab['jack'] #删除元素
for i,j in ab.items():
    print(i,j)

```


* 序列（sequence） 列表、元组和字符串可以看做是序列的某种表现形式，序列的主要功能是资格测试（in 或not in）和索引操作，拥有切片计算符
```
shoplist = ['apple', 'mango', 'carrot', 'banana']
shoplist[1:3] #索引从0开始，不包含end数字
shoplist[:2:1] #start:end:sep  步长
```
* 集合（set） 集合的内容是不重复的
```
shoplist = ['apple', 'mango', 'carrot', 'banana']
set1=set(shoplist)
set1.remove('apple') #去除元素
set1.add('dog') #添加元素
set2.issuperset(set1) #set2是否包含set1
```


### 自动备份目录
```
def backup():
    source = ['E:\\t2', 'E:\\t3']
    print(' '.join(source))
    target_dir = 'E:\\Backup'
    import os
    print(os.sep)
    import time
    target=target_dir + os.sep+time.strftime('%Y%m%d%H%M%S')+'.zip'

    if not os.path.exists(target_dir):
        os.mkdir(target_dir)
    zip_command = 'zip -r {0} {1}'.format(target,
    ' '.join(source))
    print(zip_command)
    if os.system(zip_command)==0:
        print('successful backup to', target_dir)
    else:
        print('backup failed')

backup()
```






















