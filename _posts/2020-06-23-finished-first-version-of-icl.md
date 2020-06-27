---
layout: post
title: P000. Finished First Version of ICL
---

As usual, after I've finished the rasp-peri, the peripheral library for Raspberry Pi 4, I was starting my useless thinking about some potential problems that probably don't even exist for me. That is, what if I need to use this library for Raspberry Pi Zero? And what if I need to port this library to another totally different hardware platform?

For using this library on Raspberry Pi Zero, I can probably change the macros to match Raspberry Pi Zero, because most differences between Raspberry Pi 4 and Raspberry Pi Zero are the register addresses, and the operating processes are mostly the same. However for a totally different hardware platform, not only the register addresses, but also the operating processes are different now. If I write a lot of sensor drivers based on rasp-peri library, the chance to port these drivers to another hardware platform is close to 0.

The [i2cdev library](https://github.com/jrowberg/i2cdevlib) has inspired me. This library has created an abstract interface for I2C, and different hardware platforms are implementing this interface, and the sensor drivers are using this interface. If we want to port the sensor drivers to another hardware platform, we just need to compile them with another interface implementation. However, this library contains only interface for I2C, for the antenna communication, I also need SPI. So why not re-write the rasp-peri library following the design of i2cdev then?

For the new library, I have set following goals for myself:
1. it should be written in C, because C is supported by most of the hardware platforms, and it can be easily called by other languages.
1. it should provide a unified interface for SPI and I2C.
1. different hardware platform only need to reimplement SPI and I2C interface, and the existing sensor driver implementations should work out of the box.

Since I have already worked on rasp-peri library, make the interface is very simple. By referencing the source code of BCM2835 library, and porting the rasp-peri code, the Raspberry Pi 4 implementation of the interface is also finished in a short time.

The tests also goes very well. But the most exciting news is, I've used the interface with Raspberry Pi 4 library to write the most simplest sensor driver for MPU6050, and it is very successful!

![post-image]({{ "/assets/img/2020-06-23-raspberry-pi-mpu6050-wiring.png" | absolute_url }})

The way I'm testing the sensor driver is simply writing to the sensor that I want to read the register 0x75, which is the so called "who am I" register. This register contains the I2C address that this sensor is connected to. After the program is compiled with the Raspberry Pi 4 implementation of the interface and executed, the result shows exactly the I2C address of the sensor.

![post-image]({{ "/assets/img/2020-06-23-mpu6050-whoami.png" | absolute_url }})
