---
layout: post
title: P000. CMake and vcpkg
---
Several years ago, people are complaining about the standard library in C++ is not complete. And then there comes a pile of C++ standards, which have improved this situation a lot, and make C++ now a modern programming language. And thanks to CMake, which has built an consistent abstract layer above those messy building toolchains. However, there is still one huge problem which prevents C++ become more popular. That is the dependency management tool.

In any other programming languages, the project management tool usually plays one of the most important roles in the eco-system. For Java, we have Maven and Gradle; for JavaScript, we have NPM; for Python, we have pip; for Ruby, we have bundler; for C#, we have nuget. But, what do we have for C++? Well, we have apt, yum, pacman, ... Ok, but they are usually only for one of the distributions of one of the platforms. And we have Conan, vcpkg and Build2.

Build2 seems to be the most promising one. But it is very fresh, and only contains 60 packages, even without Boost. So it is definitely out of my choice. Conan, probably it is powerful, but somehow I don't have mood to read through their documentations. I'm a lonewolf hobby C++ coder, not a professional C++ guru. I need something straight forward, easy to use, and can fit into my computer where Windows system runs on it.

It seems that I only have one choice left now. Vcpkg.

It is very easy to learn and easy to use. After having spent 15 minutes reading their documentation and trying out, I've already got the idea how to use it. And its repo contains more than 600 libraries, far more than Conan which only has not more than 300 libraries. And after I've done the integrate install, the stupid Intellisense in the VSCode is even stopping complaining about the missing header files. Everything look so magically harmonized.

Usually I'm not a fan of Microsoft products. However recently, Microsoft has made a lot of decissions to make their technology more transparent, free and community driven. I personally see this as a huge public relationship project. It seems that Microsoft has done really well these years. And I'm eager to see that with the help of vcpkg, the eco-system of C++ will become better.
