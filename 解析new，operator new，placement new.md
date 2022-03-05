# 解析new，operator new，placement new

## new

new的一般操作为 A *p = new A，这样即开辟了一块空间，p指向这块空间（即p的值就是这块空间的首地址）。

这种new操作其实分为两步，第一步是用operator new申请空间(和malloc差不多)，第二步是调用A的构造函数（当然还有返回指针）。这就是new的用法。

## operator new

有时候我们还没有设计好一种类型（如模板类），但是上面的new又要用到类的构造函数，所以这时候可以直接用operator new来申请空间，例如 A *p = (A *)::operator new(sizeof(A))（里面还可以乘个n让p指向一大块空间），operator new是个函数所以可以重载，如果要使用默认的，直接在全局::里面找就行

## placement new

有时候我们需要经常用到某种类型的指针，这个时候可能就要反复申请内存（或者说申请堆），而placement new就是提供一种机制来指定一个空间给某个对象用，例如我们已经有个指针mem了，我们可以A *p = new(mem) A，这样p指向的就是mem指向的空间，并且用了A的构造函数，但是p不能自动析构（不然把人家mem的内容都给整没了），所以如果要释放这块空间要显示析构p->~A()。

## operator new与placement new的结合

因为operator new只是分配了空间，还没有构造，所以在分配空间后，明确了类型，我们可以使用placement new来为此调用构造函数。例如：A *p = (A *)::operator new(sizeof(A))，明确了类后，new(p) A(argus)，这样就完成了p所指对象的构造。