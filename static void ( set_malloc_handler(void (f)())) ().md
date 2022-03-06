# 解析static void (* set_malloc_handler(void (*f)())) ()

在《STL源码剖析》中有一段代码：

```C++
static void (* set_malloc_handler(void (*f)()))()
{
    void (* old)() = __malloc_alloc_oom_handler;
    __malloc_alloc_oom_handler = f;
    return(old);
}
```

这段代码难就难在函数的定义上，后面看了几篇博客，自己慢慢想了想也想明白了。

首先我们要清除void(*f)()是在干什么，这段代码其实定义一个函数指针，这个函数指针的名字为f，指向的函数返回void，参数列表为空。其实我们只要知道了这个，就可以慢慢琢磨看懂上面的代码了。

对于

```C++
static void (* set_malloc_handler(void (*f)()))()
```

我们首先从内部看起，先看* set_malloc_handler(void (*f)())，容易看出（是比较容易吧）set_malloc_handler是既有返回值又有形参列表，所以set_malloc_handler是一个函数指针（或者说函数的名字），这个函数的参数又是一个void( *f)()，说明它的参数就是一个函数指针。

OK，现在*set_malloc_handler(void ( * f)())搞清楚了，外面呢，其实如果我们把set_malloc_hander(void( * f)())看作是一个整体p的话，我们会发现外面整体的代码就编程了static void (*p)()，是不是和前面的一模一样，而set_malloc_handler不就是返回了一个指针吗？如果我们把set_malloc_handler返回的指针就命名为p的话，那么外面做的事情就是把p定义为一个指向参数为空，返回为void的函数的指针。

综上，这段代码的意义就是定义了一个叫set_malloc_handler的函数，这个函数的参数是一个函数指针（这个指针指向一个参数为空，返回为void的函数），返回值也是一个函数指针（这个指针指向一个参数为空，返回为void的函数）。

如果我们

```C++
typedef void(*ptr)()
```

那么static void (* set_malloc_handler(void (*f)())) ()就可以替换为

```C++
static ptr set_malloc_handler(prt)
```

