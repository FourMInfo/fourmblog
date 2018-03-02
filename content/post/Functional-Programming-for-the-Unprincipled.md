---
title: "Functional Programming for the Unprincipled"
date: 2018-03-02
tags: ["FP", "scala", "rant"]
draft: false
---

## Anti-Intellectual Semantics
Not too long ago, someone on Gitter called me (or, more precisely, something I said) “anti-intellectual.” I was more than a bit amused, and somewhat surprised and pleased by this accusation. The fact is, for much of my life I have been labeled by both friends and family, often in an accusatory tone, as being _overly_ intellectual. The funniest part about this interchange is that it was part of a discussion on how prevalent is the use of _**functional programming (FP)**_ by Scala programmers!

This all began when I read a Twitter comment by one of the luminaries behind the ScalaZ FP framework. He said: 

> Scalaz 8's competition is NOT Scalaz 7/Cats/etc. “No one’” uses these. The real competition is non-FP in Scala, i.e. 99% of the market._

I was gobsmacked by this claim that essentially 99% of Scala programmers are not doing functional programming. Even if we discount it as hyperbole, it still makes no sense. After all, anyone with even the slightest acquaintance with Scala is aware that Martin Odersky created this language with the intention that it allow programmers to use both the OOP and FP paradigms. Odersky himself evangelizes the functional programming aspects of Scala in his books, courses, lectures and talks about Scala. 

Is he claiming that nearly all Scala programmers are ignoring Scala’s built-in FP capabilities and just using it as “a better Java”? Actually he isn’t. What he _is_ claiming is that the vast majority of Scala programmers are not doing the _right sort_ of FP programming and the new version (8) of the ScalaZ framework might help move the meter.

This comment, which reflects an attitude found among many FP luminaries in the Scala and Haskell communities, _sounds_ snobbish and is, I believe, detrimental to the broader adoption of FP.  When I made that exact point to the poster, is the precise moment my comment was labeled “anti-intellectual” by yet another well-known and prolific Scala community contributor. Very recently I had a similar conversation on Gitter with other Scala FP community leaders. I wasn’t called “anti-intellectual”, but my comments were dismissed as quibbling about “semantics”.

Social media like Twitter and Gitter are not necessarily the best places to have such a discussion. Hence I decided to write a longer piece about what I find disturbing about the attitudes behind that Twitter comment, which, as noted, is pretty widespread. 

## So What is Functional Programming (FP)?
The core of being a software programmer is writing a set of instructions to get the damn computer to do what you want it to do. Computer operations at their lowest level are mostly about moving bits of data around in registers and XOR and XANDing them. The human brain does not naturally think about solving problems in this way.

So from the earliest days of computer usage, computer scientists and engineers have worked at developing abstractions for these operations, encapsulating these in programming languages to make the life of programmers easier. Over time these abstractions have formed several alternative paradigms for programming languages.

The most basic of these paradigms, and the one nearly every programmer learns first, is the _imperative_ paradigm. This paradigm abstracts out the bits being moved through registers in the computer hardware by encapsulating data in data structures. We then use a set of high level logical constructs–-_if_, _while_, _for_—to write algorithms to get the computer to manipulate the data in the data structures to do what we want it to do. Essentially, however, we are still looking at the problem from the computer’s perspective. The recipe or set of instructions (commands––hence _imperative_) we give it is not the way we humans would naturally think about the problem.

One of the first things every programmer learns about are _functions_. These are chunks of code that can be named and referenced in other parts of the program that can do “things”.  Functions come out of another paradigm known as _structured programming_. As computer software was used to solve more complex and larger problems, imperative programming just didn’t work well. The core idea of structured programming is to divide and conquer––decompose the problem into smaller and smaller parts, which are encapsulated in functions. Then use these parts to compose bigger and bigger components, and thereby solve the whole problem more easily. 

The problem with structured programming is that it doesn’t really give you much guidance on what is the best way to decompose your problem. That’s where _object-oriented programming (OOP)_  comes into the picture. OOP is all about modeling your software program on the business domain. Essentially objects in your problem domain (e.g. _customers_, _products_, _orders_) are encapsulated in data structures with the same names. Associated with those data structures are a bunch of functions or operations that model operations in the business domain. We then tie the whole system together by having these components (objects) use these operations to give commands to each other  (e.g. a _customer_ tells the _store_ to _place_ an _order_). This type of abstraction makes it a whole lot easier for humans to think about the problem.

