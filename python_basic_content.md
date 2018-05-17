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

* 1 < 2 < 3 #=> True
* 2 < 3 < 2 #=> False
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
    import time
    import os
    source = ['E:\\t2', 'E:\\t3']
    print(' '.join(source))
    target_dir = 'E:\\Backup'
    if not os.path.exists(target_dir):
        os.mkdir(target_dir)
    today=target_dir+os.sep+time.strftime('%Y%m%d')
    now=time.strftime('%H%M%S')
    comment=input('please input the change:')
    if len(comment)==0:
        target=today+os.sep+now+'.zip'
    else:
        target=today+os.sep+now+comment.replace(' ','_')+'.zip'
    if not os.path.exists(today):
        os.mkdir(today)
    zip_command = 'zip -r {0} {1}'.format(target,
    ' '.join(source))
    print(zip_command)
    if os.system(zip_command)==0:
        print('successful backup to', target)
    else:
        print('backup failed')

backup()
```

### 面向对象编程
* 类(class),类方法和普通函数的区别是，类方法必须要有一个self参数在参数列表开头，但是在调用是不用为他赋值，python会为他提供
* python为self变量赋值的过程：myclass类的实例myobject调用类方法myobject.method(arg1,arg2) python 会自动转换为myclass.method(myobject,arg1,age2)
* 用class关键字和类的名称来创建类，在他之后是一个缩进的语句块，代表这个类的主体，用类名加一个括号创建一个类的实例（或对象）
```
class Person:
    pass # 一个空的代码块
p = Person()
print(p)
```


* 方法 类和对象如函数一样可以有方法，唯一的不同是类方法必须有self参数
```
class Person:
    def sayhi(self):
        print('hello world')
p = Person()
p.sayhi()
```

* __init__方法会在对象被实例化是立即运行，可以对操作的目标进行初始胡操作,self.name 是对象self 的一部分，name是一个局部变量
```
class Person:
    def __init__(self,name):
        self.name=name
    def sayhi(self):
        print(self.name)
p = Person('case')
p.sayhi()
```


* 类变量和对象变量,类变量是共享的，可以被类任意对象引用，对象变量是独立对象所有的，不共享
```
class Robot:
    """表示有一个带有名字的机器人。"""
    # 一个类变量，用来计数机器人的数量
    population = 0
    def __init__(self, name):
        """初始化数据"""
        #self.name 是对象变量
        self.name = name
        print("(Initializing {})".format(self.name))
        # 当有人被创建时，机器人
        # 将会增加人口数量
        #Robot.population 是类变量，self.population 是对象变量
        Robot.population += 1
    def die(self):
        """我挂了。"""
        print("{} is being destroyed!".format(self.name))
        Robot.population -= 1
        if Robot.population == 0:
            print("{} was the last one.".format(self.name))
        else:
            print("There are still {:d} robots working.".format(
        Robot.population))
    def say_hi(self):
        """来自机器人的诚挚问候
        没问题，你做得到。"""
        print("Greetings, my masters call me {}.".format(self.name))
    #装饰器将方法定义为类方法
    @classmethod
    def how_many(cls):
        """打印出当前的人口数量"""
        print("We have {:d} robots.".format(cls.population))

droid1 = Robot("R2-D2")
droid1.say_hi()
Robot.how_many()
droid2 = Robot("C-3PO")
droid2.say_hi()
Robot.how_many()
print("\nRobots can do some work here.\n")
print("Robots have finished their work. So let's destroy them.")
droid1.die()
droid2.die()
Robot.how_many()
```

* 继承（inheritance） 面向对象编程的一大优点是对代码的重用（Reuse），重用的一种实现方法就是通过继承（Inheritance）机制。继承最好是想象成在类之间实类型与子类型（Type and Subtype）关系的工具.
* SchoolMember 类会被称作基类（Base Class） 或是超类（Superclass）。 Teacher 和 Student 类会被称作派生类（Derived Classes） 或是子类（Subclass）。

* 要想使用继承，在定义类时我们需要在类后面跟一个包含基类名称的元组
* 我们可以通过在方法名前面加上基类名作为前缀，再传入 self 和其余变量，来调用基类的方法

```
class schoolmember:
    def __init__(self,name,age):
        self.name=name
        self.age=age
        print('initial schoolmember:{}'.format(self.name))
    def tell(self):
        print('name:{} age:{}'.format(self.name,self.age),end=' ')
class teacher(schoolmember):
    def __init__(self,name,age,salary):
        schoolmember.__init__(self,name,age)
        self.salary=salary
        print('initial teacher:{}'.format(self.name))
    def tell(self):
        schoolmember.tell(self)
        print('salary:{}'.format(self.salary))
