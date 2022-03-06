首先要运行C++一般需要那四个文件，关于四个文件的普通配置可以看：[vscode中C++四个重要文件](https://blog.csdn.net/weixin_41836738/article/details/121366351)

然后是对于一些项目的编译经验：

vscode只会编译当前的cpp，即file下的内容，而其他的cpp不会编译，这就导致很多时候引用自定义的头文件无效。这个时候可以在tasks文件下的argus下的-g中加上workspaceFolder，这是当前大的文件夹，然后/src/**，这个要根据具体的来。



如果要编译thread，要在-o后面加-pthread，具体看：[VScode在Ubuntu中执行多线程程序](https://blog.csdn.net/snowsking/article/details/120614393)

