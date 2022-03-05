# C++的rebind

在空间配置器的学习中可以看到rebind的用法，即在allocator中肯定有一个rebind（这是容器所要求的结构）。

rebind的结构：在allocator中<T>，定义了一个rebind，rebind又定义了一个allocator<U>

rebind的作用：通过上面的结构我们可以看到，rebind中的allocator和原来的allocator类型是不一样的，所以rebind的作用是实现对不同类型（T，U）采用同一种内存分配策略（都是allocator），所以在定义了allocator<T>之后，还可以继续定义allocator<T>::rebind<U>::other

参考：[allocator::rebind详解](https://blog.csdn.net/walkerkalr/article/details/22263351)

