NSEnumerator用法
===

NSEnumerator是一个枚举迭代类。

从iOS 2.0开始，可以使用NSEnumerator来枚举NSArray、NSDictionary和NSSet对象中的元素。

NSEnumerator本身是个抽象类。它依靠几个工厂方法，如objectEnumerator或keyEnumerator，来创建并返回相应的具体枚举器对象。

```objc
NSDictionary *myDic=[[NSDictionary alloc]initWithObjectsAndKeys:@"张三",@"name",@"李四",@"name", nil];
        
NSUInteger count = [myDic count];  
NSLog(@"词典的数量为：  %lu",count); 

NSEnumerator * myEnumerator = [myDic keyEnumerator];  

 
for (NSObject *object in myEnumerator) {  
    NSLog(@"遍历KEY的值: %@",object);  
}

myEnumerator = [[myDic allValues] objectEnumerator];
NSString *value;
while((value = [myEnumerator nextObject]))
{
    NSLog(@"遍历的值: %@",value);
}

//通过KEY找到value  
NSObject *myObject = [myDic objectForKey:@"name"];

if (myObject != nil) {  
    NSLog(@"通过KEY找到的value是: %@",myObject);  
}  

NSMutableDictionary *mydic2 = [NSMutableDictionary dictionaryWithCapacity:10];  
[mydic2 setObject:@"Alex Hu" forKey:@"name"];  
[mydic2 setObject:@"1388888888" forKey:@"mobile number"]; 

for (NSObject *object in [mydic2 objectEnumerator]) {  
    NSLog(@"遍历的值: %@",object);  
}

NSSet *mySet=[NSSet setWithObjects:@"A",@"B",@"C",@"D",[NSNumber numberWithInteger:123], nil];
count=[mySet count];
NSLog(@"count= %lu",count);

myEnumerator=[mySet objectEnumerator];
for (NSObject *object in myEnumerator) {
    NSLog(@"myEnumerator value=%@",object);
    if ([object isEqualTo:@"A"]) {
        NSLog(@"找到A了");
    }
    if ([object isEqual:@"B"]) {
        NSLog(@"找到B");
    }
}

NSArray *mySetArr=[mySet allObjects];
for (NSUInteger i=0; i<[mySetArr count];i++) {
    NSLog(@"%lu =>%@",i,[mySetArr objectAtIndex:i]);
}

if ([mySet containsObject:@"D"]) {  
    NSLog(@"集合中包含 D这个对象");  
}  
```
