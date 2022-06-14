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
课程设计：设计一个图书馆里系统。

```python
import sqlite3  # 导入sqlite数据库操作模块
import tkinter  # 导入Tkinter GUI图形界面模块

# 由于是一个基于数据库的管理系统, 因此程序运行就建立数据库连接, 最后还要关闭连接
conn = sqlite3.connect("./books.db")

# 作为简单的演示程序, 我们只创建一个books表, 包含4个字段(列) ID, ISBN, TITLE, AUTHOR
# 数据库里同样的表名只能有一个, 为了防止第二次以后运行出错, 建表SQL语句中 使用了 IF NOT EXISTS 防止出错
sql = '''
CREATE TABLE IF NOT EXISTS books (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    isbn CHAR(36) UNIQUE NOT NULL,
    title TEXT NOT NULL,
    author TEXT
);
'''
conn.execute(sql)
conn.commit()

# 做测试数据 开始>>>>>>>>>>
# 为了方便调试, 如果数据库里没有数据, 我们查询一下books表里是否有数据, (顺带了解一下查询有多少条数据的SQL)
# 如果没有数据,我们添加几条测试数据进去, 仅仅为调试用, 这一段可以注释掉的
sql = '''
    SELECT COUNT(*) FROM books
'''
cur = conn.cursor()
cur.execute(sql)
row = cur.fetchone()  # 取第一条
if row[0] == 0:
    sql = '''
        INSERT INTO  books (isbn, title, author) VALUES (?, ?, ?);
    '''
    cur.execute(sql, ('isbn001', '庆余年', '猫腻'))
    cur.execute(sql, ('isbn002', '赘婿', '愤怒的香蕉'))
    cur.execute(sql, ('ABCD1234', '天龙八部', '金庸'))
    conn.commit()
# 做测试数据 结束<<<<<<<<<<<<<<<<<<<

# 创建主窗口
winMain = tkinter.Tk()
winMain.title('图书管理系统')

# 设置窗口大小:宽x高,注,此处不能为 "*",必须使用 "x" 字母xyz的x
winMain.geometry('800x600')

# 在窗口中添加控件
# 1. 添加一个静态文本控件, 显示"图书一览"这几个字
lbl = tkinter.Label(winMain, text="图书一览")
lbl.place(x=5, y=5) # 让静态文本控件使用tkinter控件几何布局, place是相对于窗口左上角的相对位置指定, 左上角(0,0) 向右向下是+
# tkinter控件的几何布局有下面几个:
# pack()	包装；
# grid()	网格；
# place()	位置；

# 2. 添加一个表格控件, 显示图书数据
#    tkinter没有专门的表格控件，表格是用Treeview实现的, 具体参考Treeview的API文档,
#    只要是GUI编程就没有简单短小的代码, 只能去查阅API, 设置显示参数以及数据, 下面例子的用法供参考

# 这里先定义一个列名称的元组, 用于表格控件的列定义
columns = ("id", "isbn", "title", "author")

# 再定义一个列标题的元组, 用于表格控件列标题的显示
titles = ("ID", "版号", "书名", "作者")

# 开始创建这个表格控件
from tkinter.ttk import Treeview    # Treeview在tkinter.ttk包里, 因此需要这样引用进来
grid = Treeview(winMain, columns=columns, show='headings')

# y=30 的原因是要让出30的位置给上面的静态文本"图书一览" width=790的原因是左右去掉5个边距
grid.place(x=5, y=30, width=790, height=530)

# 循环设置列标题
for i, c in enumerate(columns, 0):
    grid.heading(c, text=titles[i])

# 查询数据并将数据显示到表格中去
# 由于在增,改,删这些操作之后都需要重新查询一下数据并显示,因此将查询并显示这部分代码封装到一个函数中, 调用这个函数即可
# 先定义查询并在表格中显示所有图书函数, 为了更加通用, 因此将书名作为查询条件参数, 参数是空查询全部
def researchBooks(title):
    # 清空表格中以前显示的值
    for row in grid.get_children():
        grid.delete(row)

    # 根据不同情况 拼接带条件或者不带条件的SQL语句
    sql = ''' SELECT id, isbn, title, author FROM books '''
    cur = conn.cursor()

    if title is not None and title != '': # 带条件的SQL语句
        sql += " WHERE title like '%" + title + "%' ORDER BY id"
    else: # 不带条件的
        sql += ' ORDER BY id'

    cur.execute(sql)

    # 将数据库里查询出来的值, 逐条添加到表格控件中显示
    for row in cur:
        grid.insert('', 'end', values=row)


# 调用上面这个查询函数
researchBooks(None)

# 窗口左下角, 添加4个控件, 一个静态文本:"输入书名:", 一个文本框控件让用户可以输入书名, 一个 "查询" 按钮, 一个"清空"按钮
# 添加"输入书名:"静态文本
lblHint = tkinter.Label(winMain, text="输入书名:")
lblHint.place(x=5, y=600-5-30, width=80)

# 添加用户可以输入书名的文本框控件
txtTitle = tkinter.Entry(winMain)
txtTitle.place(x=5+80+5, y=600-5-30, width=120, height=30)

# 添加查询按钮
# 因为查询按钮要绑定查询图书的事件函数, 因此先定义并实现这个查询函数
def onBtnSearchClick():
    title = txtTitle.get()
    # 调用查询函数, 并把查询结果显示到表格里
    researchBooks(title)

# 创建查询按钮并绑定点击事件,然后放置到窗口上
btnSearch = tkinter.Button(winMain, text="查询", command=onBtnSearchClick)
btnSearch.place(x=5+80+5+120+5, y=600-5-30, width=60, height=30)

# 创建清空按钮并绑定点击事件,然后放置到窗口上
# 同样先定义清空按钮的事件
def onBtnClearClick():
    txtTitle.delete(0, tkinter.END)     # 这是清空文本框的方法
    # 重新查询所有的值, 并刷新表格控件
    researchBooks(None)

btnClear = tkinter.Button(winMain, text="清空", command=onBtnClearClick)
btnClear.place(x=5+80+5+120+5+60+5, y=600-5-30, width=60, height=30)

# 窗口右下角添加操作按钮, 从右到左三个按钮: 添加图书, 修改图书, 删除图书
# 添加图书按钮, 也是同样先定义按钮的点击事件
def onBtnAddClick():
    # 当点击添加按钮的时候, 我们先创建一个窗口, 让用户输入图书的信息
    dlg = tkinter.Toplevel(winMain) # 用Toplevel创建一个子窗口, 参数是主窗口
    dlg.geometry('400x145') # 对话框的几何属性, 窗口大小参数的意义和上面主窗口一样
    dlg.title('添加图书') # 设置标题

    # 添加控件
    # 图书id在数据库中是自增长的, 所以不用设置控件
    # isbn 的标签（label）和文本框（Entry）
    lblIsbn = tkinter.Label(dlg, text='ISBN:')
    lblIsbn.place(x=5, y=5, width=80, height=30)
    txtIsbn = tkinter.Entry(dlg)
    txtIsbn.place(x=5+80+5, y=5, width=400-5-80-5-5, height=30)

    # title 的label和Entry
    lblTitle = tkinter.Label(dlg, text='书名:')
    lblTitle.place(x=5, y=40, width=80, height=30)
    txtTitle = tkinter.Entry(dlg)
    txtTitle.place(x=5 + 80 + 5, y=40, width=400 - 5 - 80 - 5 - 5, height=30)

    # author 的label和Entry
    lblAuthor = tkinter.Label(dlg, text='作者:')
    lblAuthor.place(x=5, y=80, width=75, height=30)
    txtAuthor = tkinter.Entry(dlg)
    txtAuthor.place(x=5 + 80 + 5, y=75, width=400 - 5 - 80 - 5 - 5, height=30)

    # 保存按钮, 创建保存按钮之前也要先定义按钮点击的事件函数
    def onBtnSaveClick():
        # 取出画面上用户输入的数据
        isbn = txtIsbn.get()
        title = txtTitle.get()
        author = txtAuthor.get()

        # 这个地方要做几个错误检查,例如isbn的长度, isbn是否重复 等, 为了方便阅读学习代码此处略
        # 错误检查后, 更新到数据库中
        sql = 'INSERT INTO books (isbn, title, author) VALUES (?, ?, ?)'
        cur = conn.cursor()

        # 执行sql的时候, 最好用Try来捕获异常, 如果错误的话给出提示, 为了方便阅读学习代码此处略
        cur.execute(sql, (isbn, title, author))
        conn.commit()

        # 保存结束以后, 调用researchBooks函数, 将主画面表格刷新即可
        researchBooks(None)

        # 关闭新建这个对话框, 整个事件结束
        dlg.destroy()

    # 创建保存按钮并把上面这个保存事件和按钮绑定
    btnSave = tkinter.Button(dlg, text="保存", command=onBtnSaveClick)
    btnSave.place(x=400-5-80, y=110, width=80, height=30)

    # 显示这个对话框
    dlg.mainloop()

# 主窗口上创建并安放添加图书按钮,并绑定点击事件为上面定义的onBtnAddClick事件函数
btnAdd = tkinter.Button(winMain, text="添加图书", command=onBtnAddClick)
btnAdd.place(x=800-5-80, y=600-5-30, width=80, height=30)

# 修改图书按钮, 也是同样先定义按钮的点击事件
def onBtnUpdateClick():
    # 当点击修改图书按钮的时候, 先要取得主窗口上选择的哪一行图书数据
    item = grid.item(grid.selection())  # 表格控件选择的那一行元素
    if item is None:  # 保护一下, 防止没在表格中选择一行图书而出错
        return
    row = item['values']  # 表格中这一行的值(是一个列表: [id, isbn, 书名, 作者])
    id = row[0]     # 取得主键id
    isbn = row[1]   # isbn
    title = row[2]  # 书名
    author = row[3] # 作者

    # 我们创建一个窗口, 把用户选择的图书的信息显示出来,并让用户修改
    dlg = tkinter.Toplevel(winMain)  # 用Toplevel创建一个子窗口, 参数是主窗口
    dlg.geometry('400x145')  # 对话框的几何属性, 窗口大小参数的意义和上面主窗口一样
    dlg.title('修改图书')  # 设置标题

    # 添加控件
    # 图书id是主键, 所以不用设置控件
    # isbn 的label和Entry
    lblIsbn = tkinter.Label(dlg, text='ISBN:')
    lblIsbn.place(x=5, y=5, width=80, height=30)
    txtIsbn = tkinter.Entry(dlg)
    txtIsbn.place(x=5 + 80 + 5, y=5, width=400 - 5 - 80 - 5 - 5, height=30)
    txtIsbn.insert(0, isbn) # 让isbn文本框显示ISBN的值

    # title 的label和Entry
    lblTitle = tkinter.Label(dlg, text='书名:')
    lblTitle.place(x=5, y=40, width=80, height=30)
    txtTitle = tkinter.Entry(dlg)
    txtTitle.place(x=5 + 80 + 5, y=40, width=400 - 5 - 80 - 5 - 5, height=30)
    txtTitle.insert(0, title)  # 让title文本框显示书名的值

    # author 的label和Entry
    lblAuthor = tkinter.Label(dlg, text='作者:')
    lblAuthor.place(x=5, y=80, width=75, height=30)
    txtAuthor = tkinter.Entry(dlg, textvariable=author)
    txtAuthor.place(x=5 + 80 + 5, y=75, width=400 - 5 - 80 - 5 - 5, height=30)
    txtAuthor.insert(0, author)  # 让author文本框显示作者的值

    # 保存按钮, 创建保存按钮之前也要先定义按钮点击的事件函数
    def onBtnSaveClick():
        # 取出画面上用户输入的数据
        isbn = txtIsbn.get()
        title = txtTitle.get()
        author = txtAuthor.get()

        # 这个地方要做几个错误检查,例如isbn的长度, isbn是否重复等, 为了方便阅读学习代码此处略
        # 错误检查后, 更新到数据库中
        sql = 'UPDATE books SET isbn=?, title=?, author=? WHERE id=?'
        cur = conn.cursor()

        # 执行sql的时候, 最好用Try来捕获异常, 如果错误的话给出提示, 为了方便阅读学习代码此处略
        cur.execute(sql, (isbn, title, author, id))
        conn.commit()

        # 保存结束以后, 调用researchBooks函数, 将主画面表格刷新即可
        researchBooks(None)

        # 关闭新建这个对话框, 整个事件结束
        dlg.destroy()

    # 创建保存按钮并把上面这个保存事件和按钮绑定
    btnSave = tkinter.Button(dlg, text="保存", command=onBtnSaveClick)
    btnSave.place(x=400 - 5 - 80, y=110, width=80, height=30)

    # 显示这个对话框
    dlg.mainloop()


# 主窗口上创建并安放修改图书按钮,并绑定点击事件为上面定义的onBtnUpdateClick事件函数
btnUpdate = tkinter.Button(winMain, text="修改图书", command=onBtnUpdateClick)
btnUpdate.place(x=800-5-80-5-80, y=600-5-30, width=80, height=30)

# 删除图书按钮, 同样, 先定义按钮的点击事件
def onBtnDeleteClick():
    # 取得主窗口表格上选择的哪一行图书
    item = grid.item(grid.selection())  # 表格控件选择的那一行元素
    if item is None: # 保护一下, 防止没在表格中选择一行图书而出错
        return
    row = item['values']    # 表格中这一行的值(是一个列表: [id, isbn, 书名, 作者])
    id = row[0]     # 取得主键id
    title = row[2]  # 书名

    import tkinter.messagebox
    result = tkinter.messagebox.askokcancel(title='删除确认', message='确定删除' + title + '吗?')
    if not result:  # 选择的不是确定按钮, 意味着取消, 这时候就返回即可
        return

    # 上面如果选择的不是确定按钮, 就return了, 所以下面这部分就开始删除
    sql = '''
    DELETE FROM books WHERE id = ?
    '''
    cur = conn.cursor()
    cur.execute(sql, (id, ))
    conn.commit()

    # 删除完了以后, 调用查询函数, 查询所有图书, 并刷新表格
    researchBooks(None)

# 创建并安放删除图书按钮
btnDelete = tkinter.Button(winMain, text="删除图书", command=onBtnDeleteClick)
btnDelete.place(x=800-5-80-5-80-5-80, y=600-5-30, width=80, height=30)

# 开始GUI窗口的消息循环, 等待用户输入
winMain.mainloop()

conn.close()
```