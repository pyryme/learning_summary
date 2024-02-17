# code文件

> QG寒假学习笔记，这个是老版本的，所以排版有点问题还没有改

- 学会jupyter，用git将GitHub和本地仓库连接，学会markdown语言

- 学会python的基础语法，具体笔记在code文件中

  包括异常处理，封装，继承和复写调用父类成员，多态

- 学习了机器学习的一些部分

- 

#### 异常处理

###### 捕获所有异常

`try:`

​	`可能发生错误的代码`

`except:`
	`如果出现异常执行的代码`



`try:`

`except Exception as e:`



###### 捕获指定异常

`try:`

​	`可能发生错误的代码`

`except ErrorType as e:`

​	`说明异常`

###### 捕获多个异常

`try:`

​	`可能发生错误的代码`

`except (ErrorType1,ErrorType2,...) as e:`

​	`说明异常`



###### else 和 finally语法

`try:`

`except:`

`else:#和try一起执行，为没有异常的`

`finally:#不管是否异常都执行的代码`





#### map,lambda,filter函数语法

###### map

用处：是函数处理同一类型数据参数的简写

代码：

`map(function,[])`



###### lambda

用处：和def同级，定义无名称的函数，只能临时使用一次

代码：

`lambda 参数:函数体（一行代码）`



###### filter

用处：过滤列表里面的值

代码：

`filter(返回值为bool的条件函数或方法, list)`







#### 类

###### 基本代码

理解：类似定义结构体和结构体命名变量

代码：

`class Stu:`

​	`name = Nome`

​	`age = None`

`stu_1 = Stu()`

`stu_1.name = "A"`

`stu_2.age = 18`



###### 成员变量，成员方法

概念：在类里面定义的变量称为成员变量 或 “属性”，在类里面定义的函数称为方法 或 “行为”

代码：

`#定义`

`class Stu:`

`name = None`

​	`def say_hi(self):#不含参数`

​		`print("hi")`

​	`def say_any(self,any):#含参数`

​		`print(f"hi,{any}")`

​	`def say_my(self,any):`

​		`print(f"hi,i am {self.name},{any}")`

`#引用`

`stu_1 = Stu()#用对象实现类`

`stu_1.name = "A"`

`stu_1.say_hi()`

`stu_1.say_any("直接写参数，不用写self，但是定义时一定要在一开始写上self")`

`stu_1.say_my("在类里面引用自己时要用上面的格式")`



###### 私有变量，私有方法

使用目的：为了给类里面的其他公开的变量和方法提供帮助，同时防止使用程序的用户改变和查看不可改变信息

代码：

`#定义`

`class Phone:`

​	`__current_voltage = 1#这个数据在非用户层面更改`

​	`ID = None`

​	`def __keep_single_core(self):`

​		`print("电量不够用单核模式运行")`

​	`def __keep_multi_core(self):`

​		`print("电量充足用多核模式运行")`

​	`def judge_mode(self):`
​		`if self.__current_voltage >= 1:`

​			`self.__keep_multi_core()`

​		`else:`

​			`self.__keep_single_core()`



`#创建对象并引用`

`phone_1 = Phone()`

`phone_1.ID = "111"  			#正确用法`

`phone_1.__current_voltage = 0 #不报错但是无效，不要这么用`

`phone_1.__keep_single_core()  #报错，程序停止，不要这么用`

`phone_1.judge_mode()       #正确用法`





#### 封装

概念：将限制世界事物在类中描述为属性和方法





#### 继承

概念：可以把一个类的非私有成员变量和成员方法复制到另一个类

用处：单继承可以用于多代产品的差异化。多继承可以用类模块化思想把多个功能单独写，最后集成到一个集成体上，

​			如手机的通信，电池，显示等多个功能集成到一个手机类上

代码：

`#单继承`

​	`#定义部分`

`class Phone_1:`

​	`producer = "A"  #制造厂商`

​	`ID = None				#序列号`

​	`def call_by_4g(self):`
​		`print("可以用4g通话")`



`class Phone_2(Phone_1#父类名):`

​	`face_id = True 		#新加上了面部识别`

​	`def call_by_5g(self):`

​		`print("不仅可以4g通话，也可以用5g通话")`



`#多继承`

​	`#定义部分`

`class Phone_1:`

​	`producer = None  #制造厂商`

​	`ID = None				#序列号`

​	`def call_by_g:`
​		`print("可以用4g通话")`



`class NFC:`

​	`NFC_Type = None`



`class RemoteControl:`

​	`def RC(self):`

​		`print("开启远程控制")`



`class Phone_2(Phone_1, NFC, RemoteControl):#把上一代的手机和新开发的功能继承到新一代手机上来`

​	`#对不满意的进行复写`

​	`producer = "B"`

​	`def call_by_g(self):`

​		`print("不仅可以用4g，也可以用5g")`

​	`#定义时调用复写前和复写后的父类变量语法`

​	`def explaination(self):`

​		`print(f"之前的制造商是{Phone_1.producer},{super().producer}")`

​		`print(f"现在的制造商是{self.producer}")`



#### 多态

知识点联系：用到了**继承复写**的语法

概念：父类（抽象类）用来确定有哪些方法行为（抽象方法），子类来根据自身情况定义方法行为的内容

用处：（自己理解）可以用来分类，让人一眼看出这个是哪一个类的，如判断是手机类还是电脑类

代码：

`class AirCondition:`

​	`def cool_wind_technology(self):`

​		`pass`



`class Midea_AC(AirCondition):`

​	`def cool_wind_technology(self):`

​		`print("用的是美的的核心制冷技术")`



`class Gree_AC(AirCondition):`

​	`def cool_wind_technology(self):`

​		`print("用的是格力的核心制冷技术")`
