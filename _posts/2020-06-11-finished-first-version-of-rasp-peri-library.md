---
layout: post
title: P000. Finished First Version of RaspPeri Library
---

Finally I've made it. For almost one month now. I've been always struggling between the two ideas of "am I wasting my time" and "no that will definitely be useful". Now all the efforts have paid off. Today I've managed to finish the implementation of I2C. Once I've seen the string "hello world, hello i2c." shown both on Raspberry Pi and Arduino Serial Monitor, I know immediately it is the time for a small celebration.

![post-image]({{ "/assets/img/2020-06-11-i2c-example-output.png" | absolute_url }})

After some minor refactoring, I was starting to think about whether I should announce this library in the Raspberry Pi forum or so, but soon I've figured out that it is probably not the best time to do so. For the potential users, this library is still far from feature rich. For myself, I want to continue working on my drone project. To announce it now means nothing to me except a huge workload. Maybe I can announce it after I've finished my drone project.

![post-image]({{ "/assets/img/2020-06-11-spi-wiring.png" | absolute_url }})

![post-image]({{ "/assets/img/2020-06-11-i2c-wiring.png" | absolute_url }})

The next step of the drone project is quite clear now. What I need to do is to write the hardware driver for all of the different sensors. The first hardware candidate is definitely GY-521 aka MPU6050, followed by nRF24l01, BME280, GY-91 aka MPU9250, PWM extension shield, and probably also GPS module.

I was also scouting for a reliable and cheap online PCB printing service. The people in the DIY club that I've joined have helped me a lot, they have provided a lot of useful information. So I guess I have to start learning how to design PCB board now.
