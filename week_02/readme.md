# 一、本周学了什么？:stuck_out_tongue_winking_eye:
## 1. pandas能处理什么样的数据？:dizzy:
### 框框框
* 使用pd.dataframe将数据变成表格结构
* 对数据科学家来说，column（竖着的）放变数（变量），row（横着的）放观察   
* .loc[] 取观察，读取某行的数据  
* [""] 取变数，读取某列的数据
* 有点像字典的取值，与字典非常相似   
* dataframe是二维的表格型数据结构，series是一维数组
## 2. 如何读写数据？:wave:
### 读读读   
:information_desk_person: [小抄](https://www.cnblogs.com/hotsnow/p/9480849.html)   
* 将数据读进来or输出去
* 尽量用tsv表格
* 相关语法： :hatching_chick:   
   1. df.head(n) 当没有参数时，默认输出前5个   
   2. 读写到csv = pd.read_csv("路径文档名",encoding="utf8")   
      读写到tsv = pd.read_tsv("路径文档名",encoding="utf8")   
      读写到excel = pd.read_excel("路径文档名"，encoding="utf8")   
   3. df.to_html 写入到html文件   
      df.to_markdown 转换为markdown格式   
      df.to_json 写入到json文件
      df.to_dict 转换为字典格式   
      df.to_sql  写入sql表   
   4. df.info()  索引，说明数据表里的数据类型和内存信息   
      df.shape() 输出数据表的行数和列数   
      df.describe()  输出数值列的汇总统计信息，一次性输出多个描述性统计指标.当参数是include = "all" 时，是对所有属性的描述，当参数是 include= "O" 时，则是描述object类型的属性
* read_tsv就是个摆设，根本无法运行，也无法导入，tsv文件还是得用read_csv方法读取
## 3. 如何选择列表的子集？:mushroom:
### 切切切  列表切片    
* 相关语法 :volcano:   
   1. 列子集   
      1. df.loc[]  例如 df.loc[2],df.loc[:8],df.loc[[0,2]](显示第一行和第三行)
      2. df.iloc[]  例如 df.iloc[2],df.iloc[:2]
      3. df.set_index()  将dataframe中的列转化为索引行.例如 df.set_index(["企业名称"])，那么“企业名称”就变成了索引行
      4. df.head(n)
      5. df.tail(n)  与df.head(n)用法相同
      6. df.nlargest(n,'变量')  nlargest()的优点就是能一次看到最大的几行，而且不需要排序
      7. df.nsmallest(n,'变量')
      8. df[df["变量"]>n]   例如： df[df["估值（亿人民币)"]>3000]
   2. 行子集   
      1. df['变量A']  类似文字输出方式，不太美观   
      2. df[['变量A']]   
      3. df[['变量A','变量B','变量C']]   
   3. 列+行子集    
      1. df.loc[:,'变量A'：'变量C']  例如 df.loc[:8,:]或df.loc[[0,2],["排名","企业名称"]]或df.loc[1:5,"企业名称":"国家"] 
      2. df.iloc[:,[1,2,5]]   例如 df.iloc[0:7,[1,5]]或df.iloc[1:4,2:5]
      3. df.loc[df['变量A']>10,['变量A','变量B']] 例如 df.loc[df['估值（亿人民币）']>3000,['企业名称','国家']]
## 4. 如何在pandas绘图？:ghost:
### 绘绘绘
* 首先需要这行代码   
import matplotlib.pyplot as plt（须先导入这个，否则运行会报错，我的电脑会）
* 主要用到的是这个函数      
  df.plot()  有许多参数可选择，:information_desk_person: [小抄在此](https://blog.csdn.net/h_hxx/article/details/90635650)   
* 使用 %matplotlib inline 魔法命令，可直接在jupyter嵌入图表   
* mpl.rcParams['font.sans-serif']=['SimHei'] 这个可用在图表中让其正确显示中文标签   
  mpl.rcParams['axes.unicode_minus']=False   用来正常显示负号   
## 5. 如何从现有列创建派生新列？ :flags:
### 列列列   
* 新派生列就是变数的转换   
* 相关代码 :snowboarder:  
```
df['新变量'] = df['变量A'] + df['变量B']
df['新变量'] =[转换(x) for x in df['变量A']]   
例如：
data['C'] = data['A'] + data['B']    
data['D'] = [x for x in data['A']]
```
## 6. 如何计算汇总描述性统计信息？ :space_invader:
### 算算算   
* :information_desk_person: [小抄](https://blog.csdn.net/weixin_38664232/article/details/89047510#DataFrame%E4%B8%AD%E5%B8%B8%E8%A7%81%E7%9A%84%E5%85%B6%E4%BB%96%E6%96%B9%E6%B3%95%EF%BC%9A)
* 相关代码 :baby_bottle:
   1. df.describe()   
      df.describe(include=all)  
      数据清理一般都会用到这个函数,其物理意义在于观察这一系列数据的范围。大小、波动趋势等等，便于判断后续对数据采取哪类模型更合适。   
   2. df.count()   
      非空元素计算
   3. df.sum()
      求和   
   4. df.min()   
      df.max()   
      df.mean()   
      df.median()  中位数   
      df.var()  方差   
      df.std()  标准差
# 二、iloc和loc的用法 :beer:   
  * 两个用法实在太相似了，名字也相似.iloc，即index locate 用index索引进行定位，所以参数是整型；loc，则可以使用column名和index名进行定位.
  * loc 不仅可以输入数字也可以直接column名字，**注意先行后列**
  * loc是根据dataframe的具体标签选取列，而iloc是根据标签所在的位置，从0开始计数   
# 三、自我总结 :peach:  
* 一定要用数据科学家的思维去思考问题，不要用程序员的思维去思考如何处理数据
* 千万注意数据的标点符号等要一致，以免后续进行数据清洗、提取数据、分析数据等造成不必要的麻烦和问题
* 多多练习loc和iloc的用法，不然真的很容易混淆，一定一定注意先行后列
* 数据切片的用法多练习，如何切、怎么切、用什么方法切一切取决于我们想如何分析数据
