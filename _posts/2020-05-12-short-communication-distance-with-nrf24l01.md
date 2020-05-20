---
layout: post
title: P000. Short Communication Distance with nRF24L01
---
According to my plan, nRF24L01 will be the solution for the control data and sensor data transmission. And today, I've received my nRF24L01 chips with antenna. After some test, I've found that the communication distance is quite worrisome.

![post-image]({{ "/assets/img/2020-05-12-nrf24l01-and-arduino.png" | absolute_url }})

The wiring is quite simple and straight forward. Within several minutes, I was able to wire up the chip with Arduino Uno and Arduino Nano. I couldn't wait longer for testing them. So I just copied and pasted the program from the example and run them immediately after that without even looking into a single line of the source code. And in several seconds, I saw the message sent by the Arduino Uno received by the Arduino Nano.

Nice! That's a good beginning. But it is just a beginning. After supper, I decided to do a range test, to see if the transmission range is really reaching the claimed 1100 meters or not. So I left one nRF24L01 at home, and bring the other one with me. After I've walked out around 50 meter, the link is broken. That's very disappointing. It is not even something close to 1100 meters.

I asked google for the answer after that. According to some other examples and the documentation of nRF24L01, I have to set the transmission power to max, and set the data rate to the lowest. Done! And with hope, I've tested once again. This time it is a little bit longer, but still 70 meter, that's it.

To me the worst thing is not that there is a problem, but there is a problem, and you don't know what has caused the problem. Is it because of the buildings in between? Or my configuration? Or the chip is broken? Or some other problems that I've never thought before? I have no chance to know.

But the project must go on. I've taken the adivce from one of my friend. I'll keep the chips for the first iteration, and use them for the communication. In this way the project won't be blocked by the problem that I'm currently facing. It is a possibility that the short communication distance is because of the buildings between the transmitter and the receiver. Later I'll bring it to the open area. If I can get longer communication distance from it, then I'm lucky. Otherwise, I'll try to find another more reliable solution, so that the nRF24L01 can be replaced.

Another thing which bugs me a lot before was how many antennas do I need to implement the duplex communication channel. To try this out, I've written a simple and stupid communication protocol. The client will send the message to the server, and after the server has received the message, it will send something back as an acknowledgement. Later the server will be the drone, and the client will be the controller. The goal is to get as much ping-pongs as possible between the client and the server within 1 second. And the following part was the best result:

```text
21:49:48.987 -> data received: Pong 758
21:49:49.055 -> data sent: Ping 759
21:49:49.055 -> data received: Pong 759
21:49:49.123 -> data sent: Ping 760
21:49:49.123 -> data received: Pong 760
21:49:49.190 -> data sent: Ping 761
21:49:49.190 -> data received: Pong 761
21:49:49.224 -> data sent: Ping 762
21:49:49.224 -> data received: Pong 762
21:49:49.291 -> data sent: Ping 763
21:49:49.291 -> data received: Pong 763
21:49:49.357 -> data sent: Ping 764
21:49:49.357 -> data received: Pong 764
21:49:49.425 -> data sent: Ping 765
21:49:49.425 -> data received: Pong 765
21:49:49.495 -> data sent: Ping 766
21:49:49.495 -> data received: Pong 766
21:49:49.529 -> data sent: Ping 767
21:49:49.529 -> data received: Pong 767
21:49:49.598 -> data sent: Ping 768
21:49:49.598 -> data received: Pong 768
21:49:49.666 -> data sent: Ping 769
21:49:49.666 -> data received: Pong 769
21:49:49.736 -> data sent: Ping 770
21:49:49.736 -> data received: Pong 770
21:49:49.770 -> data sent: Ping 771
21:49:49.770 -> data received: Pong 771
21:49:49.837 -> data sent: Ping 772
21:49:49.837 -> data received: Pong 772
21:49:49.904 -> data sent: Ping 773
21:49:49.904 -> data received: Pong 773
21:49:49.970 -> data sent: Ping 774
21:49:49.970 -> data received: Pong 774
21:49:50.038 -> data sent: Ping 775
```

In one second, the client and the server has managed to do the ping-pong for 16 times. I guess for flying the FPV, this data rate will probably kill the experience. And I guess this rate will becomes even lower once I'm starting to add more and more codes for the sensors and for the flight control. Because each operations to read the sensor and do the math calculation will take time.

Now I'm starting to worry about using Arduino as the main control chip. I probably should try some more powerful solutions out for the brain of the drone. After having watched some great videos from [Joop Brokking](https://www.youtube.com/channel/UCpJ5uKSLxP84TXQtwiRNm1g), I've decided to use a more powerful board directly, instead of staying with Arduino.
