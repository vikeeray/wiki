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