Perhaps OOP has taken us _too_ far from computer-centric thinking.  Once we have modeled the business domain, we are left with the problem of how to bridge the conceptual gap back to computer operations. OOP proponents developed what are known as _patterns_, essentially a bunch of heuristics, meant to guide programmers in bridging the gap between the domain model and the software architecture and implementation details. But these heuristics are not hard and fast rules. Moreover, there are so many of them, it’s impractical to remember them all or really know when and how to properly apply them. In fact, despite having developed and taught a [course on OOP][1], for the most part I never use patterns except at the highest levels of design. Finally, underneath the hood, OOP is still using imperative & structured paradigms, with all their limitations. 

Ultimately, what we really want is an abstraction that uses a well known and natural human cognitive model for problem solving that provides precise and exact guidance on how to address common computational problems. Fortunately, we have such a cognitive model: it’s called mathematics! So it would be great if we could develop a paradigm to generally apply mathematics to writing programs. _That_ is the essence of what the _functional programming_paradigm is all about!

In olden times, computer operations were called _data processing_ because at the most fundamental level, what we want the computer to do is transform one set of a data into another set of data. It’s a shame this name has fallen out of favor to _information technology._ Data processing is still a useful way to describe even the coolest new tech like blockchain. And data processing is actually a core aspect of what the _functional programming_ paradigm is all about. Instead of thinking about the problem from the domain’s perspective a la OOD, we think about the problem as a data transformation. And the way we humans have done data transformations long before computers were invented, is through mathematical functions.

Despite the similarity in name, standard programming functions aren’t exactly what the word _functional_ in the phrase is referring to. Rather, it is referring to the mathematical definition of a function, which in a very loose way may be defined as a “process” of some sort that takes values from one set (called the _ domain_) and associates (_maps_) those values to another set (called the _range_). Another way to describe a mathematical function is _a transformation of a set of inputs into a set of outputs_.  To start, you look at your business domain and analyze the data flows. Then to_do_ functional programming you need to think about your problem in terms of a pipeline of mathematical functions. You start with your initial data and make it input to a function that transforms it. The output of this function is the input to the next function and so on––hence the term _pipeline_. The output at the end of the pipeline is data in the final form you want it!

I would argue that it’s likely that 99% of programmers (and not just Scala programmers) are, at least some of the time, already doing and enjoy doing FP in the way I described it above! They just may not know that what they are doing is called FP.

First, nearly all programmers today know at least the basics of the Bash shell. As part of that, nearly every programmer has written or at least seen and understood a simple bash pipeline like this:

	ls -al | grep ".png" | wc -l

Ok, right there I’ve written a functional program! I’m willing to bet you have too! (Much thanks to Alvin Alexander and his excellent book [Functional Programming Simplified][2]where I first saw someone make the [connection between Unix pipelines and FP][3]). Ask anyone why they like using the Bash shell, and command pipelines will surely be in the top 2 reasons cited. It’s a fun, useful and easy way to get at the data you need.

One of the most popular NoSQL databases available today is MongoDB. I can’t prove this, but I’m willing to argue that one of the main reasons it became so popular is its aggregation framework. People with many years of SQL experience tend to make fun of the aggregation framework “(_said in sarcastic Foamy voice_) Oh I could do those 10 lines so much easier in one SQL statement!” But the aggregation framework is essentially a functional pipeline, it is easy and fun to use, and a very natural way to extract and transform data in a document database.

Finally wrapping back around to the claim about Scala programmers not doing FP: ask your typical Scala programmer (even the “better Java” crowd) what they like about the language and they will almost surely say the ability to transform data in a functional pipeline. Here is a simple [example from Stackoverflow][4] of taking a set of products and creating a new set with only unique values on e.g. the product model:

```Scala
productModels
  .groupBy(.1)            // produces MapProduct, Map\[Int, Product]
  .filter {case (k,v) => v.size == 1} // filters unique values
  .flatMap {case (,v) => v}
``` 
Perhaps it is true that very new Scala programmers don’t do this, but very quickly almost all Scala programmers begin to think this way and find it fun, productive and relatively easy to do.

