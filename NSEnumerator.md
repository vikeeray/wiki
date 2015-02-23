NSEnumerator用法
===

NSEnumerator是一个枚举迭代类。

从iOS 2.0开始，可以使用NSEnumerator来枚举NSArray、NSDictionary和NSSet对象中的元素。

NSEnumerator本身是个抽象类。它依靠几个工厂方法，如objectEnumerator或keyEnumerator，来创建并返回相应的具体枚举器对象。
