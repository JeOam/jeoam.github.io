---
layout: post
title: Categories, Protocols and Delegation
---

###Categories and Class Extensions
```
@interface Fraction (MathOps)
-(Fraction *) add: (Fraction *) f;
-(Fraction *) mul: (Fraction *) f;
-(Fraction *) sub: (Fraction *) f;
-(Fraction *) div: (Fraction *) f;
@end 
```
A special case allows creating a category without a name; that is, no name is specified between the ( and ). This special syntax defines what is known as a class extension. When you define an unnamed category like this, you can extend the class by adding additional instance variables and properties. This is not allowed for named categories. Methods declared in a class extension are implemented in the main implementation section for the class and not in a separate implementation section.

Class extensions are useful, because their methods are private. So, if you need to write a class that has data and methods that can be used only within the class itself, a class extension might just fit the bill.

The methods are private in the sense that they’re not advertised in the interface section.  However, if someone knows the name of a private method, she can still call it.

Remember that extending a class by adding new methods with a category affects not just that class, but all its subclasses as well.

---

###Protocols

A protocol is a list of methods that is shared among classes. The methods listed in the protocol do not have corresponding implementations; they’re meant to be implemented by someone else (like you). A protocol provides a way to define a set of methods that are somehow related with a specified name. The methods are typically documented so that you know how they are to perform and so that you can implement them in your own class definitions, if desired.

You tell the compiler that you are adopting a protocol by listing the protocol name inside a pair of angular brackets (<...>) on the @interface line.

Define a protocol：

```
@protocol NSCopying
- (id)copyWithZone: (NSZone *)zone;
@end
```

Conform/adopt that protocol：

```
@interface AddressBook: NSObject <NSCopying>
```

You don’t need to declare the methods（copyWithZone:） in the interface section. However, you need to define them in your implementation section.



If you define your own protocol, you don’t have to actually implement it yourself. However, you’re alerting other programmers that if they want to adopt the protocol, they do have to implement the required methods. 
```
@protocol Drawing
-(void) paint;
-(void) erase;
@optional
-(void) outline;
@end
```
Note the use of the @optional directive here. Any methods that are listed following that directive are optional.

(And you can subsequently switch back to listing required methods by using the @required directive inside the protocol definition.)

When you define a protocol, you can extend the definition of an existing one.
```
@protocol Drawing3D <Drawing>
```

---

###Delegation

You can also think of a protocol as an interface definition between two classes. The class that defines the protocol can be thought of as delegating the work defined by the methods in the protocol to the class that implements them.

In that way, the class can be defined to be more general, with specific actions taken by the delegate class in response to certain events or to define specific parameters.

---

Excerpt From: Stephen G. Kochan. “[Programming in Objective-C, Fifth Edition](http://book.douban.com/subject/11622649/).”