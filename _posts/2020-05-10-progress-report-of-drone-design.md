---
layout: post
title: P000. Progress Report of Drone Design
---
As a coder, I really feel that once something comes into the real world, it becomes much more complex than I can handle. Because the reality is more complex than the tiny virtual world in the computer, and it is usually unpredictable, and also has a lot of constraints. The drone design is one of the examples to prove it. Now I'm getting deeper into the project, and I've noticed that previously I was used to find solutions for a problem in the IT world, and now I'm getting used to make compromises when I hit a problem.

After having watched several drone assembly tutorials and videos, I roughly had the feeling about which components does a drone have:
* Frame
* Main controller
* Barometer
* Accelerometer
* GPS unit
* Brushless motors 4x
* Electronic speed controller (ESC) 4x
* Power distribution board (PDB)
* Battery
* FPV camera
* Video transmitter (VTX)
* Radio control receiver (RX)
* On-screen display unit (OSD) (optional)

To control the drone, I also need:
* Video receiver (VRX)
* Radio control transmitter (TX)
* Gamepad or some kind of controller

The sensors and controller is not a big problem, because I've already learnt how to deal with them from my previous tiny DIY projects. I think the most difficult part will be data processing and transmission. I've made a data transmission diagram to help me understand the situation.

![post-image]({{ "/assets/img/2020-05-10-data-transmission.png" | absolute_url }})

The control data transmission is relatively simple and straight forward. It is just really hard to choose the right chip for it. It is the nRF24l01 that comes first into my sight. It seems that this chip with correct antenna can reach around 1000m transmission range. I've also heard about some good things about LoRa, people say that it could reach over 1km and sometimes even 5km transmission range. That sounds very attractive. However, after googled for a while, I haven't found any cheap, reliable and simple solutions like nRF24l01. So I decided to firstly start with nRF24l01, and make the design and the code modularized, so that I can change this part easily in the future.

The video data transmission is not hard. There are a lot of existing video transmitter and receiver systems sold at a very reasonable price online. Once been attached to the computer, it could be treat as an external USB camera. That's very convenient for me. Since I'm not a FPV guy, so I don't need goggles or low latency video transmission. Monitoring it on my laptop would be already enough. Besides, this solution also provides me the possibility to do some fancy stuff later with the transmitted video data, for example, autopilot based on the graphical data and so on.

The biggest problem here is actually the sensor data. For autopiloting based on GPS data, or for PID tuning reason, I need to read and store the sensor data sent from the drone while flying. At first I thought the nRF24l01 is a full-duplex communication system, but actually it is only half-duplex. This means while receiving the control data, the drone is not able to send the sensor data back. Theoretically, I can alternate the sending and receiving phases, if one single phase is short enough, I can implement a "pseudo full-duplex" communication based on half-duplex. But to be honest, I have no idea whether one single phase can be that short, so that I cannot feel any obvious latency.

And then I came up with another idea. Since I am sending the video data back, why not simply hijack the video transmission, and let it do something for me? I thought about OSD at first, because from the OSD, the pilot is able to read all kinds of sensor data. However the OSD data are integrated into the transmitted video, and it is only for humanbeings to read. It is relatively hard to extract machine readable data from it. There are also protocols like SmartAudio or IRC Tramp, but they are rather protocols between flight controller and the VTX, not the protocol between VTX and VRX. The information transmitted between VTX and VRX is still encoded by OSD by integrating the information into the transmitted video in a human readable form.

After researched for a whole day, another idea came to my mind. I could use a more powerful chip as the main controller of the drone, like a Raspberry PI Zero or Pocket Beagle. The FPV camera will send video data to the chip, and then the chip will process the video data in the real time, add a colorful strip at the left side of the video with each colored patch carrying 3 sensor values (represented with RGB), and send it through VTX. At the VRX side, what I need to do is to cut the strip off from the video, decode the data and then display them in a human readable way. Although this idea sounds quite interesting, I'm not sure whether the analog video transmitting quality will be enough for it, and I'm also not sure whether it is a good idea to use them for stablizing the drone in real time situations. Besides, this kind of chips are usually quite power thirsty.

Or... As an alternative to all the possibilities above. I could simply add another dedicated nRF24l01 chip for sending sensor data back from the drone. If it is using different channel other than the chip which is receiving the control signal, it will probably be fine. And it is not adding too much weight to the drone, it is not power thirsty like RPI or Pocket Beagle, and it is also cheap. Although adding another data transmission system sounds like a waste, but at the moment, it is the best possible solution.

Besides the data transmission, the other details seem to be quite straight forward. So currently, my plan looks like this:
* Frame: TBD.
* Main controller: Arduino Nano (if it doesn't work, use ESP32 instead)
* Barometer: BMP180
* Accelerometer: MPU6050 (if it doesn't work, use MPU 9250 instead)
* GPS unit: NEO-6M
* Brushless motors 4x: TBD.
* Electronic speed controller (ESC) 4x: TBD.
* Power distribution board (PDB): TBD.
* Battery: TBD.
* FPV camera: TBD.
* Video transmitter (VTX): Eachine TX805
* Video receiver (VRX): Eachine ROTG01
* Radio control receiver (RX): nRF24L01+ PA LNA
* Radio control transmitter (TX): nRF24L01+ PA LNA
* On-screen display unit (OSD) (optional): 
* Gamepad: any thing that works
