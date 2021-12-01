# chanchankim005.github.io
pyautogui自动化控制鼠标和键盘操作

PyAutoGUI是一个纯Python的GUI自动化工具，其目的是可以用程序自动控制鼠标和键盘操作，多平台支持（Windows，OS X，Linux）。

安装

pip3 install pyautogui

pyautogui鼠标操作样例

import pyautogui

# 获取当前屏幕分辨率
screenWidth, screenHeight = pyautogui.size()

# 获取当前鼠标位置
currentMouseX, currentMouseY = pyautogui.position()

# 2秒钟鼠标移动坐标为100,100位置  绝对移动
#pyautogui.moveTo(100, 100,2)
pyautogui.moveTo(x=100, y=100,duration=2, tween=pyautogui.linear)

#鼠标移到屏幕中央。
pyautogui.moveTo(screenWidth / 2, screenHeight / 2)

# 鼠标左击一次
#pyautogui.click()
# x 
# y 
# clicks 点击次数
# interval点击之间的间隔
# button 'left', 'middle', 'right' 对应鼠标 左 中 右或者取值(1, 2, or 3)
# tween 渐变函数
#
pyautogui.click(x=None, y=None, clicks=1, interval=0.0, button='left', duration=0.0, tween=pyautogui.linear)

# 鼠标相对移动 ,向下移动
#pyautogui.moveRel(None, 10)
pyautogui.moveRel(xOffset=None, yOffset=10,duration=0.0, tween=pyautogui.linear)


# 鼠标当前位置0间隔双击
#pyautogui.doubleClick()
pyautogui.doubleClick(x=None, y=None, interval=0.0, button='left', duration=0.0, tween=pyautogui.linear)

# 鼠标当前位置3击
#pyautogui.tripleClick()
pyautogui.tripleClick(x=None, y=None, interval=0.0, button='left', duration=0.0, tween=pyautogui.linear)

#右击
pyautogui.rightClick()

#中击
pyautogui.middleClick()

#  用缓动/渐变函数让鼠标2秒后移动到(500,500)位置
#  use tweening/easing function to move mouse over 2 seconds.
pyautogui.moveTo(x=500, y=500, duration=2, tween=pyautogui.easeInOutQuad)

#鼠标拖拽
pyautogui.dragTo(x=427, y=535, duration=3,button='left')

#鼠标相对拖拽
pyautogui.dragRel(xOffset=100,yOffset=100,duration=,button='left',mouseDownUp=False)

#鼠标移动到x=1796, y=778位置按下
pyautogui.mouseDown(x=1796, y=778, button='left')

#鼠标移动到x=2745, y=778位置松开（与mouseDown组合使用选中）
pyautogui.mouseUp(x=2745, y=778, button='left',duration=5)

#鼠标当前位置滚轮滚动
pyautogui.scroll()
#鼠标水平滚动（Linux）
pyautogui.hscroll()
#鼠标左右滚动（Linux）
pyautogui.vscroll()
1

pyautogui键盘操作样例
#模拟输入信息
pyautogui.typewrite(message='Hello world!',interval=0.5)
#点击ESC
pyautogui.press('esc')
# 按住shift键
pyautogui.keyDown('shift')
# 放开shift键
pyautogui.keyUp('shift')
# 模拟组合热键
pyautogui.hotkey('ctrl', 'c')

按键支持
按键	说明
enter(或return 或 \n)	回车
esc	ESC键
shiftleft, shiftright	左右SHIFT键
altleft, altright	左右ALT键
ctrlleft, ctrlright	左右CTRL键
tab (\t)	TAB键
backspace, delete	BACKSPACE 、DELETE键
pageup, pagedown	PAGE UP 和 PAGE DOWN键
home, end	HOME 和 END键
up, down, left,right	箭头键
f1, f2, f3….	F1…….F12键
volumemute, volumedown,volumeup	有些键盘没有
pause	PAUSE键
capslock, numlock,scrolllock	CAPS LOCK, NUM LOCK, 和 SCROLLLOCK 键
insert	INS或INSERT键
printscreen	PRTSC 或 PRINT SCREEN键
winleft, winright	Win键
command	Mac OS X command键
提示信息
alert
#pyautogui.alert('This is an alert box.','Test')
pyautogui.alert(text='This is an alert box.', title='Test')
1
2


option
#pyautogui.confirm('Shall I proceed?')
pyautogui.confirm('Enter option.', buttons=['A', 'B', 'C'])
1
2


password
a = pyautogui.password('Enter password (text will be hidden)')
print(a)
1
2


prompt
a = pyautogui.prompt('input  message')
print(a)
1
2


截屏
整个屏幕截图并保存
im1 = pyautogui.screenshot()
im1.save('my_screenshot.png')

