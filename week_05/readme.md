# :eyes:Week5学习内容以及总结
## 一、本周内容:分进合击进阶分析策略:snowman: 
1. 什么叫数据透视表？   
   透视表是一种对数据动态排布并且分类汇总的表格格式，在pandas中它被称为pivot_table
2. pivot 和 pivot_table   
   * pivot重点在于合并同类项，且在行与列的交叉点值的索引必须是唯一的，否则会报错；但使用pivot_table可以避免这个问题
   * pivot_table 比 pivot 多了func方法，更加方便
   * pivot_table 是 pivot 的泛化它允许在数据集中聚合相同有相同目标的多个值
   * 我觉得pivot_table比pivot更加好用一点
3. reset_index 和 set_index
   * set_index 可以设置单索引和复合索引   
   * reset_index 可以还原索引，重新变为默认为整型索引，即进行默认索引，取消groupby分组，将组别变成普通的列。参数level控制了具体要还原的那个等级的索引。
4. 数据框排序：sort_values和sort_index
   * sort_index时按列索引进行排序，sort_values可根据指定列数据也可根据指定行的数据排序，更加灵活
   * 其参数axis=0/1,当等于0时，对纵轴有影响，方向从上到下；等于1时，对横轴有影响，方向从左到右
   * ascending是否按指定列的数组升序排列，默认为True，即升序排列
5. plot可视化
   * 可以将我们分析完成后的表格进行可视化展示出来，且可以设定字体，但是设定字体有坑，需多踩踩
## 二、我的例行总结:maple_leaf:   
   本周的内容是前两周内容的进阶，groupby、agg只是分进合击的初阶，我们这周使用的pivot和pivot_table则是进阶。且也更深入了解了其他函数方法的使用，但我仍然对函数方法的参数概念很混淆，比如reset_index()的参数axis。同时也进一步学习了可视化模块matplotlib，对图表的字体简单使用。分析数据的方法实在是太多了，以致于我到现在对数据该如何切片、如何分析还是有点点迷茫，只能多加练习了。:full_moon_with_face:
   
   
