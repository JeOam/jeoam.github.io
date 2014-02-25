---
layout: post
title:  斯坦福 iOS7 公开课第三课：Objective-C
---

这是 Stanford CS193p: Developing iOS 7 Apps for iPhone and iPad Fall 2013-14 文字版，按照视频字幕手工编辑完成。这里的内容由于是按照讲话的录音记录下来的，所以文字风格偏口语化，也比较"线性". 视频的内容大部分会记录成文字，但也酌情省略了可以忽略的语句。

本文图片较多，如果图片的注解足够清晰明了，就会省去文字记录，想要看到文章更好的排版效果，可直接浏览 GitHub 里的[文件](https://github.com/JeOam/jeoam.github.io/blob/master/_posts/2014-02-05-Lecture-2-Xcode-5.md)。

---

####Today
#####Card Matching Game
Today we will create a much more sophisticated Model(than a mere deck of playing cards).
And we'll enhance our Controller and View to take advantage.

#####More Detail about Objective-C

* Why Dot Notation?
* More about invoking Class (+) Methods.
* Some clarification about creating new instances of objects.
* A warning about sending messages to nil.

#####Review
Some slides attached for review of first 3 lectures.

###Continue Buliding Our Card Matching Game!
#####Just follow [Lecture 3 Slides](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture-3-Slides.pdf) of this courses(from page 2 to page 111).

* Page 7: In computer programming, lazy initialization is the tactic of delaying the creation of an object, the calculation of a value, or some other expensive process until the first time it is needed. (from [Wikipedia](http://en.wikipedia.org/wiki/Lazy_initialization))

* Page 28: Now the playing of the game is part of our model. It's really important to understand, it's not part of our controller, its part of our model. The model is the what your game is.

* Page 34: When I think about my card gap matchig game, there's a couple of things it just has to know to initialize. It can't just initialize itself like a playing card deck can. A playing card deck knows everything it needs to know about a playing card deck when it's started, but this doesn't really know that. So I need a couple of things. One thing I need is how many cards are we playing with? The second thing that I need is a deck, a deck of cards, because I got to deal these cards out. 

* Page 34: The only other thing I need to do is someone's going to be clicking on these cards; they're going to be flipping over and being chosen and possibly matching, so I need some sort of method to let somebody choose a card.

* Page 23: Usually you pick a card then you pick another card, and if they match you get points, if they don't match they usually both turn back over.

* Page 40: The differentiation between `designated initializer` and `convenience initializer` is: https://developer.apple.com/library/ios/documentation/general/conceptual/devpedia-cocoacore/MultipleInitializers.html.(If the link failed, read this [backup](https://gist.github.com/JeOam/9116926))

###[Lecture 3](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture-3-Slides.pdf) 的内容基本上是讲解 Card Matching Game 的实际代码编写了，基本是 Slides 里面的内容，而且 Slides 做得超详细简明的，基本可以直接看 Slides 就可以了。而且 Lecture 3 开头提到的 Review 并没有在视频中看到，而 Slides 中也注明了。

---

####Lecture 3 done! 

---

