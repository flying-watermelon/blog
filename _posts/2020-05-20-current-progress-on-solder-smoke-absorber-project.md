---
layout: post
title: P002. Current Progress on Solder Smoke Absorber Project
---
Some people were talking about the harmful solder smoke in the channel of a DIY club. While reading the discussion, I've decided to get myslef a solder smoke absorber. Immediately after I've announced it, one of the people said something like why bother buying one, because it is simply a fan with a carbon fiber sponge. And, true, I probably can build one instead of buying it.

As the one in the channel says, I need a fan and a piece of carbon fiber sponge. Other than those, I also need a frame where I can mount the fan and the sponge. I've got a fan from one of my colleague. He has an old CPU fan that he won't use anymore. After I've got the fan, I started to test it directly. According to the information online, the power supply should be 12V. So I attached it to the DC power, and the fan started to spin.

![post-image]({{ "/assets/img/2020-05-20-fan-with-dc-power.png" | absolute_url }})

Some other information says that the fan is PWM controlled. I'm not sure whether I could get higher RPM by sending PWM signal to it. So I've used an Arduino nano to generate the PWM signal. And PWM signal is only making it spinning slower, because per default, the fan will spin at the highest speed.

![post-image]({{ "/assets/img/2020-05-20-fan-with-an-arduino.png" | absolute_url }})

A problem created by the fan is the power supply. USB usually only provides 5V DC power, but what I need is 12V DC. So I've purchased an extra step up device to convert 5V DC from USB to 12V DC.

Then the problem is a frame for mounting the fan. For that, I'd like to use some object that I could find in the daily life. Thus I went to the supermarkt and bought some stuff with a solid plastic case or a metal can. Soon, I've found that the steel or tin can for the soup is the best fit. With some soft pad, I'll be able to mount the fan onto the tin can. While spinning, the fan will create a low presure area inside the can. If I then mount the sponge at the other side of the can, it will absorb the solder smoke.

![post-image]({{ "/assets/img/2020-05-20-fan-in-a-can.png" | absolute_url }})

The last part of the absorber is the sponge. I've searched it on several different online-shops. The sponge for absorbing the solder smoke are either extremely expensive, or will be delivered in a month. As an alternative, I've bought several pieces of sponge for cat litter box. I hope this will work with the fan and the frame.

Now I'm waiting for the delivery. After that I can continue my work. I'm confident that this project will be finished soon. The only problem I see now is that I have to solder the power cable from the USB voltage step-up device to the fan. But for this time, I won't have the solder smoke absorber.
