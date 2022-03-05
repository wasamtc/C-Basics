# C++的命名空间问题

为什么要引入命名空间：在大型项目中，可能有两个或多个人写出同样的全局变量或其他类型的数据，在使用时就可能造成冲突，所以使用命名空间来避免这种冲突。

怎样使用命名空间：使用关键字namespace来命名空间

为什么不要使用using namespace std：使用这一句相当于声明了整个std的内容，如果自己命名的东西和std中的内容有冲突，那么可能会出现错误。

参考：

[为什么尽量不要使用using namespace std？](https://blog.csdn.net/my_precious/article/details/49701339)

[C++命名空间（名字空间）详解](http://c.biancheng.net/view/2192.html)

[C++头文件和std命名空间（精辟）](http://c.biancheng.net/view/2193.html)

