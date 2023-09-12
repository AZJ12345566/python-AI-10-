# python-AI-10-
python+AI笔记(10)
# 一阶-五章-函数返回值之None类型
def say_hi():
    print("你好呀")

result=say_hi()
print(f"{result}")
print(f"type(result)")

def check_age(age):
    if age>18:
        return "SUCCESS"
    else:
        return None
result=check_age(16)
if not result:
    #进入if表示result是None值，也就是False
    print("未成年，请勿入内")

#None也可以声明无内容的变量
name=None

# 一阶-五章-函数的说明文档
def add(x,y):
#先打三个引号，然后一回车，电脑会自动将说明文档弹出来
    result=x+y
    print(f"2数相加的结果为:{result}")
    return result
#在pycharm中用鼠标对函数进行悬停，可以查看当前函数的说明文档

# 一阶-五章-函数的嵌套调用
def func_b():
    print("2")
def func_a():
    print("1")
    func_b()
    print("3")
#调用函数
func_a()  #输出1，2，3

# 一阶-五章-变量在函数中的作用域
def test_a():
    num=100
    print(num)
test_a()
print(num)  #程序会报错，num是局部变量，局部变量出了函数体，就无法使用了

#全局变量，指的是在函数体内、外都能生效的变量
num=200
def test_b():
    print(f"test_a:{num}")
print(num)

#在函数内去修改全局变量
#在函数内修改的全局变量的值只在函数内部有效，在函数外仍然使用最初变量初始化的值

#global关键字，在函数内声明的变量为全局变量
num=200
def test_b():
    global num
    num=500
print(num)  #输出值为500

# 一阶-五章- 函数综合案例

#定义全局变量money,name
money=5000000
name=None
#要求客户输入姓名
name=input("请输入您的姓名:")
#定义查询函数
def query(show_header):
    if show_header:
        print("-------------查询余额---------------")
    print(f"{name},您好，您的余额剩余:{money}元")
#定义存款函数
def saving(num):
    global money
    money+=num
    print("-------------存款-------------------")
    print(f"{name},您好，您存款{num}元成功。")

#调用query函数查询余额
query(False)

#定义取款函数
def get_money(num):
    global noney
    money-=num
    print("-------------取款-------------------")
    print(f"{name},您好，您取款{num}元成功。")

#定义主菜单函数
def main():
    print("---------------主菜单----------------")
    print(f"{name}您好·，欢迎来到银行，请选择操作:")
    print("查询余额\t[输入1]")
    print("存款\t\t[输入2]")
    print("取款\t\t[输入3]")
    print("退出\t\t[输入4]")
    return input("请输入您的选择:")
#设置无限循环，确保循环不退出
while True:
    keyboard_input=main()
    if keyboard_input=="1":
        query(True)
        continue  #通过continue继续下一次循环，一进来就是主菜单
    elif keyboard_input=="2"
        num==input("您想要存都少钱？请输入:")
        saving(num)
        continue
    elif keyboard_input=="3":
        num=int(input("请输入你要取多少钱？请输入:"))
        get_money(num)
        continue
    else:
        print("程序已退出")
        break
