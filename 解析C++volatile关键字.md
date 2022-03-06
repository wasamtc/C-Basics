# 解析C++volatile关键字

volatile其实就一个功能，告诉编译器volatile修饰的变量易变，如果你要取这个变量的值的话，请去真正存这个变量的地方取，不要在什么临时存储的地方（如寄存器）取。

参考：

[谈谈C++的volatile关键字以及常见的误解](https://www.cnblogs.com/zhao-zongsheng/p/9092520.html)

[详解C/C++中volatile关键字](https://blog.csdn.net/weixin_44363885/article/details/92838607)

