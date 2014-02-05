---
layout: post
title:  斯坦福 iOS7 公开课第二课： Xcode 5
---

这是 Stanford CS193p: Developing iOS 7 Apps for iPhone and iPad Fall 2013-14 文字版，按照视频字幕手工编辑完成。这里的内容由于是按照讲话的录音记录下来的，所以文字风格偏口语化，也比较"线性". 视频的内容大部分会记录成文字，但也酌情省略了可以忽略的语句。

本文图片较多，如果图片的注解足够清晰明了，就会省去文字记录，想要看到文章更好的排版效果，可直接浏览 GitHub 里的[文件](https://github.com/JeOam/jeoam.github.io/blob/master/_posts/2014-02-05-Lecture-2-Xcode-5.md)。

---

####Today
Today we're going to have some slides at the beginning, little more talking, and then I'm going to have a quite big demo that's going to try and hopefully synthesize all the things I've been talking about on the slides for the first two lectures, which is that we're going to start building our card game. This card matching game is going to be our substrate for the first two weeks of learning some Objective-C, learning about Xcode, learning about how iOS hooks up the controller, and the view, and the model to make a UI.

If you remember from the last time, we did the card thing, it was a very simple class. Today, we're going to go on and do another class, which is a deck! The deck of cards. And remember, that card and deck are generic; they're not specific to playing cards. A playing card, like the ace of clubs(梅花 A) or the king of the hearts(红心国王)

####Objective-C Demo

* A getter is really just setting and getting a value. It might have side effects, like setting it might update the UI, or getting it might make sure it's initialized first.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_01.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_02.jpg)
* If you want to have a optional argument, the only way to do that in Objective-C is to delcare a new method. So just understand that, in some languages, some arguments can be optional or you can kind of overload things to have the same method name have different arguments. No. In Objective-C every method is completely distinct and has a distinct name.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_03.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_04.jpg)
* Our deck is just going to contain a bunch of cards.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_05.jpg)
* Objects in array can be of any class. There's really no way to specify what kind of objct is in an array. Some languages allow you to do that. You can specify "This is an array of strings" and it knows that. But in Objective-C you can't do that. That's a little bit of the wild west of Objective-C. but there are ways to kind of check and see what the objects are if you want to be really safe about it. Normally an NS array is immutable. Oncd it's created, whatever objects enter it, that's the objects that are in it forever. So if we want array where we can add stuff, we have to use its subclass of NS array called NS mutable array.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_06.jpg)
* Insert object add index(insertObject:atIndex:) is a method in NS mutable array, not in NS array -- only in NS mutable array because that would be mutating it -- that inserts the object at that index in the array and index zero is going to be the top that we're going to define. And then otherwise if we're not going to put it at the top, we're going to put it at the bottom, we're going to use a different NS mutable array method called add object, and that just adds something at the end of the array.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_07.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_08.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_09.jpg)
* arc4random() is a C library function. It gets a random integer.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_10.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_11.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_12.jpg)
* Let's move onto another class, which is playing card. The reason I'm showing you playing cards, i just want to to show you what it looks like to make a subclass of another class that you've written. So playing card is subclass of card. And this is the specific card like king of hearts, three of diamonds. Now, it has properties that are specific to a playing card, which is the suit and rank. The rank being like a three, four, a jack, king; and the suit being hearts, diamonds, clubs.The four French playing card suits used primarily in the English speaking world: spades (♠), hearts (♥), diamonds (♦) and clubs (♣).
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_13.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_14.jpg)
* And here I'm using notice NSU integer instead of unsigned int. So NSU integer and unsigned int are almost exactly the same thing. The only thing about NSU integer is it's typedef. It might be a little different on different platforms. For example, the new iPhone 5s are 64-bit processers. So NSU integer is going to be a 64-bit int, unsigned int on an iPhone 5. And it might only about a 32-bit one back on an iPhone 4 and before.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_15.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_16.jpg)
* Notice that our rank is really nice because if our rank is zero, which it starts out being when we say new playing card, all the instance variables are zero so rank would be zero, we get this nice question mark. But our suit starts out as nil, and it would be nice if the suit also returned question mark if it was unsaid, if it was nil. So here I'm just overriding the getter of suit to say: "If return, if my suit is nill, then return the question mark, otherwise when my suit's not nil, then return what the suit is."
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_17.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_18.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_19.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_20.jpg)
* Every time I use the at sign open square bracket--the blue one -- to create an array, that's actually creating a new array every time. That at sign square bracket and all this array stuff is really just calling methods. That's calling a method like `alloc` `init` with array with objects or something like that.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_21.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_22.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_23.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_24.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_25.jpg)
* The only thing we really use plus methods for, class methods, is two things really: Creating things like in the previous slide when we had string with format that's a class method that was creating a string for us; and then also utility methods like this, like the return constants and things that, you know, our class wants and utility methods.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_26.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_27.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_28.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_29.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_30.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_31.jpg)
* method `maxRank` looks at how many strings are in rank strings. 
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_32.jpg)
* Never call that alloc thing without wrapping an init around it. That makes on snse to have an object allocated in the heap that's never been initialized. And vice versa: Never call that init except for when you wrap it around an alloc. And dfinitely never call that init more than once.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_33.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_34.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_35.jpg)
* `- (instancetype)init`: `init` is always going to return self. instancetype  is new for iOS 7.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_36.jpg)
* A playing card deck has 52 cards in it, one of each kind of card.
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_37.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_38.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_39.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_40.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_41.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_42.jpg)
![Lecture-2-Code-Demo](https://raw2.github.com/JeOam/jeoam.github.io/master/images/Lecture-2-Code-Demo_Page_43.jpg)

#####Okay, so that's it for the slides.

---

####Lecture 2 done! 

---