Finally, for another more detailed description of what functional programming as a data flow transformation pipeline means, and the advantages of this paradigm, you can and should read [this excellent piece][5] by Li Haoyi. 

## The Purity Ring
At this point I am sure many of my readers are shaking their heads, and perhaps their fists at me. Some might object that if FP is so “useful” and “natural” as I claim, why does it have a reputation for being so difficult and why isn’t it used more widely? 

First, let’s eliminate the argument that it’s the _mathematics_ aspect that scares people off. Even if you are not a [mathematical Platonist][6](a position I admit has great appeal for me personally) who believes our brains are hard-wired to discover mathematical truths, mathematics is still an almost universal tool set for humans, and has been throughout history. In almost every country in the world today, at least the basic tools of mathematics are part of every person’s education. So even if our brains aren’t hardwired for mathematical discovery, mathematics is still a fundamental human tool. Certainly anyone who does programming has studied more than the standard amount of mathematics and mathematics is part of the computer science curriculum. So lack of familiarity or comfort with math is not the main barrier for programmers to use FP.

On the flip side, many hard core proponents of FP will be objecting that my explanation here does not describe _real_ FP. In fact, as noted earlier, I have been told as much. After all, when describing the ideal programming paradigm, I noted we want to use mathematics because it is precise, as opposed to the vague heuristics of OOP. And my description above which shows FP to be “fun, productive and relatively easy to do” leaves out a clear explanation of this most important advantage!

A core principle inherent in the definition of mathematical functions is that every time you use the same inputs on a mathematical function, you will always get, and only get, the exact same singular output. Part of what guarantees this is that in the course of your calculations, variables are immutable. Once you assign them a value, that value can’t change. The other part that guarantees this it that functions only make changes locally and don’t effect, or can’t be affected by variables other than the inputs.
Hence we can reliably substitute any expression for it equivalent value. This is known as _referential transparency_ (the infamous _purity_).

If we could impose these requirements on our program’s functions, we can always know exactly how they will perform no matter how many times they are run. We can reason about the logic flow and be confident our programs will perform as advertised, without even testing. Essentially they would be bug free! We would be able to quote the famous line in Edgar Dijkstra’s preface to his _A Discipline of Programming_: "None of the programs in this monograph, needless to say, has been tested on a machine."  

Unfortunately such programs wouldn’t be very useful for most  data processing systems applications. Since we don’t have total control of our inputs, we can’t demand that our functions always provide exact outputs. We have to deal with getting partial results, or results with an unknown range or even error results. Similarly, we can’t demand that our functions _only_ provide specific results. Sometimes we want to be able to log whats going on, or send notifications to other processes over and above the output of the function. And of course state mutation is often a requirement of what we need to do.

All these situations describe bumps in the road to data processing as a clean chain of pure mathematical functions. These bumps are also known as _effects_. If not handled properly, these effects become_side effects_ , i.e. computations that break referential transparency. Essentially this means that the results of our program are neither predictable nor consistent.

But FP it it’s most developed form has precise mathematical tools for dealing with effects so that we can handle them in ways consistent with and conforming to the principles of mathematical functions. Moreover there are only a relatively limited number of effects that we need to deal with, and these same effects repeat themselves in all data processing systems, no matter what the business domain. So the number of patterns we need to learn are far more limited than in OOD. Most importantly the tools we have to deal with these patterns are mathematically precise and can be (and are) encapsulated in programming frameworks.

So this type of functional programming, the “real” functional programming, more correctly called _pure_ functional programming, allows us to build data processing systems that are consistent, reliable and predictable! This is orders of magnitude more important and useful than vague notions like “fun and productive”. Given this, why isn’t the whole programming world rushing to adopt functional programming? 

## Don’t Put the Ring On!
[This article][7] essentially provides most of the reasons why people, even people who claim to be sympathetic to FP, don’t want to do it. Put aside his comparison of Go and Scala, which is just apples and oranges, and his exaggerated critiques of Scala. What’s relevant here are the attitudes he displays about pure FP. Tl;dr: 

