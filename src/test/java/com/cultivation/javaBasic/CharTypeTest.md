####1、`should_describe_escaped_chars`
- **测试：** 用来描述常用的转义字符

- **修改：** 将对应的转义字符加上

- **查询：** [Character类型](https://docs.oracle.com/javase/10/docs/api/java/lang/Character.html) 	

- **主要问题：** 

1、为什么在字符类中有许多方法接受`int`参数而不是`char`?

Answer：因为在计算机中保存这些字符时，是保存这些字符对应的编号，因此char类型的值也可以直接作为整型值来使用，相当于一个16位无符号整数。传入int整数时，系统会自动的当成char类型处理。

2、Java字符型使用UTF-16编码，可是我们一般设置的编码UTF-8，此处存疑。






