#### python基础

##### 格式基础
1. 文件声明
    ````java
    #!/usr/bin/python
    # -*- coding: UTF-8 -*-
    ````
##### 命名规范
1. 命名组成：数字、字母、下划线
2. 区分大小写
3. 单下划线， 不能直接访问的类属性，可以用类提供的接口访问。_foo
4. 双下划线，代表类的私有成员。__foo
5. 前后双下划线，特殊方法专用的标识。__init__()
6. python的保留字段
7. 使用‘\’作为换行符。total = item_one + \ + item_two
8. 使用了（），【】，{}不用区分换行
9. 单引号、双引号、三引号标识字符串，三引号为文本段
10. print x，y  //输出一行，不换行；   print x;print y //输出两行，换行。加了，才不换行


##### 数据类型
1. Number（数字）：int,long,float,complex
2. String（字符串）
3. List（列表）
4. Tuple（元组）：元组里面的内容，值都是不允许更新的
5. Dictionary（字典）

##### 运算符及优先级
	指数运算        **
	按位翻转        ~
	乘除           * /
	加减
	右移、左移      <<  >>
	按位与         &
	按位或         |
	比较运算符      <=
	等于运算符      ==
	赋值运算符      =+
	身份运算符      is, is not
	成员运算符      in, not in
	逻辑运算符      not,or,and

##### 常用语句
1. 条件语句：if;else if; else
2. 循环语句：while,{for i in range(0,20): else:}
3. break,continue,pass


# 
#
##### 常用问题处理

###### 字典dict
1. 获得所有的keys `dict.keys()`，得到
2. 获得每一对key,value：`for item_key, item_value in dict.items()`

###### for 循环
1. 基本语法`for i in range(0, 10)`
2. 搭配else：当i 不在range的范围内，执行else
3. 