1.  Pure FP requires you to think hard before you do it. You write less code so you are less productive.
2.  Pure FP  requires you to think hard and it’s complicated. Hence very few programmers want to bother to learn it.
3.  Pure FP code is obscure to read and full of weird math thingees.
4. 2+3 = if the one pure FP person you have on staff is on vacation, you’re doomed.
5. Go, by contrast, is super easy. Even PhP programmers (“the bottom of the heap”) can learn it fast, and spit out reams of code and new features really quickly.

The one good argument he makes is that different applications require different programming languages. Something like Kubernetes needs to be written in something like Go because otherwise it would have been written in C  or C++ (not Scala or Haskell). Perhaps it would have been better if it had been written in Rust, but Go and Kubernetes are both Google babies, so yep.

Unlike the author’s startup, Google, Microsoft and Red Hat can and are applying enormous amounts of resources and brain power to ensure that Kubernetes, despite being written in Go, is safe, secure, consistent and reliable. By contrast, a typical startup, and more importantly even large enterprises ranging from financial institutions to nuclear reactors, don’t have these level of resources and so do have to worry about all the [flaws in Go][8]. 

Behavioral science can give us additional insight on why programmers don’t learn pure FP. First, humans have difficulty thinking about future events and are focused on current rewards and risks. Unfortunately, software project managers are usually rewarded for pushing features out the door, not for creating safe, secure, consistent and reliable software. Moreover when the disastrous breach inevitably happens, the programmers and project managers who created the awful code have likely moved on. So it makes total sense to prefer imperative Go (quickly push out lots of features that gives me current rewards) over Scala pure FP (consistent and reliable software that has less features now but more likely to prevents future disasters). 

Moreover, it is definitely true that the concepts needed for learning how to properly handle effects and the programming frameworks that are used for doing so are not easy or even relatively easy. They require effort to learn how to read and even more effort to learn how to use properly.  Behavioral science also teaches us, that by nature humans are lazy. So there is a great deal of psychological inertia to overcome in learning something difficult like pure FP. 

## FP for the Unprincipled
While the ultimate measure of a successful software project is the agile definition _working code that meets customer needs_, excellent systems are also reliable (safe, secure, consistent) and maintainable (easy to change, easy to bring on new team members). We all know that many (perhaps most) software systems are the opposite of that! As [this article][9]points out, using pure FP while not a goal in itself, is one important means for helping us programmers create excellent software. 

So how do we encourage programmers to use FP (and other “hard”) tools to become better at our craft? There are three methods that behavioral economics teaches us we can use to change human behavior: persuasion, education, and choice architecture. Let’s look at all three.

Let’s start with persuasion. The original Tweet that started this rant, had a correct intuition that pure FP has to be “marketed”. The problem is that pure FP proponents are terrible at marketing. I have often heard as part of conference talks, pure FP referred to as _principled_ or even _ethical_––seemingly implying that the rest of us programmers who don’t use pure FP are unprincipled and perhaps even unethical! Even the term _purity_ can be off-putting. Layer on top of this the   terminology being thrown around in discussions of pure FP—functors, monads, monoids, Kleisli, etc.—and you can see why FP proponents sound like real snobs in an elite club that the _hoi polloi_ of programmers will never, ever, be able to join.

I stress that I use the phrase “sound like” because in reality, almost all the people I have encountered in the pure FP community are the opposite of snobs. They genuinely want more people to join them in using pure FP and are eager to teach people what it is, and how and why to use it. And they put their money where their mouth is. They spend enormous amounts of personal time developing FP tools and frameworks and hours on Gitter and other forums voluntarily teaching people how to do pure FP. All of them, especially the ones I had the Gitter/Twitter discussions with, are people I highly respect and admire for their enormous contributions to the Scala/Scala FP ecosystem

Unfortunately what many of them don’t seem to realize or accept is that semantics _do_ matter. Behavioral science also teaches us that how you anchor what you are “selling” has a huge impact on how easy it is to sell. By saying 99% of programmers are not yet in this “market”, you end up excluding, not enticing, that 99%.

It is not my place to tell other people how to spend their time. So I certainly can’t ask FP proponents to be more generous of their time or more tolerant of novices. However, to those who are already being generous and who obviously feel leading more people to the FP promised land is a worthwhile endeavor, I do feel comfortable giving some advice.

