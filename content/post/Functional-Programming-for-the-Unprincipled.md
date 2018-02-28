---
title: "Functional Programming for the Unprincipled"
date: 2018-02-28
tags: ["FP", "scala", "rant"]
draft: false
---

## Anti-Intellectual Semantics
Not too long ago, someone on Gitter called me (or, more precisely, something I said) “anti-intellectual.” I was more than a bit amused, and somewhat surprised and pleased by this accusation. The fact is, for much of my life I have been labeled by both friends and family, often in an accusatory tone, as being _overly_ intellectual. The funniest part about this interchange is that it was part of a discussion on how prevalent is the use of _**functional programming (FP)**_ by Scala programmers!

This all began when I read a Twitter comment by John de Goes, one of the luminaries behind the ScalaZ FP framework. He said:
> Scalaz 8's competition is NOT Scalaz 7/Cats/etc. “No one’” uses these. The real competition is non-FP in Scala, i.e. 99% of the market.

I was gobsmacked by his claim that essentially 99% of Scala programmers are not doing functional programming. Even if we discount it as hyperbole, on the surface this claim makes no sense. After all, anyone with even the slightest acquaintance with Scala is aware that Martin Odersky created this language with the intention that it allow programmers to use both the OOP and FP paradigms. Odersky himself evangelizes the functional programming aspects of Scala in his books, courses, lectures and talks about Scala. 

Is de Goes claiming that nearly all Scala programmers are ignoring Scala’s built-in FP capabilities and just using it as “Python with strong typing”? Actually he isn’t. What he _is_ claiming is that the vast majority of Scala programmers are not doing the _right sort_ of FP programming and the new version (8) of the ScalaZ framework he is working on, might help move the meter.

de Goes’ comment, which reflects an attitude found among many FP luminaries in the Scala and Haskell communities, sounds snobbish and is, I believe, detrimental to the broader adoption of FP.  When I made that exact point to de Goes, is the precise moment my comment was labeled “anti-intellectual” by yet another well-known and prolific Scala community contributor. Very recently I had a similar conversation on Gitter with other Scala FP community leaders. I wasn’t called “anti-intellectual”, but my comments were dismissed as quibbling about “semantics”.

Social media like Twitter and Gitter are not necessarily the best places to have such a discussion. Hence I decided to write a longer piece about what I find disturbing about the attitudes behind de Goes’ comment, which, as noted, is pretty widespread. To do that, I need to explain what exactly  _functional programming_ means (yes, “semantics”). I am not going to go into a great deal of detail. Rather I will provide some basic ideas along with pointers to resources I found helpful and convincing.

## So What is Functional Programming (FP)?
The core of being a software programmer is writing a set of instructions to get the damn computer to do what you want it to do. Computer operations at their lowest level are mostly about moving bits of data around, and the human brain does not naturally think about solving problems in this way.

So from the earliest days of computer usage, computer scientists and engineers have worked at developing abstractions for these operations, encapsulating these in programming languages to make the life of programmers easier. Over time these abstractions have formed alternative paradigms for programming languages.

The most basic of these paradigms, and the one nearly every programmer learns first, is the _imperative_ paradigm. This paradigm abstracts out the bits being moved through registers in the computer hardware by encapsulating data in data structures. We then use a set of high level logical constructs––\_if_, \_while_, \_for\_—to write algorithms to get the computer to manipulate the data in the data structures to do what we want it to do. Essentially, however, we are still looking at the problem from the computer’s perspective. The recipe or set of instructions (commands––hence _imperative_) we give it is not the way we humans would naturally think about the problem.

One of the first things every programmer today learns about are _functions_. These are chunks of code that can be named and referenced in other parts of the program that can do “things”.  Functions come out of another paradigm known as _structured programming_. As computer software was used to solve more complex and larger problems, imperative programming just didn’t work well. The core idea of structured programming is to divide and conquer––decompose the problem into smaller and smaller parts, which are encapsulated in functions. Then use these parts to compose bigger and bigger components, and thereby solve the whole problem more easily. 

