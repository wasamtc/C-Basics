# size_t，ptrdiff_t

这两个的具体长度都是机器相关的，设计出来就是为了适应不同的平台。

size_t主要是指示数组的长度或下标，不能小于0.

prtdiff_t主要是指示两个指针间的差距，与具体类型无关，因为他的计算方式是地址相减除以类型的长度

除此之外还有size_type指示容器长度或下标，difference_type指示两个迭代器之间的差距，这两个是STL独有的。

参考：

[size_t、ptrdiff_t](https://www.cnblogs.com/liulipeng/archive/2012/10/08/2715246.html)





更正：size_t机器相关的意义是它的大小是当前机器的内存地址大小，如32位机上size_t就占32bit，这样size_t可以表示该机器上的任一地址和任一大小。也就是说，用size_t一般不存在越界的问题。

ptrdiff_t主要还是用来表示一个类型有几个这种。

参考：

[为什么size_t重要](https://www.jianshu.com/p/6085776b7d77)