Avoid language that sounds like you are judging other people, even if that is not your intention. Yes I understand the terms “pure” and “principled” are not referring to character, but to mathematical aspects of the concepts. But your uninitiated audience won’t understand that. Ban “ethical” and “principled”  and perhaps even “pure” from your lexicon. Reserve terms like “unprincipled” and “unethical” for when you are talking about programmers who, for example, help companies like VW or Uber cheat!

On the positive side, work on broadening the tent of functional programming. Sure FP is not simply pipelines, and pipelines are not necessarily FP. But thinking of FP in its broadest sense, allows you point out to programmers that they have likely already taken their first steps into the FP world. People often joke that Scala is a “gateway drug” to Haskell. Leverage that idea to persuade people FP really isn’t that scary. 

In fact, what got me moving down the path of learning pure FP, was using optics in the _Circe_ library. I still don’t fully understand them, but they were easy to use and made my code simpler and far easier to understand than the alternatives.  Using _Option_ or _Either_ or _for comprehensions_ may be just baby steps in the big FP picture. But those steps can be a springboard to persuading programmers that FP is worthwhile and can be usefully applied even before you fully understand it. They also provide simple examples that can help in educating novices.

Which is a good segue into the topic of education. Currently there aren’t enough resources for novices to help us wrap our head around pure FP.  The people in the vanguard of adopting pure FP are the smartest programmers out there. Very smart people often have great difficulty being able to get down to the level of the rest of us. Moreover many of the smartest people are busy doing FP, not necessarily teaching it. 

Fortunately, precisely because the vanguard are so generous with their time, more and more learning resources for explaining pure FP are being developed—books, articles, blog posts, conference talks etc. Again, here is some advice to help be more effective when talking to us novices.

FP proponents argue we can’t use just any words to describe FP concepts because mathematics is precise and so terminology needs to be precise. Fuzzy terminology will lead to fuzzy thinking and will do more harm than good. But as in all fields of mathematics, the terminology has to be build up by layers of examples and simpler concepts. If you want to get people to reach a precise understanding, you have build up those layers. Along the way, you have to be tolerant of fuzzy thinking and foster intuitions not definitions, because mathematical discovery is a voyage. 

Try to build off of concepts and intuitions that your novice FP programmer might already have. Don’t talk down, but do bring down your language to simpler terms, when you want to reach a wider audience. Remember, there are lots of holes in people’s knowledge so don’t assume they already know. Repetition doesn’t hurt. Also don’t forget that there is a far larger audience of novices out there, than experts. Try to step back to help shepard them along into the tent.

A great example of someone taking many of the above points into consideration, is [this presentation][10] by Rob Norris. It was extremely helpful to me in making more intuitive the difference between effects and side effects, and what these thingees called monads, applicative etc. are all about. Watching it, I had more than one “a-ha” moment. It’s still a bit complex and many points went over my head, but that was more a result of the limited time available. 

Finally, we come to choice architecture, which essentially is about making it easier for people to choose doing the right thing. One of the best ways to get programmers to adopt good programming paradigms and practices is to build a development process that focuses on/values code quality, over code and feature quantity. The fact that the guy who wrote that blog post on “Go vs Scala” brags about doing the opposite, shows how this type of process is not as prevalent as it should be. 

Ultimately, the best incentive for programmers is providing them tools that makes for less work and more play. The more programmers use FP, the more they learn that it actually reduces the time they have to spend coding, testing and debugging.  So gently encouraging programmers to go down the FP path (instead of chastising them) will itself create a positive, virtuous circle. 

[1]:	http://old.fourm.info:8082/TPP/OOAD/CB/
[2]:	https://alvinalexander.com/scala/functional-programming-simplified-book
[3]:	https://alvinalexander.com/scala/fp-book/how-functional-programming-is-like-unix-pipelines
[4]:	https://stackoverflow.com/questions/36606148/scala-filter-a-map-for-based-on-unique-values-within-map-values
[5]:	http://www.lihaoyi.com/post/WhatsFunctionalProgrammingAllAbout.html
[6]:	https://plato.stanford.edu/entries/platonism-mathematics/
[7]:	https://movio.co/en/blog/migrate-Scala-to-Go/
[8]:	http://yager.io/programming/go.html
[9]:	http://degoes.net/articles/fp-is-not-the-answer
[10]:	https://www.youtube.com/watch?v=po3wmq4S15A&feature=youtu.be