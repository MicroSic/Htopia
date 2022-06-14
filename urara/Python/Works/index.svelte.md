---
title: 'Python Works'
date: 2022-03-14
lastmod: 2022-03-14
tags:
  - 'Hello World'
  - 'Python'
cover: '/Python/Works/cover.webp'
---
## 数据类型

作业1：从键盘输入一个字符串，统计大写字母、小写字母、数字字符和其他字符的个数 。
请完成三种以上不同形式的输出。


```python
s = input('请输入字符串s:' )
u,l,d,e=0,0,0,0
for i in s:
    if i.isupper():
        u += 1
    elif i.islower():
        l += 1
    elif i.isdigit():
        d += 1
    else:
        e += 1

print(str.format('字符串s中大写字母{}个，小写字母{}个，数字字符{}个，其他字符{}个',u,l,d,e))
print('字符串s中大写字母{}个，小写字母{}个，数字字符{}个，其他字符{}个'.format(u,l,d,e))
print(f'字符串s中大写字母{u}个，小写字母{l}个，数字字符{d}个，其他字符{e}个')
```


作业2：尝试独立编写，从键盘输入最近几天的温度，用逗号分隔，求最高温度和最低温度，保留2位小数。 

```python
tem = input("请输入最近几天的温度，用半角逗号分隔：")
list = tem.split(",")   #分隔符为半角逗号
max = float(max(list))  #求列表list中元素的最大值
min = float(min(list))
print(str.format("最高温度是{:.2f}度，最低温度是{:.2f}度",max,min))
```


作业3：尝试完成登录小程序，要求随机产生4位验证码，验证码可以包括大小写字母和数字字符。

```python
import random
s = "FpV74ctsYQqIW9JMhPRcs1UfRxm9XY6ZAnBD9zFqeshgi1FLglIZI63nQRGkTS27jTlJrbSpPD2"   #随机长字符串
input_str = ""
for i in range(4):
    ran = random.randint(0,len(s)-1)  
    input_str = input_str + s[ran]   #ran是长字符串中任意一个字符的索引

print(str.format("随机验证码是：{}",input_str))
login_name = input("请输入用户名：")
login_pass = input("请输入登录密码：")
login_str = input("请输入随机验证码：")
if login_name == "test" and login_pass == "passw0rd" and login_str == input_str:
    print(str.format("用户{}已成功登录！",login_name))
elif login_str != login_str:
    print("验证码错误")
else:
    print("用户名与密码不匹配")
```


作业4：输入一个月份数字，返回对应月份名称缩写。

```python
months = "JanFebMarAprMayJunJulAugSepOctNovDec"
m = input("请输入月份数，要求在1-12之间：")
indices = (int(m)-1)*3  #月份简写的切片首字母索引和月份数的关系
output = months[indices:indices+3]   #包左不包右
print(str.format("月份简写是{}",output))
```

## 控制结构

作业1：分段函数—各种数学函数的练习。

```python
from math import *
x = eval(input("请输入x的值："))
if (x <=0 ):
    y = sin(x)+e
else:
    y = log(x)

print(f"y的值是{y:.2f}")
```

作业2：闰年的判断。

闰年是能被4整除，但不能被100整除的年份(例如2008是闰年，1900不是闰年) ，能被400整除的年份(例如2000年)也是闰年。

```python
year = eval(input("请输入年份："))
if year % 400 == 0 or (year % 4 == 0 and year % 100 != 0):
    print(str.format("{}年是闰年",year))
else:
    print(str.format("{}年不是闰年",year))
```

作业3：百分制转换为五级制。

```python
point = eval(input("请输入分数，0-100之间："))
grade = ""
if point >= 90:
    grade = "优秀"
elif point >= 80:
    grade = "良好"
elif point >= 70:
    grade = "一般"
elif point >= 60:
    grade = "及格"
else:
    grade = "不及格"

print(str.format("此分数{}",grade))
```

作业4：打印九九乘法表。

```python
for i in range(1,10):    #乘数i的取值区间为[1,9]
    for j in range (1,i+1):   #乘数j的取值区间为[1，i]
        s = i*j
        print(str.format("{}*{}={}",i,j,s,),end=" ")   #当乘数i相同时以空格为结束符将打印结果分隔开
    print()   #回车
```

作业5：打印斐波那契数列。

```python
a, b = 0, 1
while b < 1000:
    print(b,end = " ")  #规定以空格为结束符
    a, b = b, a + b
```

作业6：打印100-200之间的素数。

```python
nums = []   #生成一个空列表nums
for num in range(100,201):
    for i in range(2,num):   #被除数i的取值区间为[2,num-1]
        if num % i == 0:
            break
    if num == i+1:   #当i取到最大值num-1依旧不满足num % i == 0，判断num是素数
        nums.append(num)  #将对象num加入列表nums的末端
print("100-200之间的素数有：",nums)
```
拓展：输入一个正整数，判断是否为素数。