The problem with structured programming is that it doesn’t really give you much guidance on what is the best way to decompose your problem. That’s where _object-oriented programming (OOP)_  comes into the picture. Essentially the idea is to look at objects in your problem domain (e.g. _customers_, _products_, _orders_) as encapsulated in a data structure and a bunch of associated functions. We then tie the whole system together by having these components (objects) give commands to each other  (e.g. a _customer_ commands the _store_ to _place_ an _order_). What is really great about OOP is that it allows us to model the software program on the domain. This type of abstraction makes it a whole lot easier for humans to think about how to solve the problem in software. 

Each of these paradigms introduce an abstraction that moves us further and further away from writing software from the computer’s perspective and closer to the problem domain itself. But underneath the hood, OOP is still using imperative (i.e. computer-centric) thinking to write the functions. Ultimately, we want an abstraction that totally let’s go of computer thinking and uses a well known human cognitive model for problem solving. To come up with such an abstraction, we need to describe in the most general terms what we as humans want from computers!

In olden times, computer operations were called _data processing_ because at the most fundamental level, what we want the computer to do is transform one set of a data into another set of data. It’s a shame this name has fallen out of favor to _information technology._ Data processing is still a useful way to describe even the coolest new tech like blockchain. And data processing is actually what the _functional programming_ paradigm is all about! Instead of thinking about the problem from the computer’s perspective, we think about the problem as a data transformation. And the way we humans have done data transformations long before computers were invented, is through functions 

Despite the similarity in name, programming functions aren’t exactly what the word _functional_ in the phrase is referring to. Rather, it is referring to the mathematical definition of a function, which in a very loose way may be defined as a “process” of some sort that takes values from one set (called the _ domain_) and associates (_maps_) those values to another set (called the _range_). Another way to describe a mathematical function is _a transformation of a set of inputs into a set of outputs_.  To _do_ functional programming you need to think about your problem in terms of a pipeline of mathematical functions. You start with your initial data and make it input to a function that transforms it. The output of this function is the input to the next function and so on––hence the term _pipeline_. The output at the end of the pipeline is data in the final form you want it!

So why is this better than imperative style programming? Many reasons. But before I go into the standard ones, I want to sharpen the argument I’ve been making thus far, viz. that FP is just a natural step in the road of abstracting away from computer thinking and towards human thinking.

Even if you are not a [mathematical Platonist][1](a position I admit has great appeal for me personally) who believes mathematical truths are discovered, not invented, mathematics is still an almost universal tool set for humans throughout history. In almost every country in the world today, at least the basic tools of mathematics are part of every person’s education. So even if our brains aren’t hardwired for mathematical discovery, mathematics is still a fundamental human tool. Certainly anyone who does programming has studied more than the standard amount of mathematics and mathematics is part of the computer science curriculum. Hence it’s seems almost obvious that looking at a programming problem as mathematical is more natural for humans, especially computer programming humans.

Unlike de Goes, I would argue that it’s likely that 99% of programmers (and not just Scala programmers) are already doing and enjoy doing FP in the way I described it above! They just may not know that what they are doing is called FP.

First nearly all programmers today know at least the basics of the Bash shell. As part of that, nearly every programmer has written or at least seen and understood a simple bash pipeline like this:

	ls -al | grep .png | wc -l

Ok, right there I’ve written a functional program! I’m willing to bet you have too! (Much thanks to Alvin Alexander and his excellent book [Functional Programming Simplified][2]where I first saw someone make the [connection between Unix pipelines and FP][3]). Ask anyone why they like using the Bash shell, and command pipelines will surely be in the top 3 reasons cited. It’s a fun, useful and easy way to get at the data you need.

