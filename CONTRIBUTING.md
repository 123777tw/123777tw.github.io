# 为了让更多人获得更多自由，作为贡献者您可能需要牺牲自己的部分自由。<br/>In order for more people to gain more freedom, as a contributor, you may need to sacrifice some of your own freedom.

为了简单实现某个功能，您可以使用多种不同的方式或风格迥异的代码。当您开始思考什么样的代码可以被更广泛的环境运行时，您正在和我们思考一样的东西。下面是我们针对这个仓库总结出的一些经验，它们可能不全面，甚至会有些许纰漏，但我们仍然希望可以帮到您。

To simply implement a certain function, you can use various different methods and styles of code. When you start thinking about what kind of code can be run in a wider environment, you are thinking about the same thing as us. Below are some of the experiences we have summarized for this repository, which may not be comprehensive or even have some flaws, but we still hope to be helpful to you.

## 在保证最新版本兼容的前提下，使用尽可能旧的语法。<br/>Use the oldest possible syntax while ensuring compatibility with the latest version.

Chromium是一个著名的浏览器开发项目，它在版本50放弃了对Windows XP的支持。如果您的代码基于ECMAScript 5标准编写，则它们有可能在某台装载了Windows XP和Chromium 49的电脑上正确运行。如果某些功能确实不能使用旧语法，请尽量将它们模块化，即使它们不被支持也不会影响其他功能。

Chromium is a famous browser development project. It abandoned support for Windows XP in version 50. If your code is written based on the ECMAScript 5 standard, it is possible that they will run correctly on a computer loaded with Windows XP and Chromium 49. If certain functions cannot use the old syntax, please try to modularize them as much as possible, so that even if they are not supported, they will not affect other functions.

## 使用尽可能少的约束来实现功能。 Use as few constraints as possible to achieve functionality.

全球的开发者在持续数年的“浏览器大战”中积累了大量的经验，也产生了较多约定俗成的限制。我们在开发自己的网页程序时，可以针对当下的这些限制优化我们的代码逻辑加以规避。例如纯粹的本地功能应尽量脱离http或https协议的依赖，使它们在file协议或者content协议下依然可以正常工作。再具体一点，您不应该在纯粹的本地应用中使用XMLHttpRequest类。

Developers all over the world have accumulated a lot of experience in the "Browser wars" that has lasted for several years, and there are also many conventional restrictions. When developing our own web program, we can optimize our code logic to avoid these current limitations. For example, pure local functions should be as independent of the HTTP or HTTPS schema as possible, so that they can still work properly under the FILE or CONTENT schema. More specifically, you should not use the XMLHttpRequest class in purely local applications.

## 只做一件事，做好一件事。 Do one thing and do it well.

这曾经是20世纪著名操作系统Unix的核心理念，如今它已跟随Unix日薄西山。这看起来似乎是过时的理念，其实不然。Unix并非被它的理念单方面打败，Unix失败的原因是多元的，但它的理念非常适合我们的现在的仓库。我们的仓库与Unix之间有很多不同，例如使用我们的仓库不需要支付任何费用。当我们想要做第二件事情时，开始写第二个应用。这样做的一个好处是，所见即全部——使用浏览器直接保存网页就可以下载全部必要代码；而另一个好处则是，以最小单元最大化兼容性——当其中一个应用无法执行时，不影响其他可能兼容的应用。虽然多个应用之间的相互耦合不被建议，但在特定的情况下也是可以接受的。

This was once the core concept of the famous operating system Unix in the 20th century, but now it has followed the decline of Unix. This may seem like an outdated concept, but it's actually not. Unix is not defeated unilaterally by its philosophy. The reasons for Unix's failure are diverse, but its philosophy is very suitable for our current repository. There are many differences between our repository and Unix, such as using our repository without paying any fees. When we want to do the second thing, start writing the second application. One of the advantages of doing this is that what you see is everything - you can download all the necessary code by saving the webpage directly using a browser; Another advantage is to maximize compatibility with the smallest unit - when one application cannot be executed, it does not affect other potentially compatible applications. Although coupling between multiple applications is not recommended, it is also acceptable in specific situations.

## 使用尽可能少的方法实现尽可能多的功能。<br/>Use as few methods as possible to achieve as many functions as possible.

即使Chromium如此著名，但仍然有部分设备不会装载Chromium浏览器，目前一个典型的例子就是iPhone™。您会发现一些函数在Chromium中工作正常，但在Safari中不被支持。我们不能简单地找出所有同时支持Chromium和Safari的函数来编码，因为仍然有数不胜数的其他浏览器，以及各自数不胜数的版本，而且它们可能会随着时间的推移消失或出现。我们能做到的，就是尽可能使用统一的风格，加上尽可能少的函数、类、以及代码依赖。

Even though Chromium is so famous, there are still some devices that do not load the Chromium browser, and a typical example currently is iPhone™. You will find that some functions work properly in Chromium, but are not supported in Safari. We cannot simply find all the functions that support both Chromium and Safari to encode, as there are still countless other browsers and their respective versions that may disappear or appear over time. What we can do is to use a unified style as much as possible, with as few functions, classes, and code dependencies as possible.

在这里我要特别指出一个不好的案例：JQuery。我们暂时抛开它本身的目的。它有一个好的初衷，是希望与更多的浏览器相互支持。但可惜的是，它使用完全不同的理念，使用类似“盘查”的方式将各种情况迭代到自己的代码逻辑中，使自己本身看起来非常臃肿。这在代码仍需要人类维护的现在，会造成不小的困扰。

I would like to point out a bad case here: JQuery. We temporarily set aside its own purpose. It has a good intention of supporting each other with more browsers. Unfortunately, it uses a completely different philosophy and uses a similar "inventory" approach to iterate various situations into its own code logic, making itself look very bloated. This can cause significant troubles in today's world where code still requires human maintenance.

我们希望我们的代码被尽可能多的设备执行，但不代表我们的代码必须一味地向所有不同的设别“妥协”。一些设备不能执行我们的代码，这很遗憾，但犯错的可能是设备本身，不是我们的代码:}

We hope that our code will be executed by as many devices as possible, but this does not mean that our code must blindly "compromise" with all different devices. Some devices cannot execute our code, which is regrettable, but the error may have been made by the device itself, not our code:}
