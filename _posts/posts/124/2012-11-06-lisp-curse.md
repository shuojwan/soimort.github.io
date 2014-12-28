---
layout: post
uri: /posts/124
permalink: /posts/124/index.html
title: 【译文】Lisp魔咒：对Lisp的非技术性吐槽
category:
tag:
description:
disqus: false
lang: zh
---
Original Article: [The Lisp Curse](http://www.winestockwebdesign.com/Essays/Lisp_Curse.html)
by Rudolf Winestock  
(Chinese Translation by [Mort Yao](http://www.soimort.org/))

***

这篇文章的标题叫“The Lisp Curse”。

我给它加了一个副标题，叫“对Lisp的非技术性吐槽”。

毫无疑问，这是一篇非技术性质的文章，但是它也许比很多技术文章能更好地解释一些疑问。列举几个无聊的的命题：_“为什么世界上[最好的编程语言](http://schemers.org/)没有得到它应有的地位”_、_“为什么自底向上支撑着我们个人计算机乃至整个网络的Unix / BSD / GNU / GTK+ / Qt / Linux / Apache / MySQL...不是用Lisp/Scheme写的”_、_“为什么王垠[批完Google](http://news.cnblogs.com/n/153840/)[批学术界](http://news.cnblogs.com/n/157058/)却没做多少[牛逼哄哄的项目](https://github.com/yinwang0)”_或者_“为什么说‘[孤狼](http://en.wikipedia.org/wiki/Lone_wolf_\(trait\))黑客’对开源软件的生态环境是有害的”_……诸如此类。

顺便说一句，我最初是在[@yukihiro_matz](https://twitter.com/yukihiro_matz/status/265244572853088256)的推上看到这篇文章的分享的。所谓的“孤狼黑客”，并不是指Matz和Van Rossum这些人——至少从Python和Ruby发布到社区的一刻起就不再是了。

再补充一句，我相信不管是这篇文章的原作者还是翻译君本人，都没有任何对[Lisp社区](https://groups.google.com/forum/?fromgroups#!forum/comp.lang.lisp)不敬的意思——只是就一项事实陈述和复述某种观点而已。

好了，废话少说，以下是正文内容。

***

这篇文章是另一次尝试，旨在解释Lisp语言在具备强大力量的同时、为何Lisp社区却无法重现它们在[“AI之冬”](http://c2.com/cgi/wiki?AiWinter)之前的辉煌。毫无疑问，即便在式微之后，Lisp语言仍然是各种奇思妙想的重要来源。这一事实，加之各种Lisp实现的优异架构，还有如今在长达十年之后Lisp的复兴、显示着那些Lisp拥护者们是多么需要为自己的得意之作找到一点优越感；尽管有这一切，他们却没能成功地把Lisp的力量转换成一场压倒性的技术革新。

在本文中，我将阐述这样一个论点：Lisp那极其强大的表达能力，实际上是如何成为它缺乏前进动力的致命诱因的。

***

Lisp的力量也是它自身最危险的天敌。

要证明这件事情，试想一个简单的思维实验：选择两种非面向对象的程序语言。你的任务，如果你愿意接受的话，就是为它们提供面向对象编程范式的支持，并且保持它们与原语言向后兼容——排除一些边界情况以外。把任意两种语言放到这个思维实验的设定当中，你会很容易发现一些语言较另一些语言更容易完成任务。这正是这个思维实验的要点。随手举个简单的例子：[INTERCAL](http://en.wikipedia.org/wiki/INTERCAL)和[Pascal](http://en.wikipedia.org/wiki/Pascal_\(programming_language\))。

现在让我们把这个思维实验变得更有说服力些。想象一下给C和Scheme添加面向对象的支持。让Scheme支持面向对象不过是个稍微费点脑筋的家庭作业。另一方面，让C支持面向对象，你恐怕得有Bjarne Stroustrup的本事才能办到。

这种对于解决问题所需才能和努力程度上的分歧，造成了_Lisp的魔咒_：

__Lisp是如此强大，以至于在其他编程语言中的技术问题，到了Lisp中变成了社会问题。__

***

想一想Scheme的情形吧。因为让Scheme支持面向对象是如此轻而易举，许多Scheme黑客都完成过这件事情，更准确地说，是许多_独立的_Scheme黑客都完成过。这就导致了在20世纪90年代，这个语言的面向对象支持包像工厂量产出来的库存清单一样数不胜数。想想[选择谬论](http://en.wikipedia.org/wiki/The_Paradox_of_Choice%3A_Why_More_Is_Less)就知道，没有哪一个包能够成为正式的标准。如今某些Scheme实现已经有了它们自己的面向对象功能，这还不算太坏。尽管如此，那些五花八门的由不同独立开发者开发出来的包所造成的问题，正如Olin Shivers在给[Scheme Shell（scsh）](http://en.wikipedia.org/wiki/Scsh)写文档的时候所提到的一样。

独立黑客们写出来的程序基本上遵循“抓痒模型”。这些程序解决了写程序的黑客们自己关心的问题，但是却未必能很好地处理对于其他人来说有用的部分功能。况且，虽说这些程序无疑可以在这个黑客自己的环境配置上运行得很好，但却不一定能移植到其他的Scheme实现、甚至不同平台上的同一Scheme实现上。文档可能会极度匮乏。从现实的角度讲，一个黑客用自己挤出来的空闲时间做出来的项目，当然也可能会因为黑客自己的现实生活问题而烂尾。正如Olin Shivers指出的那样，这些个人性质的项目更倾向于解决整个问题的百分之八十。

Mark Tarver博士的文章，[The Bipolar Lisp Programmer（双面Lisp程序员）](http://www.lambdassociates.org/blog/bipolar.htm)，对这种现象有一个确切的表述。他写道，这些“孤狼”式的Lisp黑客以及他们：

_……不能把事情恰当地做完收尾。所谓的“用过就扔设计”绝对和[拉屎](https://www.healthtap.com/#topics/big-bowel-movements)这件事儿没什么两样（注：原文如此），而它来源于Lisp社区。Lisp允许你如此虎头蛇尾地了结一件事，而且还让你心安理得地这么去做。十年前，我有一次需要给我的Lisp程序写一个GUI。没问题，我找到了9个GUI库。麻烦在于这9个库没有一个拥有足够完整的文档，而且它们全部是bug充斥的。基本上，每个人都实现了他们自己的一套解决方案，对于他们来说能用就行。这是一种拉屎式的态度（注：原文如此）；反正我做到了，我消化它了。这同样也是无须在他人帮助下即可得到的产物。_

***

那么再想一想C语言在上述思维实验中的情形吧。由于在C上面实现面向对象支持的困难程度，只有两个严肃的解决方案摆上了台面：C++，以及Objective-C。Objective-C在Mac上最为流行，而C++几乎统治了其他一切平台。这意味着，给定一个平台，如何让C支持面向对象的扩展几乎已经被唯一确定了。这意味着这些语言的面向对象支持将拥有完善的文档，高度集成的IDE，和兼容性良好的库，等等。

Mark Tarver博士的文章说到这一点：

_现在与之相反，C/C++的做事方式完全不同。用镊子和胶水一步步搭建成一个东西实在太他妈困难了，所以你所做的一切都是实实在在的成就。你想要为它好好地写些文档。你会在做一个规模可观的C语言项目时候需要他人的帮助；因此你也更加容易变得社会性、学会去与他人合作。你需要做到这些，因为你需要完成某件事情。_

_而全部的这些，从一个雇主的角度来讲，是非常吸引人的。十个能够相互交流、写文档与团队协作的人显然会比一个像拉翔一样自己去hack些Lisp代码的人更有用，而这种翔的替代品只能是另一坨翔，这些翔们随时都可能因为某些个人的问题、自己退出项目而丢下一个不可收拾的烂摊子。_

所以说，那些懂C的人不会去纠结“我应该用哪种面向对象系统？”相反，他们会去选择C++或者Objective-C，就像他们的同事所选择的一样，然后他们会提问“我该怎样使用面向对象的功能X？”答案很简单：[“咕狗一下，你就知道。”](http://www.baidu.com/)

***

真正的黑客，当然早就知道面向对象并非如它的拥趸们所宣称的那样是解决一切问题的灵丹妙药。真正的黑客已经在探寻更加高阶的概念，诸如不可变数据结构、类型推断、惰性求值、monad、arrow、模式匹配、约束编程，等等。真正的黑客也都知道，C/C++对于写大部分不需要进行任意位操作的程序来说并不合适。尽管如此，Lisp的魔咒仍然存在。

一些沾沾自喜的Lisp发烧友，调研了当前学术界编程语言的硕果（Haskell、OCaml等等）后，发现它们所缺失的一些特性，要么就是已经在Lisp中存在、要么就是可以用Lisp很轻易地实现——并且可以[改进](http://www.reddit.com/r/programming/comments/ujj3/a_critique_of_abelson_and_sussman_or_why/cutzn)——基于Lisp宏。他们也许是对的。

但是太可惜了，Lisp黑客们。

***

Mark Tarver博士——在上面已经两次引用过——曾经设计过一个Lisp的方言，叫做[Qi](http://www.lambdassociates.org/)。它仅仅由少于一万行的宏组成，基于Clisp运行。它实现了绝大部分Haskell和OCaml所独有的特性。从某个方面来说，Qi甚至超越了它们。举个例子说吧，Qi的类型推断引擎本身是_图灵完全_的。在[这样的](http://www.wimp.com/theman/)一个由天才科学家组成的杰出团队才能开发出Haskell语言的世界中，Tarver博士，他完全是一个人做出来了Qi。

再看一眼上面这段话。仔细想想，是不是可怕极了。

***

_给读者的习题_：假想Haskell与Common Lisp之间发生了激烈的对抗，下一步将会发生什么？

_答案_：Lisp魔咒应验了。每两个或者三个Lisp黑客就会开发出一套属于自己的惰性求值、纯函数式、arrow、模式匹配、类型推断等等的实现。大部分这种项目都是孤狼式开发。因而，它们具备大部人所需要的80%功能（虽然这80%的定义会随情况不同而各异）。它们的文档通常会很差。它们无法在不同的Lisp系统上移植。有些项目可能起初信誓旦旦地会维护下去，直到开发者决定自己跑到别处赚钱去了，结果丢下一个无法收拾的烂摊子。有一些可能会在某种程度上多多少少地打败Haskell，但是它的认可度会被[comp.lang.lisp](https://groups.google.com/forum/?fromgroups#!forum/comp.lang.lisp)新闻组里面的口水战淹没。

_故事的结局_：任意一个传统的Lisp黑客的宏能够拼凑成一个文档匮乏的、不可移植的、bug充斥的80%的Haskell实现，_仅仅因为_Lisp是一种比Haskell表达力更加强大的语言。

***

这个故事的教育意义在于，__次级效应和三级效应至关重要__。技术不只是影响我们解决技术问题的方式，它也影响着我们的社会行为。而社会行为会反馈并施加影响于我们最初试图解决的技术问题。

Lisp是一个活生生的事例。Lisp是如此强大有力，它鼓励个人的、狂热的特立独行。在[Lisp机器](http://en.wikipedia.org/wiki/Lisp_machine)曾经盛极一时的年代，这种特立独行产生了举世瞩目的成果。但也正是同样的特立独行，阻碍了所谓“自底而上纯Lisp实现”的计算机系统的复苏；自Symbolics和LMI夭折之后，再也没有一个“Lisp操作系统”项目达到过值得令人关注的高度。

这些次级和三级效应的一个后果是，即使Lisp是有史以来最富于表达力的编程语言，以至于理论上几乎不可能创造出比它更具表达力的语言，_Lisper们将仍然有许多从其他编程语言那里学习的东西_。Smalltalk程序员们教会了每个人——包括那些Lisp黑客们——多多少少一点关于面向对象的概念。[Clean语言](http://www.discenda.org/Clean/)和[Mozart/Oz](http://www.mozart-oz.org/)也有着一些自己的奇特之处。

***

Lisp魔咒并不违背[Stanislav Datskovskiy](http://www.loper-os.org/?p=69)的至理名言：__雇主们更喜欢可以被取代的雇员，而不是生产率最高的雇员。__说得太实在了。你早该醒悟到那些管理学课程只是骗钱的把戏。然而，他这篇文章的最后几行似乎存在问题。请看：

_在“自由软件”的世界里，工业界教条仅仅是在口头上被激烈地批判，但却从未在实践中被反对过。那些“办公隔间地狱”里被唯恐避之不及的概念，同样也未曾在业余爱好者中间得到过青睐。_

在脚注中，他将Linux作为一个拒绝追求新奇想法的实例。为了例证，他将[操作系统](http://slashdot.org/story/00/06/06/1151209/Systems-Research-Is-Dead)作为自己的一个论点（下面评论的1L是SB）。他并没有提到编程语言。Python和Ruby都受到了Lisp的影响。很多它们的饭表示了对Lisp的尊重，而他们的一些兴趣则促进了Lisp的复兴。公正地讲，JavaScript也曾被描述为“披着C外衣的Scheme”，尽管它诞生在那些[办公隔间地狱](http://www.jwz.org/tent-of-doom/)中间。

即便有如此大的影响力，在工业和开源界里，Lisp也仅仅只吸引了一部分程序员的一部分注意力，而这也是拜最近脚本语言的兴起所赐。那些拿着MBA学位的高富帅码农们的思维封闭并不是唯一的原因。“Lisp魔咒”本身能解释更多的事情。

***

提供给Lisp的、可用的自由开发环境可以作为“Lisp魔咒”的一个例证。

尽管说出来让人难堪，但必须得有人去做这件事情。忘掉Lisp机器吧；我们甚至还没有一个能达到算得上[Smalltalk](http://www.opencobalt.org/)[黑客](http://www.pharo-project.org/home)[小康标准](http://www.squeak.org/)的开发环境（_“我总赶脚到Lisp是一个牛逼的语言，而Smalltalk是一个牛逼的环境。”_——[Ramon Leon](http://onsmalltalk.com/aha-moments-in-lisp)如是说）。除非他们愿意付上千刀美元，否则Lisp黑客们仍然会受制于Emacs。<del>（翻译君：[比肾还贵](http://www.lispworks.com/buy/prices-1c.html)的LispWorks，包邮哦亲，[欲购从速](http://disney.go.com/wreck-it-ralph/)哦）</del>

James Gosling，第一个在Unix上运行的Emacs的作者，[恰当地指出了](http://www.computerworld.com.au/article/207799/don_t_use_emacs_says_java_father/)Emacs已经长达二十年没有任何基础上的变动。这是因为，Emacs维护者们只是不断地在这个当年由一个MIT的AI实验室的研究生做的设计上垒代码，那时Emacs项目仍然间接地从国债那里获得资助。也许Slashdot喷子会反驳说Emacs已经无所不能，它可以完成其它任何开发环境所能做的事情，而且只会完成得更好。不然那些[当年曾经用过](http://www.ymeme.com/zmacs-vs-emacs-manual.html)Lisp机器的也要这么说。

那么，为什么Lisp黑客们没有把那些Smalltalk家伙们给彻底打败呢？为什么他们没有做出一个自由的开发环境，可以从某种程度上唤回Lisp机器曾经的辉煌，即使他们不能够重现出另一个Lisp机器？

这件事没有发生的原因来自于Lisp魔咒。大量的Lisp黑客应该去协作。说得更详细些：大量_成为Lisp黑客的人们_应该去协作。而且他们应该学会合作去做一个新的设计、而非遵从一个从一开始就写死了的现有设计。这过程中不应该有任何来自外界的压力，例如风险资本家或者企业雇主，来干涉他们做事的方式。

每个项目都会存在参与者的分歧，诸如意见不合、风格或哲学上的冲突。如果这些社会性的问题持续下去，任何大的项目都无法完成，这就产生了一个让它们倾向于解决的反作用力。“要么我们团结一心，要么我们都会被吊死在同一棵树上”。而Lisp的强大表达能力削弱了这个反作用力；一个人总可以着手去自搞一套。这样，刚愎自用的黑客们认为不值得去应付观点分歧带来的麻烦；因此他们要么退出了合作项目，要么就干脆不参加已有的项目、而选择自力更生从头开始。这就是Lisp魔咒。

我们甚至可以自己去hack Emacs，为了追求个人理念中所谓的_“足够好”_。于是乎，Lisp诅咒差不多就变成了[“坏即是好（Worse is Better）”](http://en.wikipedia.org/wiki/Worse_is_better)的同义词。<del>（翻译君：这最后一段有点不知所云。。。）</del>

***

__Lisp的强大表达能力也会带来坏处。天下可没有免费的午餐。__

