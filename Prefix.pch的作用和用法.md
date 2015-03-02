Hello World_Prefix.pch:扩展名.pch表示"precompiled header",这是一个你工程要用到的来自于外部框架的头文件列表。位于工程－－targets－－build settings－－AppleLLVM 5.0 Language中的Prefix Header选项

xcode将编译这些头到文件，这将减少你在选择Build 或Build and Go时编译项目的时间。
通常用到的头文件已经自动包含了pch，系统编译每个cpp文件前，都会先include这个文件。
这样就节省了添加include的时间，相当于加速编译.还有就是可以再这里面放入宏，在整个工程中都可以用，节省了时间。

当我们新建一个工程的时候，在Supporting FIles文件下会看到一个以  -Prefix.pch结尾文件的文件，
pch全称是“precompiled header”，也就是预编译头文件，该文件里存放的工程中一些不常被修改的代码，
比如常用的框架头文件，这样做的目的提高编译器编译速度。当我们修改一个工程中某个文件代码时候，
编译器并不是重新编译所有所有文件，而是编译改动过文件。假如pch中某个文件修改了，
那么pch整个文件里包含的的其他文件也会重新编译一次，这样就会消耗大量时间，
所以它里面添加的文件最好是是很少变动或不变动的头文件或者是预编译的代码片段。

一直在用xcode6开发，但项目都是在xcode5上创建的，所以一直没注意到，xcode6竟然干掉pch文件了。

为什么xcode6没有自动创建pch文件呢？

简单地看：我们在写项目的时候，大部分宏定义，头文件导入都在这里，Xcode6去掉Precompile Prefix Header的主要原因可能在于Prefix Header大大的增加了Build的时间。没有了Prefix Header之后就要通过手动@import来手动导入头文件了，在失去了编程便利性的同时也降低了Build的时间。具体原因

StackOverFlow上讨论的已经比较清晰了

StackOverFlow:为什么xcode6没有自动创建pch文件呢？

如何在Xcode6中添加pch（Precompile Prefix Header）？
1，Command+N，打开新建文件窗口：ios->other->PCH file，创建一个pch文件：“工程名-Prefix.pch”：


2，将building setting中的precompile header选项的路径添加“$(SRCROOT)/项目名称/pch文件名”（例如：$(SRCROOT)/LotteryFive/LotteryFive-Prefix.pch）


可以了，编译一下程序，如果有错误检查一下添加的路径是否正确。

3，将Precompile Prefix Header为YES，预编译后的pch文件会被缓存起来，可以提高编译速度


