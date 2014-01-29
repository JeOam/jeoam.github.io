---
layout: post
title:  斯坦福 iOS7 公开课第一课：Class Logistics, Overview of iOS, MVC, Objective-C
---

这是 Stanford CS193p: Developing iOS 7 Apps for iPhone and iPad Fall 2013-14 文字版，按照视频字幕手工编辑完成。

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
   * MVC is essentially a strategy for how to organize all the classes in your application. And what we do fundamentally is we divide all the classes into one of there camps:

![images-MVC](https://raw.github.com/JeOam/jeoam.github.io/master/images/MVC.png)

更新中....
---

