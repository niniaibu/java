#### 1、`should_get_range_of_primitive_int_type`
- **测试问题：** 测试的是int类型最大最小值，了解其范围
- **修改原因：** 因为TODO中指明不涉及到具体数字，而是使用属性或者变量来赋值；先前想要直接赋值给某变量，浏览之后发现存在`Integer.MAX_VALUE`和`Integer.MIN_VALUE`这静态变量，故直接赋值。
- **查询地址：** [Integer](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Integer.html)


#### 2、`should_get_range_of_primitive_short_type`
- **测试问题：** 测试的是short类型最大最小值，了解其范围
- **修改原因：** 与上例今天类型一样，举一反三。存在`Short.MAX_VALUE`和`Short.MIN_VALUE`这静态变量，故直接赋值。
- **查询地址：** [Short](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Short.html)

#### 3、`should_get_range_of_primitive_long_type`
- **测试问题：** 测试的是long类型最大最小值
- **修改原因：** 同上两例
- **查询地址：** [Long](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Long.html)

#### 4、`should_get_range_of_primitive_byte_type`
- **测试问题：** 测试的是byte类型最大最小值
- **修改原因：** 同上三例
- **查询地址：** [Byte](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/Byte.html)

#### 5、`should_overflow_silently`
- **测试问题：** 测试的当到达int类型的上限之后，在加1会出现怎样的情况，即int类型的向上溢出
- **修改原因：** 因为最高位为符号位，0为正整数，1为负整数；故当正整数加1时，会向最高位进1的，即由0x7fffffff变为0x80000000，正好为Integer的最小值。


#### 6、`should_underflow_silently`
- **测试问题：** 测试的当到达int类型的下限之后，在减1会出现怎样的情况，即int类型的向下溢出
- **修改原因：** 与5相似，最高位为符号位，即由0x800000000变为x7fffffff，正好为Integer的最大值。


#### 7、`should_throw_exception_when_overflow`
- **测试问题：** 测试的是数据是否能在溢出的时候可以抛出异常来
- **修改原因：** 重写add函数，当int类型数据溢出时，抛出一个算术异常，如果正常则可以进行加减。
- **查询地址：** [overflow](https://blog.csdn.net/qq_33330687/article/details/81626157)

> 继续修改======================

- **修改原因2：** 直接调用Integer包装类中的sum函数，此处还是未能找到java已给出的功能。

#### 8、`just_prevent_lazy_implementation`
- **测试问题：** 测试重写的add函数是否仅仅抛出异常，能否处理正常情况
- **修改原因：** 正常add()函数的操作
- **具体问题：** 是否有更简单的异常处理操作,即如何更好的重写add方法？

#### 9、`should_take_care_of_number_type_when_doing_calculation`
- **测试问题：** 测试数据不同写法进行除等算术操作时，会出现不一样的结果，需要说明的是需要在计算的时候注意数据类型
- **修改原因：** 根据计算来，int类型除法仅保留商的部分，忽略余数，所以导致结果不一致

#### 10、`should_truncate_number_when_casting`
- **测试问题：** 测试如何截断数据，当从大的数据类型强制转换到小的数据类型时，精度丢失的问题
- **修改原因：** int类型是4字节，共32位；short类型是2字节，共16位，故会丢失高位数据

#### 11、`should_increment`
- **测试问题：** 测试i++问题，变量使用和自增先后顺序问题
- **修改原因：** i++即先使用变量i，再使i的值自增1

#### 12、`should_increment_2`
- **测试问题：** 测试++i问题，变量使用和自增先后顺序问题
- **修改原因：** ++i即先使i的值自增1，再使用变量i

