---
layout: post
title: P000. Progress Report of Raspberry Pi Peripheral Driver
---

There is an old saying, "don't reinvent the wheel". Well, to some extent, what I'm currently trying to do, building a peripheral driver for Raspberry Pi 4B, is somehow violating one of the important golden rules in the software development.

What the heck am I doing? This is probably the question that I have asked myself the most these days. Actually, there is already a good library available, which is called BCM2835. It is written in C, supporting Raspberry Pi 4B, and very well structured and well documented. The thing that I'm not satisfied with BCM2835 are all minor details. However there is a strange motivation which is driving me to build a completely new peripheral driver library, which is basically reimplementing BCM2835 in C++ language.

Now the work-in-progress version of the library can be found in the [GitHub repo](https://github.com/flying-watermelon/rasp-peri), which only have basic GPIO and SPI implemented. It is definite not that feature rich yet, but I've already decided to push it to the end.

But still, I'm trying to avoid the question. What the heck am I doing?

I guess I'm mostly trying to write such codes, that even without any comments, one should be able to roughly understand what is going on there. So I was caring about the cleaness of the code a lot. I'm also trying to utilize the advanced language features of C++, thus the interface between the user and the library should stay clean and clear. In the meanwhile, I'm also trying to keep the high performance of the library. Besides, the library will be header-only, which means there is almost zero overhead if one wants to include it in another project.

And most important, with this project, not I'm getting into the world of hardware programing. This area was completely new to me before. It is really a challenging work, because most of the time, you don't really have an easy way to help you to debug a problem. In most of the cases, I'm just trying to do things very carefully, and always tripple check everything. However, there are still a lot of strange problems coming up. For example, after I've implemented SPI, I've spent 2 days trying to figure out why it is not working. I was going to give up, and ask people online why I don't receive anything after I've sent the messages. However, once I've re-written everything for providing a minimal program which can reproduce the problem, I found that it is magically working. Finally, lesson learnt. If I prefix an integer value with "0", it is going to be a octal number. I don't know why I have the feeling that it should be binary, but binary is actually prefixed with "0b".

Finally, once I see the correct value is received, I cannot say I'm super happy, and I was definitely not sad. It just ... feels normal, as if it should be like this.

![post-image]({{ "/assets/img/2020-06-08-spi-example-output.png" | absolute_url }})

And I clearly know that, doing this is actually taking a huge detour in the drone project. But anyway, since this project is already becoming a marathon run, it doesn't matter if I add several hundred meters to it, right?
