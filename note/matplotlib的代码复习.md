```python
# matplotlib的代码复习
#1. 导入包
from matplotlib import pyplot as plt

#2.中文语言设置 这两行代码查看电脑系统中已经有的文字，我找了个'Microsoft JhengHei'微软正黑，
# import matplotlib as mpl
# mpl.font_manager.FontManager().ttflist
#这一行是进行语言设置，这样的话整个文档都能显示这个中文字体了 
plt.rcParams['font.sans-serif'] = ['Microsoft JhengHei']

#3.
#----------折线图
x_1=[]
x_2=[]
y_1=[]
y_2=[]

	#一个语句确定一条折线，要多少条就写多少个对应语句。
	#这里可以设置图例，要配合后面的添加语句
    #同时这里也可以自定义图形风格，线条颜色 风格 粗细 透明度
plt.plot(x,y_1,label="A人") 
plt.plot(x,y_2,color='',linestyle='',linewidth=2 ,alpha=0.1 ,label="B人")
	#设置坐标轴显示的列表，调整疏密程度，y轴同理
plt.xticks(x) #方1
_xtick_lables = [i/2 for i in range(4,49)]#方2,调整步长，
plt.xticks(_xtick_lables[::3])
_x = list(x_1)+list(x_2)#方3 用非数字列表 并且进行合并坐标轴数据，则要进行数据的对齐，同时可以旋转
_xticks_labels = ["10点{}分".format(i) for i in x_1 ]
_xticks_labels += ["11点{}分".format(i-60) for i in x_2]
plt.xticks(_x,_xtick_labels,rotation=90)
_xticks_labels = ["10点{}分".format(i) for i in x if x<60]#4 条件
plt.xticks(x[::5],_x_ticks[::5],rotation=90)

	#添加描述信息
plt.xlable("时间")
plt.ylable("温度 单位℃")
plt.title("早上这个时间段每分钟的温度变化情况")
#----------散点图
#把上面的plt.plot() 改为 plt.scatter()即可
#----------条形图
x_1=[非数字列表]
y_1=[]
plt.bar(range(len(a)),b)#输入数字列表
plt.xticks(range(len(a)),a)#将对应关系转回来
#旋转，调整稀疏程度
plt.barh(range(len(a)),b,height=0.3)
plt.yticks(range(len(a)),a)
#----------饼图
fig, axe = plt.subplots(figsize = (8,5))
lables_1 = ['A','B','C','D']
lables_2 = ['S1','S2','S3','S4']
values_1 = [111,222,333,444]
values_2 = [123,2,3,4]

explode_1 = [0,0,0.1,0.2]#显示饼状图的突出程度
explode_2 = [0,0,0,0]

axe.pie(values_1, radius=1.5, wedgeprops=dict(width=0.5),autopct='%.2f%%',
       pctdistance=0.8,labels=lables_1,labeldistance=1.05,explode=explode_1)
axe.pie(values_2, radius=1, wedgeprops=dict(width=0.5),autopct='%.2f%%',
       pctdistance=0.8,labels=lables_2,labeldistance=0.3,explode=explode_2)
#填入value值 这个是用来计算占比的series（即字典对列表），radius表示饼状图的半径，wedgeprops=dict(width=0.5)表示饼状图的宽度，autopct='%.2f%%'表示计算结果显示到小数点后两位，pctdistance=0.8表示计算的百分比结果离中心的距离，labels=lables_1 表示标签是什么， labeldistance=1.05表示标签离中心的距离，explode=explode_1表示突出程度 要求也是一个列表 所以前面先写了。






#
#4.添加图例，可以不用写loc，系统默认显示在右上角
plt.legend(loc="upper left")

#5.辅助的网格
plt.grid(alpha=0.1)

#6.设置图片大小,清晰度
plt.figure(figsize=(20,8),dip=80)


#7.保存图片
plt.savefig("./tupian.png")
#8.展示图形
plt.show()
```

