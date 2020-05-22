---
layout: post
title: P002. Current Progress on Solder Smoke Absorber Project
---
Some people were talking about harmful solder smoke in the Telegram channel of a DIY club that I've joined. While reading the discussion, I've decided to get myself a solder smoke absorber. Immediately after I've announced it, someone in the channel asked me why even bother buying one, because it is simply a fan with a carbon fiber sponge. Indeed, I probably should build one instead of buying it.

As the club member said, I need a fan and a piece of carbon fiber sponge. Other than that, I also need a frame where I can mount the fan and the sponge, and some kind of power supply for the fan. I've got a fan from one of my colleague. He has an extra old CPU fan not used for years. After I've got the fan, I started to test it immediately. According to the information online, the power supply should be 12V. So I attached it to the DC power, and the fan started to spin smoothly and quitely.

![post-image]({{ "/assets/img/2020-05-20-fan-with-dc-power.png" | absolute_url }})

Some other information says that the fan is PWM controlled. I'm not sure whether I could get higher RPM by sending PWM signal to it. So I've used an Arduino nano to generate the PWM signal. And any PWM signal will only making it spinning slower, because per default, the fan will spin at the highest speed.

![post-image]({{ "/assets/img/2020-05-20-fan-with-an-arduino.png" | absolute_url }})

For the power supply, I'm considering using USB. However, USB usually only provides 5V DC power, but what I need is 12V DC. So I've purchased an extra step up device to convert 5V DC from USB to 12V DC.

Regarding the frame for mounting the fan, I'd like to use some object that I could find in the daily life. Thus I went to the supermarkt and bought almost everything that I can find with a solid plastic case or a metal can which roughly fit the size of the fan. Soon, I've found that the steel can for the soup is the best fit. With some soft pad, I'm able to mount the fan onto the tin can solidly. While spinning, the fan will create a low presure area inside the can, which will absorb the solder smoke. If I mount the sponge at the other side of the can, the solder smoke will be filtered by the carbon fiber sponge.

![post-image]({{ "/assets/img/2020-05-20-fan-in-a-can.png" | absolute_url }})

The last thing that I need to take care of is the carbon fiber sponge. I've searched for it on several different online-shops. The sponge for absorbing the solder smoke are either extremely expensive, or will be delivered in a month. As an alternative, I've bought several pieces of sponge for cat litter box, which is also made of carbon fiber. All I can do is hoping it will also filter out the solder smoke effectively.

Now I'm waiting for the delivery. I'm quite sure that this project will be finished soon. The only problem I see now is that I have to solder the power cable from the USB voltage step-up device to the fan. But while doing that, I won't have the solder smoke absorber.