class student(schoolmember):
    def __init__(self,name,age,mark):
        schoolmember.__init__(self,name,age)
        self.mark=mark
        print('initial student:{}'.format(self.name) )
    def tell(self):
        schoolmember.tell(self)
        print('mark:{}'.format(self.mark))

m=teacher('wangzl',20,5000)
n=student('zhouyan',22,100)
print()
member=[m,n]
for i in member:
    i.tell()
```


### 输入与输出

* input实现输入，print实现输出
```
def reverse(a):
    return(a[::-1])
def is_para(a):
    return a.replace(' ','')==reverse(a).replace(' ','')

something=input('please input something:')
if is_para(something):
    print(something,'is para')
else:
    print(something,'is not para')
```

### 文件
* 文件可以操作open('文件名','wbtar'),read,readline,close

```
pemp=''' 江南佳丽地，金陵帝王州。
逶迤带绿水，迢递起朱楼。
飞甍夹驰道，垂杨荫御沟。
凝笳翼高盖，叠鼓送华辀。
献纳云台表，功名良可收。 
'''
f=open('d.txt','a')
f.write(pemp)
f.close()

f=open('d.txt')
while True:
    line=f.readline()
    if len(line)==0:
        break
    print(line)
f.close()
```

### pickle模块
* 将python对象存储到一个文件中，之后取出，这叫持续存储对象
```
import pickle
shoplistdate='shoplist.data'
shoplist=['mango','cara','beef']
f=open(shoplistdate,'wb')
pickle.dump(shoplist,f)
f.close()

del shoplist
f=open(shoplistdate,'rb')
storelist=pickle.load(f)
print(storelist)
```
### unicode
```
import io
f=io.open('abc.txt','wt',encoding="UTF_8")
f.write('Imagine non-English language here')
f.close()

text=io.open('abc.txt',encoding="UTF_8").read()
print(text)
```

### 异常处理
* 我们可以使用try...except 来处理异常，一般俩说我们将通常的语句放在try语句中，将我们错误处理器代码放在except代码块中
```
try:
    text=input('plese input somthine:')
except EOFError:
    print('Why did you do an EOF on me?')
except KeyboardInterrupt:
    print('why did you do an interrupt')
else:
    print('you have input {}'.format(text))
```

* 抛出异常 使用raise语句抛出异常，异常必须是直接或间接从属Exception类的派生类
```
# 定义一个异常
class ShortinputExcepiton(Exception):
    def __init__(self,lenth,aleast):
        Exception.__init__(self)
        self.lenth=lenth
        self.aleast=aleast
try:
    text=input('please input someting:')
    if len(text)<3:
    #抛出异常
        raise ShortinputExcepiton(len(text),3)
except EOFError:
    print('eoferror')
except ShortinputExcepiton as t:
    print('input {0} was {1} le nth,except {2} lenth'.format(text,t.lenth,t.aleast))
else:
    print('input was',text)

```
### try...final


### 传递元组
* 如果需要函数返回两个值，只需要用一个元组就可
```
def get_error_detail():
    return(2,'detail')
a,b=get_error_detail()
print(a,b)

#交换两个值最快的方法是传递元组
a=3
b=4
a,b=b,a
print(a,b)

```
### lambda表达式
* lambda 语句可以创建一个新的函数对象。从本质上说， lambda 需要一个参数，后跟一个表
* 达式作为函数体，这一表达式执行的值将作为这个新函数的返回值。
* key -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，指定可迭代对象中的一个元素来进行排序。
```
points = [{'x': 2, 'y': 3},{'x': 4, 'y': 1}]
points.sort(key=lambda i: i['y'])
print(points)



def takeSecond(elem):
    return elem[1]

# 列表
random = [(2, 2), (3, 4), (4, 1), (1, 3)]

#方法一
random.sort(key=lambda i:i[1])
print(random)

# 方法二 指定第二个元素排序
random.sort(key=takeSecond)
print(random)
```
### 列表推导
* 从一个列表中得到另一个列表
```
list1=[1,2,3,4]
list2=[2*i for i in list1 if i>=3]
print(list2)
```


### 函数中接收元组和字典
### 函数中接收元组和字典
```
def powersum(power,*arg):
    total=0
    for i in arg:
        total+=i**power
    return total

print(powersum(2,3,4))
```
### asert语句
* 断言，如果assert断言失败，则返回AssertionError错误
```
list1=[1]
assert len(list1)==1
assert len(list1)==2
Traceback (most recent call last):
  File "<input>", line 1, in <module>
AssertionError

```
