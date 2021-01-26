1.对于int类型的装箱和拆箱，是分别是使用如下方法

装箱：Integer.valueOf(int) .这个需要用Integer a = 10; 然后看字节码即可知道

在jdk1.8中，Integr.valueOf方法有判断入参是否在-128~·127之间，有的话就用cache，所以

```java
Integer a = 127;
Integer b = 127;
a==b; // true

Integer a = new Integer(127);
Integer b = new Integer(127);
a == b; // false
```

拆卸的方法是Integer.intValue();





2.方法可以改变入参的属性，但你不能改变入参指向的地址。如果你改变了指向的地址，那么你操纵的就是另外一个对象。原本的对象不变。

java是值传递的，而不是引用传递。

[java方法是值传递还是引用传递](http://www.javadude.com/articles/passbyvalue.htm#/introduction)

```java
In programming language design, a "pointer" is a variable that indirectly tracks the location of some piece of data. The value of a pointer is often the memory address of the data you're interested in. Some languages allow you to manipulate that address; others do not.

A "reference" is an alias to another variable. Any manipulation done to the reference variable directly changes the original variable.
```

```java
The Java Spec says that everything in Java is pass-by-value. There is no such thing as "pass-by-reference" in Java.

The key to understanding this is that something like

Dog myDog;
is not a Dog; it's actually a pointer to a Dog.

What that means, is when you have

Dog myDog = new Dog("Rover");
foo(myDog);
you're essentially passing the address of the created Dog object to the foo method.

(I say essentially because Java pointers aren't direct addresses, but it's easiest to think of them that way)

Suppose the Dog object resides at memory address 42. This means we pass 42 to the method.
```

