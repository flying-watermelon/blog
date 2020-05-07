---
layout: post
title: P001. First Post About Drone Project
---
Although named "first post", this post is already too late for recording the whole process of the drone project now. I've been working on this project for several weeks now. It has made a lot of fun.

This project all starts with the word "PID", a method in control theory that is often used for drone control. I don't know why, but the moment when I heard about this word, I just felt very curious about the theory behind it. So I googled it, learnt it and even wrote a simulation program to see how it actually works.

The physics simulation goes quite well. However, I didn't feel that I'm satisfied. I believe that I can do far more than that, and actually Im eager to do more. So I extended the simulation program, implemented a PID controller to stabilize a virtual drone in the simulation program. It works very well indeed.

![Drone Simulator]({{ "/assets/img/2020-05-07-drone-simulator" | absolute_url }})

Since the drone is already flying in the virtual world now. There is no excuse anymore not to bring it into the reality. But the problem is, I haven't ever touched a drone before, actually I even haven't seen someone flying a drone closely. It is very hard for me to imagine what do people do to control a drone. It is some YouTube videos that helped me out. For example the [DJI Tutorial](https://www.youtube.com/watch?v=QwMFK9J462A) and [a wonderful tutorial series by Joshua Bardwell](https://www.youtube.com/watch?v=391D5dX7LKg) for the FPV flying style.

Currently, my plan about this project is clear. I'd like to try my best to build a selfmade drone with an Arduino, instead of using any existing flight controller chip. If I had a chance, I'll design the carbon fiber frame by myself. And if I can manage to finish that, I'd like to make the whole project open-source, so that everyone can easily make his/her own modified copy from it.

At the moment, I've already finished porting some source code from python to C for Arduino. Next step I'll try to build the radio controller for Arduino, and then connect them to the simulation program. And then I'll be able to control the virtual drone in the simulation program. After that, I'll purchase some parts to build the physical drone.
