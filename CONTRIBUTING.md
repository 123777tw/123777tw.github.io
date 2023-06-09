# 为了让更多人获得更多自由，作为贡献者您可能需要牺牲自己的部分自由。<br/>In order for more people to gain more freedom, as a contributor, you may need to sacrifice some of your own freedom.

为了简单实现某个功能，您可以使用多种不同的方式或风格迥异的代码。当您开始思考什么样的代码可以被更广泛的环境运行时，您正在和我们思考一样的东西。下面是我们针对这个仓库总结出的一些经验，它们可能不全面，甚至会有些许纰漏，但我们仍然希望可以帮到您。

To simply implement a certain function, you can use various different methods and styles of code. When you start thinking about what kind of code can be run in a wider environment, you are thinking about the same thing as us. Below are some of the experiences we have summarized for this warehouse, which may not be comprehensive or even have some flaws, but we still hope to be helpful to you.

## 在保证最新版本兼容的前提下，使用尽可能旧的语法。<br/>Use the oldest possible syntax while ensuring compatibility with the latest version.

Chromium是一个著名的浏览器开发项目，它在版本50放弃了对Windows XP的支持。如果您的代码基于ECMAScript 5标准编写，则它们有可能在某台装载了Windows XP和Chromium 49的电脑上正确运行。如果某些功能确实不能使用旧语法，请尽量将它们模块化，即使它们不被支持也不会影响其他功能。

Chromium is a famous browser development project. It abandoned support for Windows XP in version 50. If your code is written based on the ECMAScript 5 standard, it is possible that they will run correctly on a computer loaded with Windows XP and Chromium 49. If certain functions cannot use the old syntax, please try to modularize them as much as possible, so that even if they are not supported, they will not affect other functions.

## 使用尽可能少的方法实现尽可能多的功能。<br/>Use as few methods as possible to achieve as many functions as possible.

即使Chromium如此著名，但仍然有部分设备不会装载Chromium浏览器，目前一个典型的例子就是iPhone™。你会发现一些函数在Chromium中工作正常，但在Safari中不被支持。我们不能简单地找出所有同时支持Chromium和Safari的函数来编码，因为仍然有数不胜数的其他浏览器，以及各自数不胜数的版本，而且它们可能会随着时间的推移消失或出现。我们能做到的，就是尽可能使用统一的风格、少的类或函数、以及代码依赖。

Even though Chromium is so famous, there are still some devices that do not load the Chromium browser, and a typical example currently is iPhone™. You will find that some functions work properly in Chromium, but are not supported in Safari. We cannot simply find all the functions that support both Chromium and Safari to encode, as there are still countless other browsers and their respective versions that may disappear or appear over time. What we can do is to use a unified style, fewer classes or functions, and code dependencies as much as possible.

在这里我要特别指出一个不好的案例：JQuery。我们暂时抛开它本身的目的。它有一个好的初衷，是希望与更多的浏览器相互支持。但可惜的是，它使用完全不同的理念，使用类似“盘查”的方式将各种情况迭代到自己的代码逻辑中，使自己本身看起来非常臃肿。这在代码仍需要人类维护的现在，会造成不小的困扰。

I would like to point out a bad case here: JQuery. We temporarily set aside its own purpose. It has a good intention of supporting each other with more browsers. Unfortunately, it uses a completely different philosophy and uses a similar "inventory" approach to iterate various situations into its own code logic, making itself look very bloated. This can cause significant troubles in today's world where code still requires human maintenance.

我们希望我们的代码被尽可能多的设备执行，但不代表我们的代码必须一味地向所有不同的设别“妥协”。一些设备不能执行我们的代码，这很遗憾，但犯错的可能是设备本身，不是我们的代码:}

We hope that our code will be executed by as many devices as possible, but this does not mean that our code must blindly "compromise" with all different devices. Some devices cannot execute our code, which is regrettable, but the error may have been made by the device itself, not our code:}
