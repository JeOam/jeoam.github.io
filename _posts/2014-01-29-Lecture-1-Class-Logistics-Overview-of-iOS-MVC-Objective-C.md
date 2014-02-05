---
layout: post
title:  斯坦福 iOS7 公开课第一课：Class Logistics, Overview of iOS, MVC, Objective-C
---

这是 [Stanford CS193p: Developing iOS 7 Apps for iPhone and iPad Fall 2013-14](https://itunes.apple.com/cn/course/developing-ios-7-apps-for/id733644550) 文字版，按照视频字幕手工编辑完成。这里的内容由于是按照讲话的录音记录下来的，所以文字风格便口语化，也比较"线性". 视频的内容大部分会记录成文字，但也酌情省略了可以忽略的语句。

想要看到文章更好的排版效果，可直接浏览 GitHub 里的[文件](https://github.com/JeOam/jeoam.github.io/blob/master/_posts/2014-01-29-Lecture-1-Class-Logistics-Overview-of-iOS-MVC-Objective-C.md)。深受 md 格式解析不统一的害！！

---

Welcome to Stanford CS193P fall of 2013-14, We are going to be covering developing applications for iOS, so specifically iOS7. iOS is really cool platform for building apps. 

###What will I learn in this course?

* How to build cool apps
  * Easy to build even very complex applications
  * Result lives in your pocket or backpack!
  * Very easy to distribute your application through the AppStore Vibrant development community
  
* Real-life Object-Oriented Programming 
  * The heart of Cocoa Touch is 100% object-oriented
  * Application of MVC design model
  * Many computer science concepts applied in a commercial development platform: Databases, Graphics, Multimedia, Multithreading, Animation, Networking, and much, much more! 
  * Numerous students have gone on to sell products on the AppStore

---

###Prerequisites
The prerequisites for this class are super duper important.    

* Most Important Prereq!  
  * Object-Oriented Programming
  * CS106A&B (or X) required
  * CS107 or CS108 or CS110 required
  * (or equivalent for non-Stanford undergrad)

* Object-Oriented Terms
  * Class (description/template for an object)
  * Instance (manifestation of a class) 
  * Message (sent to object to make it act) 
  * Method (code invoked by a Message) 
  * Instance Variable (object-specific storage) 
  * Superclass/Subclass (Inheritance)
  
If you are not very comfortable with all of these, this might not be the class for you! 

This is an upper-level CS course. If you have never written a program where you had to design and implement more than a handful of classes, this will be a big step up in difficulty for you.

iOS7 is completely object-oriented. The whole structure, the design of the thing, is object-oriented.

---

###Assignments

* Weekly Homework
  * 6 weekly (approximately) assignments 
  * Individual work only
  * Required Tasks and Evaluation criteria
* Final Project
  * 3 weeks to work on it
  * Individual work only
  * Keynote presentation required (2 mins or so)
  
All of the homework assignments have detailed write-up of the required task and what we're evaluating you on, and they also have hints in there. They're basically reinforcing what has been taught in lecture in that week.

I'm a big believer in a teaching methodology, which is I'm going to tell you about a concept, via slides, and then I'm going to show you it by demoing it to you, actually writing an application that does, then I'm going to ask you to do it on the homework.

So that's three times you're going to see every single thing pretty much in this class. By the end of that, you're going to know how to do it.

---

###What’s in iOS?
This is just a high-level overview
 
#####1. Core OS, which is the stuff that's close to the hardware.

       OSX Kernel, Mach 3.0, BSD, Sockets, Security, Power Management, Keychain Access, Certificates, File System Bonjour

   * At the Core OS layer, is a Unix Kernel. This is a Unix operating system on this device. And BFD-based(BFD is Binary File Descriptor library) mock, and so you get everything you get with Unix. 
   * You're getting sockets and you're getting file system with Unix, permissions, all that stuff, plus you're getting a bunch of other stuff that's kind of specific to a mobile device like power management, and key chain access to kind of manage the security of things.
   * Bonjour, which is this kind of network, finding other things on the network
   * It's a very powerful underlying operating system. But all of that API, or most of it is in C, and we want to be programming kind of purely object-oriented layer.

#####2. Core Services, which is an object-oriented layer[error] on top of Core OS.  

       Collections, AddressBook, Networking, File Access, SQLite, Core Location, Net Services, Threading, Preferences, URL Utilities

   * We're going to be mostly operating when we're talking, touching those things at the Core Services[error] layer. So this layer has things like language, things that kind of make the language more powerful, like arrays and dictionaries, and strings like that, plus it has object-oriented ways to access the file system. It has object-oriented ways to find out the GPS location of your device, for example, it has ways to do multithreading. All this stuff what you want to be able to do, but you want to stay in an object-oriented kind of mindset as you're doing them all. There's a huge layer, foundation layer there at Core Services for doing that.

#####3. Media, because these devices are basically iPods with a phone in them or with a big screen on them, but media is really important to these devices, in them or with a big screen on them 

       Core Audio, OpenAL, Audio Mixing, Audio Recording, Video Playback, JPEG, PNG, TIFF, PDF, Quartz (2D), Core Animation, OpenGL ES

   * At the Media layer, you've got video here, you've got video editing, you got images that it can display, it's incredibly powerful audio for doing 3D audio, if you have games, you can make the Thai fighters feel like they're ripping by you and stuff. All that stuff is in here. This is the part of iOS that really I can't cover in a lot of depth.

#####4. Cocoa Touch, which is the UI layer

       Multi-Touch, Core Motion, View Hierarchy, Localization, Controls, Alerts, Web View, Map Kit Image Picker, Camera

   * Cocoa Touch is where we're going to spend most of our time. This is where you are going to be building buttons and sliders and text fields, talking to each other, and animation happening, things sliding in and out, and, you know, fading out and fading in. If you want to get a picture from the camera, from the user, you can do that. Things like localization so that you're app can run in many countries in the world and up your sales by doing that. A whole map kit for doing all the 3D maps that you've probably seen in iOS7 and all that stuff is all in there. And there's even a view in there that's an entire web brower in a little rectangle that you can just plop right into your app. So these are really high-level objects, and we're going 
 to really be diving into this layer. So this is really the primary. And it's called Cocoa Touch because the API in here was originally developed for Mac OS X, and it was called Cocoa, and of course then when they went to iOS, they adapted, and a lot of API is shared between the two platforms. In fact, if you develop an iOS app and then you say someday, oh, I want to develop an app for the Mac using Cocoa, it's going to be very similar. So Cocoa Touch, obviously, is the touchscreen version of Cocoa. 

---

###Platform Components
#####1. Tools

   * What's great on this platform is pretty much a one-tool fits all. There's this one tool, Xcode 5, and everything's in ther. You're debugger's in there, all your source code editing, your source code control, the UI building, everything is in this one app. 
   * There's a little adjunct there, Instruments, which is for things like profiling your app and things like that, Memory usage, those kind of things. but you're really all was inside Xcode 5.

#####2. Language

   * There's a new language for you to learn, Objective C.

#####3. Frameworks
   * Any big system like this groups all of its objects into libraries, essentially. We call them Frameworks in iOS. So there are dozens of frameworks in iOS. The two main ones we're going to look at, at the begining of the course, are foundation, that's where all that Core Services stuff is, like arrays and dictionaries and all that.  And then UI kit, that's where buttons and sliders and all those things aree. But there's a whole bunch of other frameworks like Core Data, that's the object-oriented database, Core Motion, that's the gyro and accelerometer, Map Kit, obviously the maps, and there's dozens more.

#####4. Design Strategies
   * A design strategy called MVC. This is not unique to iOS, other platforms use MVS, Model View Controller, as their fundamental design strategy. The main thing to see in MVC here is to see how I talk about it so that when we get into iOS, and I start saying things like your models is UI independent, you'll know what I'm talking about and we'll all be on the same page.
   * MVC is essentially a strategy for how to organize all the classes in your application. And what we do fundamentally is we divide all the classes into one of there camps: the Model camp, the Controller camp, and the View camp. The Model is essentially the what of your program(but not how it is displayed).
![images-MVC](https://raw.github.com/JeOam/jeoam.github.io/master/images/MVC.png)
   * As we're doing this MVC talk, I'm going to talk  about our first application we're going to build which is a card matching game. It's gotta bunch of cards on the screen, like playing cards, Ace of Clubs and all that, and you're going to be able to go choose the cards and you'll get certain points if they match. Like the suit matches or the rank matches, or whatever, you get more points, less points, whatever, but you're doing that. In that kind of application, a little card matching game, the cards and the deck, and even the logic for how the game is played are all UI independent, and in the model. So how the cards get drawn on screen is the job of the controller. So the controller is, it's job to figure out how am I going to take this set of cards and display them on screen, and then animate their movement and things like that. So the controller controls how the model is presented on screen, and the view, the minions, the classes that the controller is going to use, kind of like the building blocks, the things we're going to do build our UI we're going to use in the view, so, the stuff that's in the view is pretty generic. Generic UI elements, the stuff in the controller is very specific to how your UI works, and the stuff in the model is completely independent of how your UI works.
   * Doing MVC is about knowing where things go, but also about how to communicate between these three camps and so I'm going to try and summarize how the communication works between these camps and I've used road markings, you see the double yellow line and then the dashed white line, so that's like you're driving in your car, try to use them as that I have an image for how this communication happens, where is's allowed, where it's not allowed.
   * So let's talk about the controller talking to the model. Going from controller side of the road over to the model side is a dashed white line, in other words, you can head right across there, you probably want to look before you go, but you can go right across. The controller has to know everything about the model and it has to have complete ability to talk to the model, use its public API as much as it wants, because the controller's job is to present the model to the user using its view as its minions, so it has to have this access. So that's full, unrestricted access the controller has talking to the model. This is a one-way ero, or one way arrow, from the controller to the model.
   * And similarly from the controller to the view, is also unlimited communication because the controller is responsible for talking, using it's own minions, the view is the controllers' minions to lay out the user interface and all that stuff, so the controller can do anything it want, I've put that little green word "outlet" up there because when we have a property of a controller that points into the view, we call it an outlet.
   * What about this communicaton? Model to view, never. And why is that? 100 percent obvious. The model is completely UI independent. So there's absolutely no way it could talk to a view or object or any in that view camp. Because the view objects are fundamentally UI objects, they're kind of generic, but they're still fundamentally UI objects. Similarly, since the view objects are kind of generic, they can't be talking to any specific model. They need a controller to interpret a model for them.
   * What about the view talking back to the controller? You got these generic view objects, like buttons, can they talk to the controller? Well...yes, they can, but they have to be careful because the view objects are generic, so they can't really know much about the control, so, they can only communicate back to the controller in a blind way, where they don't know the class of the thing they're talking to, and, in a structured way, a way where we all agree, we're going to communicate this way, between the view and the controller. So what's an example of a structured way? Well one is called target action. So the controller basically drops a target on itself and then it hands out an action, which is like an arrow, to the view and says to the view. When you do what you do, like you're a button and someone touches you or you're a slider and someone moves you, send me that action. So in this way, the geeneric button, or slider, is communicating back to the controller, it has no idea that it's a card geme controller or a space geme controller, it doesn't know what kind of controller it is. All it knows is that when something happens in itself, boom! It sends messages to targets. So that's a blind, simple, strutured way for the view boom, it send messages to targets to communicate with the controller.
   * But what about more complicated ways? Sometimes the view, things are happening in the view that are somewhat complicated and the controller needs to be informed of what's going on, synchronizing what's happening. And one way to think about this is these words I put up there in the View camp, "will", "should", "did", when the view is kind of like, let's say on the scroll view and I'm scrolling around, and I want to let the controller, somebody know that the user just did scroll, or the user puts down the touch and is about to scroll, I want to let the controller know the user will be scrolling. Or the user puts a touch down and the scroll view wants to know, should I allow the user to scroll here, is that allowed? All those things, the scroll view itself might not have enough logic to know the answer to those questions, so what it does is it delegates the authority to answer those questions to some other object. Now it doesn't know the class od that object, all it know is that other object can answer these questions, will, should, did, this, that or the other thing, like, should allow scrolling, did scroll to point, things like that. So those are the kind of methods you're going to see in these delegare protocols. A protocol is just a blind way to talk to another object.
   * Also, another important thing is that views should not onw the data that they're displaying. In other words, it shouldn't be a property inside of them where that's the truth of that data. And the easiest example for this is all the songs in your iPod or your iPhone or your iPad, you might have 10,000 songs in there. So if you have some kind of generic list view in your view, you can't transfer all 10,000 songs to its instance variables and expect it to hold 10,000 songs so it can list through it. A, that would be inefficient, and B, that information, those 10,000 songs belongs where? In the model,okay? Because your song database is a model. It has nothing to do with UI's, just a list of songs and artists and albums and all that, it's in the model. Some controller has to look at that dadabase and tell a view how to display all those songs. 
   * So we need that communication to happen here and the view is displaying some sort of list, and you're touching down and you're flicking on the list and trying to see more songs, how does that communication happen, and the answer is, we have another special kind of delegete, which we call a data source. Now the data source doesn't do the will, did, should, it's going to be asking questions like count, like how many songs are there? And the controller looks in the model, 10,000. Response to the view, there's 10,000. The view makes space, internally, for 10,000 things, it doesn't know what they are, moves the scroll bar indicator a little bit, so that you know where it is, and then you start scrolling, flipping through it, and its start sending the message to the controller: give me the data at line 150, next 10 items. See what I mean？ And then you flick down some more, now it's saying 250, 10 more items, and so the controller is going back to the model and saying give me more data, and it's providing it to the view in this blind way. So data source is just a kind of delegate, it's a specific kind of delegate for getting data. So you're going to see that there are classes in iOS that have a data source, and they also have a delegare. Most sophisticated classes in iOS have a delegate, the will, did, should kind of things. Some of them have a data source, it depends on whether they're showing a lot of data or not. Now simple data, like if I had a view, if I invented a view for my card game called playing card view, and it just has a suit and a rank, we're not going to do count data at for just suit and rank, we are going to set those properties. And so the view then would have those, that data set in it, but it wouldn't be owning it. The model would still be owning the suit and rank, the view is just getting that data to present it. So simple data we might transfer to the view, but it's merely for it to display it.
   * What about this communication? Can the model talk to the controller? Again, obviously that's verboten because model knows nothing about UI, so it couldn't possibly talk to a UI like the controlle. But sometimes things change in the model and the controller needs to know about it. Data changes, a database changes or the model is some network database and somebody changes something on the network and it changes, and the controller needs to find out. So how do we do that communication? We do that using kind of a radio station model. So the model, a radio station concept, the model will use this concept to essentially broadcast information to anyone who's interested. And the mechanisms for doing this in iOS are called notification and key value observing, KVO we call it, and so the model can just say, oh, anytime something changes in my model, I'm just going broadcast on my radio station and then the controller simply tunes into that radio station. And it can find out things are changing. And when it finds out something changes, it's going to communicate via its green arrow to the model, and say, okey, give me that data that changed. So towards the end of the quarter, we'll start seeing a little how to do notification to find out, for example, if the data in the database changes, we'll get a notification, the Controller can then go talk to the model to get the info. Some people have asked, can a view tune into the radio station? They probably could, but you probably wouldn't want to do that. That would probably be a violation of MVC.
   * Well, we're essentially going to combine multiple MVC's, Because you, an MVC can use, as part of its view, another MVC, Okay? So, an entire MVC, can be one of the minions of some bigger MVC. And by doing that and cascading it down, we can build more and more complicated applications. So, an example of this is you might have your calendar app, and it's showing you the entire year, and you click on a month, and now it shows you a month view. Well a month view looks a lot different than a year view. Month view just has all the days and maybe some circle that tells you where you have an appointment on a day. And then when you click on a day, and now you get a day view. And the day is showing you the hours and what your appointments are, and you click on an appointment, and now you get an appointment view and it's showing the detail of where you're going and when it is etc. Well, each of those views, the year view, the month view, the day view, and the appointment view are their own MVC's. But you can see how the last three are used as a minion of the top-level view, the year view, to show more detail. So the year view, you click on a month, it's going to use the month view MVC to show more detail. So, you see this also in iOS with tab bar controllers. You have the tab bar, along the bottom, I have four or five things you can choose, well there's some MVC at the top who has four pointers to four minions, which are the four MVC's that are each going to appear in a tab bar.
   * So, that basically results in a picture that looks kind of like this. ![MVCs](https://raw.github.com/JeOam/jeoam.github.io/master/images/MVCs.png)Where you got this MVC and you see the purple one that's like underneath the word "togeter" there, and it points to three other MVC's outside its view thing. That's how we're going to build this, that might be a tab bar controller, and those might be the three tabs. Each one is its own little MVC, completely independent, operates on its own, doesn't even know it's a generic, reusable view like thing at this point, it doesn't even know that it's in a tab bar. Okey? It just knows that it's supposed to do whatever it does. And so it's modular in that way. You can also see that there's no communication between any other, there's no other arrows except for some of the models. You see some of the models are communicating with each other, you know, a big application might have single, shared model. Or, the models might be split off into pieces to be used by sub MVC's. But that's the only kind of communication you're going to have there, all other communication is either the structured communication we saw in the MVC or it's using MVC's as part of the view of another MVC.
   
---

###Objective-C

#####New language to learn!

* Strict superset of C
* Adds syntax for classes, methods, etc.
* A few things to “think differently” about (e.g. properties, dynamic binding)

#####Most important concept to understand today: Properties

* Usually we do not access instance variables directly in Objective-C.
* Instead, we use “properties.”
* A “property” is just the combination of a getter method and a setter method in a class.
* The getter (usually) has the name of the property (e.g. “myValue”)
* The setter’s name is “set” plus capitalized property name (e.g. “setMyValue:”)
* (To make this look nice, we always use a lowercase letter as the first letter of a * property name.) We just call the setter to store the value we want and the getter to get it. Simple.

#####￼￼This is just your first glimpse of this language!

* We’ll go much more into the details next week.
* Don’t get too freaked out by the syntax at this point.

---

###Objective-C Code Demo
In objective-C every class we have and the class I'm going to show you today is a, is in our, essentially our model that we're going to build for our card game matching app. We're going to have a card and a deck, and we're also going to have subclass of card called playing card, and a subclass of deck called playing card deck. Those are the four classes that are going to be in our model, to start.

* ".h" file is public API, and ".m" file is private API.
![code1](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-1.png)
![code2](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-2.png)
![code3](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-3.png)
* When our superclass is something that's in iOS, however, we dont' usually import just that classes header file, which in this case is "foundation", we actually import the entire framework, which is all precompiled and optimized. And in fact, in iOS7, the syntax for this is really to say "@import Foundation;"
![code44](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-4.png)
![code5](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-5.png)
![code6](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-6.png)
![code7](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-7.png)
* Objective-C does not require you to declare something before you use it in a file.
![code8](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-8.png)
![code9](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-9.png)
![code10](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-10.png)
* All objects live in the heap, not in the stack.
![code11](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-11.png)
* We can sent message to pointer `nil`.
![code12](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-12.png)
![code13](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-13.png)
![code14](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-14.png)
* `nonatomic` means you can't have two threads tring to set this property at the same time. Because the way we do multithreading in iOS is not by having a single object that muliple threads are setting on, we usually have a seperate set of objects that are running in another thread, like your model, and then other,than your UI stuff is running in the UI thread and they're talking thread to thread.
![code15](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-15.png)
![code16](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-16.png)
![code17](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-17.png)
![code18](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-18.png)
![code19](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-19.png)
![code20](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-20.png)
![code21](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-21.png)
![code22](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-22.png)
![code23](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-23.png)
![code24](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-24.png)
![code25](https://raw.github.com/JeOam/jeoam.github.io/master/images/Lecture1-code-25.png)

---

###Coming Up
#####Next Lecture

* More of our Card Game Model
* Xcode 5 Demonstration (start building our Card Game application)

#####Next Week

* Finish off our Card Game application 
* Objective-C in more detail 
* Foundation (array, dictionary, etc.) 
* And much much more!
 
---

####Lecture 1 done! 

---

