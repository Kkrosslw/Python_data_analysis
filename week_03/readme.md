# :heart_decoration: week3学习内容+总结！
### :speedboat: 本周学习内容：分进合击（剑法、心法）、分分分、进进进、合合合、数据感
**采用倒叙的方式进行学习**
***
## :surfer: 一、合合合
1. 用 **.agg()** 函数实现聚合,一般和groupby()合用
2. .agg()的各种写法 
```
   1. .agg({"某个变量名":"count","某个变量名":"sum"})   
   2. .agg(["sum","count"])["某个变量名"]
   3. df.groupby("国家")[["某个变量名"]].agg(["count"])
   4. df.groupby("国家")[["企业名称"]].count()
   ps:此处“国家”只是示例变量名
```
## :sunrise: 二、进进进
1. 通常用来计算数据，所用到的函数有：**count,sum,mean,min,max**
2. 注意结合要分析的表格，使用相应的函数来筛选自己想要的数据
3. 在开始之前，应该使用info()函数查看表格的数据类型.如sum/mean会筛选数据类型为int的列
## :helicopter: 三、分分分
1. 用 **.groupby()** 函数实现数据切片。在开始分析数据之前，先观察数据类型，哪些可以切，哪些可以聚合
2. 可以用groupby切一个层级的数据，也可以切多个层级；传递的参数还可以用来做索引
3. 筛选查看单个列或者所需要列的数据统计
4. groupby的属性之一————groups，是一个字典,其键是计算出的唯一组，对应的值是每个组的轴标签（个人理解为类似于索引值）
## :mount_fuji: 四、分进合击出报表
1. 分进合击之剑法
   * 分：groupby   
   * 进：count,mean,sum,min,max
   * 合：agg
2. 分进合击之心法   
   * 分：split
   * 进：apply
   * 合：combine
3. 出报表法
   * Excel分页法
   ```
   with pd.ExcelWriter() as writer:
      某个表格名.to_excel(writer,sheet_name="你要命名的名字")
   或
   with open() as fp
   ```
   * rename改名：修改列名称
   * sort_values排序：当ascending=False时为降序，默认为True为升序；除此外还有sort方法
## :sunrise_over_mountains: 五、数据感
1. pandas类别数据：categorical，是变量数据类型变成catefory 
   * 
    ```
     df.某个列名.astype('category')
    ```
    astype()可用于转化dataframe某一列的数据类型   
    * assign:直接向dataframe添加新的一列，我认为可以是替换原来的一列，并且替换之后可以更改其数据类型   
    ```
   new_df = new_df.assign(国家=df.国家.astype('category'))
   ```
2. 索引项
   * 当使用groupby进行数据切片时，默认切片的第一个为索引列
   * as_index:当值为True时，不显示索引项，以第一列为索引，此时不能用df.loc[]进行取值；当值为False时，显示索引项，可以用df.loc[]进行取值
## :rainbow: 六、我的总结
例行周总结，现在开始。我非常容易把这门课当成代码课，但这门课显然不是，总是被自己的想法所误导。一定一定要用数据科学家的思维去解剖数据、思考问题，认真观察数据类型，例如sum、mean函数会筛选int数据类型，且要想清楚哪些数据可以切，哪些可以合，我们要拿这些数据做什么，每个数据都有它自己的意义。对groupby和agg的用法还不是很熟，需多加锻炼，希望学习本课程之后可以有分析数据的能力！
