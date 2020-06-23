---
layout: default
title: Projects
---
### Finished Project
#### P002. Solder Smoke Absorber
It is said that the soldering smoke is very harmful to one's health. People usually recommend something like 493 solder smoke absorber. But if you take a closer look into the solder smoke absorber, you will find it is quite simple, a frame, a fan and a carbon fiber sponge and that's it. So instead of spending more than 30 Euro or even 40 Euro to buy one online, I decided to build one for myself.

I've finished the project on May 21st, 2020. Although it is not very efficient, it is able to reduce the smell of the solder smoke a lot. In the future I'll probably make a version 2.0, with a more powerful fan to improve the performance.

### On-going Project

#### P000. Open-source Drone
In this project I'll try to build a drone with Arduino, carbon fiber board and other necessary components. After that I'll publish all related source code, 2D/3D-models and documentations, so that other people can easily build a copy.

#### P001. Camping Van
I'd like to convert a transporter to a simple camping van for weekend travelling. It will act as a moving tent, and I hope it can help me save some money for booking the hotel room. It won't be over complex. After convertion, it should be still able to used for daily affairs like shopping or commute in a rainy day, and so on.

#### P003. Inter-Chip communication Library
Even for the same sensor, if we are using it on different hardware platforms (e.g. different micro-controllers or micro-computers), one should also use different sensor drivers for it, because each hardware platforms have their own ways to deal with the inter-chip communication protocols like I2C and SPI. However, it is a waste of time, because people is implementing the same logic to communicate with the sensor again and again on different hardware platforms.

After having read the repository of [i2cdevlib](https://github.com/jrowberg/i2cdevlib), I've decided to make an interface between the hardware platform specific implementation, and the sensor specific implementation. In this case, they can change separately. If we want to port a sensor driver to another micro-controller or micro-computer, we only need to change the hardware platform specific implementation, and no need to touch the sensor communication part, which I think will save a lot of time for myself. 

### Planned Project