One of the most popular NoSQL databases available today is MongoDB. I can’t prove this, but I’m willing to argue that one of the main reasons it became so popular is its aggregation framework. People with many years of SQL experience tend to make fun of the aggregation framework “(_said in sarcastic Foamy voice_) Oh I could do those 10 lines so much easier in one SQL statement!” But the aggregation framework is essentially a functional pipeline, it is easy and fun to use, and a very natural way to extract and transform data in a document database.

Finally wrapping back around to de Goes’ claim about Scala programmers, ask your typical Scala programmer what they like about the language and they will almost surely say the ability to transform data in a functional pipeline. Here is a simple [example from Stackoverflow][4] of taking a set of products and creating a new set with only unique values on e.g. the product model:

```Scala
productModels
  .groupBy(.1)            // produces MapProduct, Map\[Int, Product]
  .filter {case (k,v) => v.size == 1} // filters unique values
  .flatMap {case (,v) => v}
``` 
Perhaps it is true that very new Scala programmers don’t do this, but very quickly almost all Scala programmers begin to think this way and find it fun, productive and relatively easy to do.

“Fun, productive and relatively easy to do” are pretty fuzzy ways to describe the advantages of functional programming. For a clear and more detailed description of what functional programming as a data flow transformation pipeline means, and the advantages of this paradigm, you can and should read [this excellent piece][5] by Li Haoyi. 

## The Purity Ring
At this point I am sure many of my readers are shaking their heads, and perhaps their fists at me. Some might object that if FP is so “natural” as I claim, why does it have a reputation for being so difficult? I would argue that FP has this reputation because many FP proponents aren’t actually advocating for “FP as functional pipelines”, but for a more advanced form that takes more time and effort to learn. 

Worse still, many of these proponents will object that my definition here does not describe _real_ FP. In fact, as noted earlier I have been told as much. These proponents use the term _pure_ FP. They call programs that use pure FP _principled_ or even _ethical_––seemingly implying that the rest of us programmers who don’t use pure FP are unprincipled and perhaps even unethical! In short they sound like real snobs in an elite club that the _hoi polloi_ of programmers will never, ever be able to join. 

I stress that I use the phrase “sound like” because in reality almost all the people I have encountered in the pure FP community are the opposite of snobs. They genuinely want more people to join them in using pure FP and are eager to teach people what it is, and how and why to use it. And they put their money where their mouth is. They spend enormous amounts of personal time developing FP tools and frameworks and hours on Gitter and other forums voluntarily teaching people how to do pure FP. All of them, especially the ones I had the gitter/twitter discussions with, are people I highly respect and admire for their enormous contributions to the Scala/Scala FP ecosystem

Unfortunately what many of them don’t seem to realize or accept is that semantics _do_ matter. Human beings are irrational and how you anchor what you are “selling” has a huge impact on how easy it is to sell. By saying 99% of programmers are not yet in his “market”, de Goes ends up excluding, not enticing, that 99%.

What is this pure FP and why are so many people (including me by the way) so excited about it? A core principle inherent in the definition of mathematical functions is that every time you use the same inputs on a mathematical function, you will always get, and only get, the exact same outputs. By contrast, the outputs of standard programming functions might depend on global variables that change and so each time you run them, they may give different outputs. Or, the functions may themselves change global variables and not only provide the usual outputs. These _side effects_ mean that the results of programming functions are neither predictable nor consistent. In fact, programming functions often only have side effects and don’t have any outputs at all! Pure FP can be succinctly defined as FP without side effects.


[1]:	https://plato.stanford.edu/entries/platonism-mathematics/
[2]:	https://alvinalexander.com/scala/functional-programming-simplified-book
[3]:	https://alvinalexander.com/scala/fp-book/how-functional-programming-is-like-unix-pipelines
[4]:	https://stackoverflow.com/questions/36606148/scala-filter-a-map-for-based-on-unique-values-within-map-values
[5]:	http://www.lihaoyi.com/post/WhatsFunctionalProgrammingAllAbout.html