im2 = pyautogui.screenshot('my_screenshot2.png')
1
2
3
4
屏幕查找图片位置并获取中间点
#在当前屏幕中查找指定图片(图片需要由系统截图功能截取的图)
coords = pyautogui.locateOnScreen('folder.png')
#获取定位到的图中间点坐标
x,y=pyautogui.center(coords)
#右击该坐标点
pyautogui.rightClick(x,y)

安全设置
import pyautogui

#保护措施，避免失控
pyautogui.FAILSAFE = True
#为所有的PyAutoGUI函数增加延迟。默认延迟时间是0.1秒。
pyautogui.PAUSE = 0.5

#第二部分

获取鼠标位置
所以我们的第一条命令就是获取鼠标当前的位置。
x,y = pyautogui.position()

我们来打印下当前的位置

print ("当前鼠标的X轴的位置为：{}，Y轴的位置为：{}".format(x,y))

输出结果如下：

当前鼠标的X轴的位置为：333，Y轴的位置为：327

获取屏幕分辨率
如何获取屏幕的分辨率呢？也就是最大的X和Y的值
x,y = pyautogui.size()

打印屏幕的分辨率

print ("当前屏幕的分辨率是{}*{}".format(x,y))

输出结果：

当前屏幕的分辨率是1536*864

移动鼠标
比如说，电脑桌面上的火狐浏览器的位置是（100，100）.我如何将鼠标移动到这个位置呢？
pyautogui.moveTo(x=300,y=300,duration=0.25)

duration类似于移动时间或移动速度，省略后则是瞬间移动到指定的位置

单击鼠标
如何让鼠标左键点击屏幕中(100,100)的位置呢？
pyautogui.click(x=100,y=150,button='left')

当button=‘left’相当于鼠标左键，button=‘right’相当于鼠标右键。当不带button参数时，默认为左键。

双击鼠标
如何双击鼠标呢？
pyautogui.doubleClick(x=100,y=150,button="left")

当button=‘left’相当于鼠标左键，button=‘right’相当于鼠标右键。当不带button参数时，默认为左键。

拖拽鼠标
如何实现拖拽鼠标？
pyautogui.dragTo(x,y,duration=0.25)

duration类似于移动时间或移动速度，省略后则是瞬间移动到指定的位置

键盘操作
在讲键盘操作之间，先展示一张从脚本之家盗来的按键映射表


发送组合键
pyautogui.hotkey('win', 'r')

发送的按键之间使用【，】逗号隔开。

输入内容
pyautogui.typewrite(message="hello world",interval=0.25)

message后面跟要输入的内容,interval用于设置输入的速度

高级操作
pyautogui有内置的截图功能，可以使用screenshot方法进行截图，然后可以操作截图，进行确认图片位置或者指定坐标的颜色等。

获取坐标点的像素
img = pyautogui.screenshot()
color = img.getpixel((100,100))


执行结果：

该坐标的像素点的颜色是：(255, 255, 255)

返回的是三原色值。

获取图片的位置
x,y,width,height =  pyautogui.locateOnScreen('a.png')

括号中传递的是图标文件的路径
执行：

print ("该图标在屏幕中的位置是：X={},Y={}，宽{}像素,高{}像素".format(x,y,width,height))

结果：

该图标在屏幕中的位置是：X=9,Y=741，宽81像素,高95像素

获取图标的中心点
x, y = pyautogui.center((9,741,81,95))

括号中分别传递，图片的X轴，Y轴，宽，长
执行命令：

x,y = pyautogui.center((9,741,81,95))

执行结果：

该图标的中心点是:X=49,Y=788


import pyautogui


"""获取鼠标当前的坐标位置"""
'''
x,y = pyautogui.position()

print ("当前鼠标的X轴的位置为：{}，Y轴的位置为：{}".format(x,y))
'''


"""获取屏幕分辨率"""
'''
x,y = pyautogui.size()
print ("当前屏幕的分辨率是{}*{}".format(x,y))
'''



"""移动鼠标到指定位置"""
'''
pyautogui.moveTo(x=300,y=300,duration=0.25)
'''


"""点击鼠标"""
'''
pyautogui.click(x=100,y=150,button='right')
'''


"""双击鼠标"""
'''
pyautogui.doubleClick(x=100,y=150,button="left")

'''

"""发送组合键"""
'''
pyautogui.hotkey('win', 'r')
'''

"""输入内容"""
'''
pyautogui.typewrite(message="hello world",interval=0.25)
'''

"""获取指定坐标的颜色"""
'''
img = pyautogui.screenshot()
color = img.getpixel((100,100))
print ("该坐标的像素点的颜色是：{}".format(color))
'''


"""获取图标的位置"""
'''
x,y,width,height =  pyautogui.locateOnScreen('a.png')
print ("该图标在屏幕中的位置是：X={},Y={}，宽{}像素,高{}像素".format(x,y,width,height))
'''

"""获取中心点"""
'''
x,y = pyautogui.center((9,741,81,95))
print ("该图标的中心点是:X={},Y={}".format(x,y))
'''
————————————————