```python
x = input("请输入一个正整数，按q退出：")
if x.upper() == "Q":  #若将字符串全部大写后等于Q，退出程序
    exit
else:
    x = eval(x)  #将字符串转换为数值型
    for i in range(2,x):
        if x % i == 0:
            print(f"{x}不是素数")
            break
        if x == i + 1:
            print(f"{x}是素数")
```

作业7：完善四组运算小程序。

```python
a = eval(input("请输入数字a："))
op = input("请输入四则运算符（+-*/）:")
b = eval(input("请输入数字b："))
if op != "+" or "-" or "*" or "/":
    print("请输入正确的四则运算符！")
else:
    if op == "+":
        s = a + b
    elif op == "-":
        s = a - b
    elif op == "*":
        s = a * b
    elif op == "/":
        s = a / b
    print(str.format("计算结果为{}{}{}={}",a,op,b,s))
```

作业8：完善登录小程序。
```python
import random
str1 = ""
for i in range(6):
    ran = random.randint(1,9)
    str1 = str1 + str(ran)
#生成六位数字验证码，登录
print(str.format("验证码是{}",str1))
login_name = input("请输入用户名：")
login_pass = input("请输入登录密码：")
login_str = input("请输入随机验证码：")
if login_name == "test" and login_pass == "passw0rd" and login_str == str1:
    print(str.format("用户{}已成功登录！",login_name))
elif login_str != str1:
    print("验证码错误")
else:
    print("用户名与密码不匹配")
```

作业9：完善猜数字小游戏。

```python
import random
print("=" * 30)
print("欢迎来到猜数字小游戏！")
print("=" * 30)
ran = random.randint(0, 10)
num = eval(input("请输入数字（0-9）："))
i = 1
while i <= 3:   #尝试少于三次
    if num > ran :
        print("大了！")
    elif num < ran:
        print("小了！")
    else:
        print("恭喜你，猜中了！")
        break
    num = eval(input("请输入数字（0-9）："))
    i += 1
else:   #第四次
    if num != ran:
        print("已经尝试四次失败了，请再试一次吧！")
    if num == ran:
        print("恭喜你，猜中了！")
```

## 函数与模块

作业1：定义计算并返回第n阶调和数（1 + 1/2 + 1/3 + … + 1/n）的函数，并调用该函数。

```python
def harmonic(n):  #计算n阶调和数(1+1/2+1/3+...+1/n)
    total=0.0
    for i in range(1,n+1):
        total+=1.0/i
    return total

n=eval(input("请输入正整数n："))
print(harmonic(n))
```
作业2：定义一个函数，其功能是求正整数的阶乘，并利用该函数求解6！、16！和26！的结果。 

```python
def func(n):
    s =1
    if n == 0:
      return 1
    elif n >= 1:
        for i in range(1, n + 1) :
            s *= i
        return s
    else:
        print('出错')

print(func(6))

print(func(16))

print(func(26))
```

作业3：定义一个登录函数，定义一个获取验证码的函数，允许用户登录3次。

```python
import random
def code(n) :
    str1 = ""
    for i in range(n):
        ran = random.randint(1,9)
        str1 += str(ran)
    return str1
#生成n位数字验证码，登录
code1 = code(4)
print(str.format("验证码是{}",code1))
login_name = input("请输入用户名：")
login_pass = input("请输入登录密码：")
login_str = input("请输入随机验证码：")
def login(login_name,login_pass,login_str):
    name = "test"
    pwd = "passw0rd"
    for i in range(3) :
        if login_name == name and login_pass == pwd and login_str == code1 :
            print(str.format("用户{}已成功登录！", login_name))
            break
        else :
            print("请重试")
            login_name = input("请输入用户名：")
            login_pass = input("请输入登录密码：")
            login_str = input("请输入随机验证码：")
    else :
        print("用户被锁定")
#登录函数
login(login_name,login_pass,login_str)
```
## 文件操作和异常

作业1：设计一个图书管理小程序。

