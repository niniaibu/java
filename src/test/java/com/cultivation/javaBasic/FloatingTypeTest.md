####1、`should_not_get_rounded_result_if_convert_floating_number_to_integer`
- **测试：** 将浮点数转换成整形时会怎么样

- **修改：** 注意到将浮点数强制转换为整数时，会出现直接截断小数部分，仅仅保留整数部分

- **查询：** [float强制转换为int](https://docs.oracle.com/javase/10/docs/api/java/lang/Float.html#intValue()) 	
> 注：字符串不能直接转换为基本类型，需要通过对应的包装类实现转换

- **主要问题：** 官方文档中并无涉及强制转换的函数，只看到`intvalue`这个函数，是否就是强制转换函数`(int)value？什么情况下需要注意强制转换？


####2、`should_judge_special_double_cases`
- **测试：** 测试除浮点数0，比较是否为无穷大值和是否是数值

- **修改：** 仅修改原来的`isInfinity`函数，存在修改疑问

- **查询地址：** [Double类中的isInfinity函数](https://docs.oracle.com/javase/10/docs/api/java/lang/Double.html#isInfinite(double))、[Double类中的isNaN函数](https://docs.oracle.com/javase/10/docs/api/java/lang/Double.html#isNaN(double))

- **主要问题：** 讨论所得，应该是java中存在直接判断的方法，如`isInfinity`和`isNaN`函数，可是没有其实现方法，可是测试代码中需要重新调用，如何查看函数源码呢或者底层函数如何实现？

> continue to learn



####3、`should_not_round_number_when_convert_to_integer`
- **测试：** 强制类型转换

- **修改：** 与1修改一致

- **主要问题：** 与例1所涉及到的知识点是否有不同？



####4、`should_round_number`
- **测试：** 将double类型的浮点型数转换为long类型整数，且规则为四舍五入

- **修改：** 查找四舍五入函数的输入和对应输出，调用`Math.round`函数进行四舍五入操作

- **查询地址：** [输入为double类型的四舍五入函数](https://docs.oracle.com/javase/10/docs/api/java/lang/Math.html#round(double))、[CSDN四舍五入](https://blog.csdn.net/happylifex/article/details/44277891)

- **主要问题：** 在查询四舍五入函数时候会有使用`BigDecimal`，会有使用`DecimalFormat`，格式控制和`Math.round`函数，一般都在什么条件下使用？

> continue to learn
