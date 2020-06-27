---
layout: post
title: P000. Finished First Version of RaspPeri Library
---

Finally I've made it! For almost 3 weeks now. I've been always struggling between the two ideas of "I'm wasting my time" and "no that will definitely be useful". Now all the efforts have paid off. Today I've managed to finish the implementation of I2C. Once I've seen the string "hello world, hello i2c." shown both on Raspberry Pi and Arduino Serial Monitor, I know immediately it is the time for a small celebration.

![post-image]({{ "/assets/img/2020-06-11-i2c-example-output.png" | absolute_url }})

Currently, the library is supporting the very basic functionalities of GPIO, I2C and SPI. I decided to postpone PWM part a little bit. Since I will definitely use a PWM extension shield which has an I2C interface. So using Raspberry Pi for direct PWM is not necessary.

After finished the final refactoring of the library, I was starting to think about whether I should announce this library in the Raspberry Pi community or not, but soon I've figured out that it is probably not the best time to do so. For the potential users, this library is still far from feature rich. For myself, I want to continue working on my drone project. To announce it now means nothing to me except a huge workload. Maybe I can announce it after I've finished my drone project.

![post-image]({{ "/assets/img/2020-06-11-spi-wiring.png" | absolute_url }}) 

![post-image]({{ "/assets/img/2020-06-11-i2c-wiring.png" | absolute_url }})

The next step of the drone project is coming naturally. What I need to do is to write the hardware driver for all of the different sensors. The first hardware candidate is definitely GY-521 aka MPU6050, followed by nRF24l01, BME280, GY-91 aka MPU9250, PWM extension shield, and probably also the GPS module.

I was also scouting for a reliable and cheap online PCB printing service. The people in the DIY club that I've joined have helped me a lot, they have provided some very useful information. So I guess I have to start learning how to design PCB board now.
