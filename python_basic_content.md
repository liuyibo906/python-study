#格式化字符串
age=20                                          
name='liuyb'                                       
print('{} is {} years old'.format(name,age))       
print('{0:.6f}'.format(1.0/3)) #小数点后保留6为小数
#转义字符
print('this is the first line.\nthis is the second line.') 
#原始字符串用r或R
print(r'this's a new message')
#如果一个字符串很长，可以使用\来换行
s='this is a very \
long story'