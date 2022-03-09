# 解析C++中explicit

对于类的构造函数来说，仅有1个参数或除了一个参数外其余参数均有默认参数的情况下，有可能发生隐式的类型转换。例如

```C++
#include <iostream>
using namespace std;
 
class A
{
public:
    A(int i = 5)
    {
        m_a = i;
     }
private:
    int m_a;
};
 
int main()
{
    A s;
    //我们会发现,我们没有重载'='运算符,但是却可以把内置的int类型赋值给了对象A.
    s = 10;
    //实际上,10被隐式转换成了下面的形式,所以才能这样.
    //s = A temp(10);
 
    system("pause");
    return 0;
}
```

为了防止这种情况，我们在类的构造函数的声明前加上explicit，阻止这种隐式转换，即必须显式的调用这个函数才能进行构造和转换。

```C++
#include <iostream>
using namespace std;
 
class A
{
public:
    //这里用explicit关键词来修饰类构造函数.
    explicit A(int i = 5, int j = 10)
    {
        m_a = i;
        m_b = j;
    }
private:
    int m_a;
    int m_b;
};
 
int main()
{
    A s;
    //这样直接赋值,会被提示错误,因为explicit抑制隐式转换的进行
    s = 10;//这样会报错!!!
    //当然显示转换还是可以的.
    s = A(20);
 
    system("pause");
    return 0;
}
```

这样就可以阻止这种隐式转换。

前面说完了再补充一点，其实也不是必须要一个参数或出来一个参数外其余全是默认参数才能发生隐式转换，只要不加explicit，后面赋的值只要符合构造函数的参数都会隐式转换。

参考：

[C++中explicit的作用及用法](https://blog.csdn.net/qq_36570733/article/details/100585625)