```python
import json
import os
filename = 'family.json'
# 判断文件是不是存在
json_file = os.path.exists(filename)
books =[]
#增加图书
def add_books():
    global books
    # 文件存在
    if json_file:
        with open(filename)as f:
            books = json.load(f)
    while True:
        name = input('请输入要添加的图书：')
        isExist = False
        for book in books:
            if book['name']==name:
                print('该书已存在')
                isExist = True
                break
        # 用户输入的图书不在books中
        if not isExist:
            price = input('请输入价格：')
            book = {}
            book['name'] = name
            book['price'] = price
            books.append(book)
            print('图书添加成功！')

        answer = input('继续增加吗？（y/n）')
        if answer.upper() == 'Y':
            continue
        else:
            break
    with open(filename,'w')as f:
        json.dump(books,f)
    return
#浏览图书
def show_books():
    if json_file:#文件存在
        with open(filename)as f:
            books = json.load(f)
        for book in books:
            print(book['name'],'价格是',book['price'])
    return
#删除图书
def del_books():
    if json_file:
        with open(filename)as f:
            books = json.load(f)
    while True:
        name = input('请输入要删除的图书：')
        isDel = False
        for index, book in enumerate(books):
            if book['name'] == name:
                isDel = True
                books.pop(index)

        if isDel:
            print('图书删除成功！')
        else:
            print('不存在图书{}！'.format(name))

        answer = input('继续删除吗？（y/n）')
        if answer.upper() == 'Y':
            continue
        else:
            break
    with open(filename,'w')as f:
        json.dump(books,f)
    return
#查询图书
def search_books():
    if json_file:
        with open(filename)as f:
            books = json.load(f)

    name= input('请输入要查询的图书：')
    for book in books:
        if book['name'] == name:
            print(book['name'], book['price'])
            return

    print("不存在名字是{}的图书".format(name))


def main():
    while True:
        print('欢迎使用图书小程序！')
        print('|-------1.图书增加--------｜')
        print('|-------2.图书浏览--------｜')
        print('|-------3.图书查询--------｜')
        print('|-------4.图书删除--------｜')
        print('|-------5.退出------------｜')
        n = input('请选择要进行的操作：')
        if n=='1':
            add_books()
            input('按回车键继续...')
        elif n=='2':
            show_books()
            input('按回车键继续...')
        elif n=='3':
            search_books()
        elif n == '4':
            del_books()
        elif n == '5':
            break
        else:
            print('请输入1-5之间的数！')
            break

if __name__=='__main__':
    main()
```
## 类与对象

作业1：建立银行卡类

属性：账户名、余额

方法：
   0. 通过init实现属性初始化

   1. 存款（金额）

   2. 取款（金额）

   3. 转账（card）给card转*\钱，对应的余额属性要减少

   4. 打印对象要显示的所有属性信息

```python
class Card:
    def __init__(self, number, name, blance):
        self.number=number
        self.name=name
        self.blance=blance

    def save_money(self, blance):
        self.blance+=blance

    def get_money(self, blance):
        if blance>self.blance:
            print("余额不足")
            return False
        else:
            self.blance -=blance
            return True

    def search_blance(self):
        print("卡号{},姓名{} 的余额是{}".format(self.number, self.name, self.blance))

    def give_money(self, card, blance):
        if blance>self.blance:
            print("余额不足")
        else:
            card.blance += blance
            self.blance -= blance

        flag = self.get_money(blance)
        if flag:
            card.save_money(blance)


class ATM:
    def __init__(self, name=None, size=None, card=None):
        self.name = name
        self.size = size
        self.card = card

    def insert_card(self, card):
        self.card = card

    def save_money(self, blance):
        self.card.save_money(blance)

    def get_money(self, blance):
        self.card.get_money(blance)

    def search_blance(self):
        self.card.search_blance()

    def give_money(self, card, blance):
        self.card.give_money(card, blance)


card1 = Card('00123', '小明', 10000)
card1.search_blance()
card1.save_money(8000)
card1.search_blance()
card1.get_money(2000)
card1.search_blance()

card2 = Card('00112', '小华', 0)
card1.give_money(card2, 20000)
card2.search_blance()


atm = ATM()
atm.insert_card(card1)
atm.search_blance()

atm.save_money(8000)
atm.search_blance()
```

作业2：编写简单的工资管理程序，系统可以管理以下四类人：工人（worker）、销售员（salesman）、经理（manager）、销售经理（salesmanager）。所有的员工都有员工号，姓名，工资等属性，有设置姓名，获取姓名，获取员工号，计算工资等方法。
1）工人，工人具有工作小时数和时薪的属性，工资计算法为基本工资+工作小时数*时薪
2）销售员：具有销售额和提成比例的属性，工资计算方法为基本工资+销售额*提成比例
3）经理：具有固定月薪的属性，工资计算方法为固定月薪
4）销售经理：工资计算方法为销售额*提成比例+固定月薪
请根据以上要求设计合理的类，完成以下功能：
1）创建的不同类型的员工
2）计算月薪
3）显示所有人的工资情况

```python
class Person:
    def __init__(self,no,name,salary):
        self.no = no
        self.name = name
        self.salary = salary

    def __str__(self):
        msg = '工号：{},姓名：{},本月工资：{}'.format(self.no,self.name,self.salary)
        return msg

    #def getSalary(self):
        #return self.salary

class Worker(Person):
    def __init__(self,no,name,salary,hours,per_hour):
        super().__init__(no,name,salary)
        self.hours = hour
        self.per_hour = per_hour

    def getSalary(self):
        money = self.hours * self.per_hour
        self.salary += money
        return self.salary

class Salesman(Person):
    def __init__(self,no,name,salary,salemoney,percent):
        super().__init__(no,name,salary)
        self.salemoney = salemoney
        self.percent = percent

    def getSalary(self):
        money = self.salemoney * self.percent
        self.salary += money
        return self.salary
```
