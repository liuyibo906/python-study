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




























