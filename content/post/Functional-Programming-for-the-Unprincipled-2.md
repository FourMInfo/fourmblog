---
title: "Functional Programming for the Unprincipled Part 2"
date: 2018-03-03
tags: ["FP", "scala", "rant"]
draft: false
---

## Frodo, Don’t Wear the Ring!
The [first part of this article][1] discussed why FP in general, and pure FP in particular, is a critically important programming paradigm that all software developers should add to their tool chest. We concluded by asking why isn’t the whole programming world rushing to adopt functional programming? We answer that here.

First, let’s eliminate the argument that it’s the _mathematics_ aspect that scares people off. Even if you are not a [mathematical Platonist][2](a position I admit has great appeal for me personally) who believes our brains are hard-wired to discover mathematical truths, mathematics is still an almost universal tool set for humans, and has been throughout history. In almost every country in the world today, at least the basic tools of mathematics are part of every person’s education. So even if our brains aren’t hardwired for mathematical discovery, mathematics is still a fundamental human tool. Certainly anyone who does programming has studied more than the standard amount of mathematics and mathematics is part of the computer science curriculum. So lack of familiarity or comfort with math is not the main barrier for programmers to use FP.

[This article][3] essentially provides most of the reasons (excuses) why people, even people who claim to be sympathetic to FP, don’t want to do it. Put aside his comparison of Go and Scala, which is just apples and oranges, and his exaggerated critiques of Scala. What’s relevant are the attitudes he displays about pure FP. Tl;dr: 

1.  Pure FP requires you to think hard before you do it. You write less code so you are less productive.
2.  Pure FP  requires you to think hard and it’s complicated. Hence very few programmers want to bother to learn it.
3.  Pure FP code is obscure to read and full of weird math thingees.
4. 2+3 = if the one pure FP person you have on staff is on vacation, you’re doomed.
5. Go, by contrast, is super easy. Even PhP programmers (“the bottom of the heap?”) can learn it fast, and spit out reams of code and new features really quickly.

The one good argument he makes is that different applications require different programming languages. Something like Kubernetes needs to be written in something like Go because otherwise it would have been written in C  or C++ (not Scala or Haskell). Perhaps it would have been better if it had been written in Rust, but Go and Kubernetes are both Google babies, so yep.

Unlike the author’s startup, Google, Microsoft and Red Hat can and are applying enormous amounts of resources and brain power to ensure that Kubernetes, despite being written in Go, is safe, secure, consistent and reliable. By contrast, a typical startup, and more importantly even large enterprises ranging from financial institutions to nuclear reactors, don’t have these level of resources and so do have to worry about all the [flaws in Go][4]. Hence for all the rest of us, languages that encourage formal methods have big payoffs and are worth the effort of learning.

Behavioral science can give us additional insight on why programmers don’t learn pure FP. First, humans have difficulty thinking about future events and are focused on current rewards and risks. Unfortunately, software project managers are usually rewarded for pushing features out the door, not for creating safe, secure, consistent and reliable software. Moreover when the disastrous breach inevitably happens, the programmers and project managers who created the awful code have likely moved on. So it makes total sense to prefer imperative Go (quickly push out lots of features that gives me current rewards) over Scala pure FP (consistent and reliable software that supposedly has less features now but is more likely to prevents future disasters). 

Moreover, it is definitely true that the concepts needed for learning how to properly handle effects and the programming frameworks that are used for doing so are not easy or even relatively easy. They require effort to learn how to read and even more effort to learn how to use properly.  Behavioral science also teaches us, that by nature humans are lazy. So there is a great deal of psychological inertia to overcome in learning something difficult like pure FP. 

## FP for the Unprincipled
While the ultimate measure of a successful software project is the agile definition _working code that meets customer needs_, excellent systems are also reliable (safe, secure, consistent) and maintainable (easy to change, easy to bring on new team members). We all know that many (perhaps most) software systems are the opposite of that! Formal thinking using pure FP can help us not only with reliability but also maintainability, as [this article][5] points out. While, as the author notes, we shouldn’t be fanatical about it, pure FP is a very important and useful tool for helping us programmers create excellent software. 

So how do we encourage programmers to use FP (and other “hard”) tools to become better at our craft? There are three methods that behavioral economics teaches us we can use to change human behavior: persuasion, education, and choice architecture. 

Let’s start with persuasion. The original Tweet that started this rant, had a correct intuition that pure FP has to be “marketed”. The problem is that pure FP proponents are terrible at marketing. I have often heard as part of conference talks, pure FP referred to as _principled_ or even _ethical_, seemingly implying that the rest of us programmers who don’t use pure FP are unprincipled and perhaps even unethical! Even the term _purity_ can be off-putting. Layer on top of this the   terminology being thrown around in discussions of pure FP—functors, monads, monoids, Kleisli, etc.—and you can see why FP proponents sound like real snobs in an elite club that the _hoi polloi_ of programmers will never, ever, be able to join.

I stress that I use the phrase “sound like” because in reality, almost all the people I have encountered in the pure FP community are the opposite of snobs. They genuinely want more people to join them in using pure FP and are eager to teach people what it is, and how and why to use it. And they put their money where their mouth is. They spend enormous amounts of personal time developing FP tools and frameworks and hours on Gitter and other forums voluntarily teaching people how to do pure FP. All of them, especially the ones I had the Gitter/Twitter discussions with, are people I highly respect and admire for their enormous contributions to the Scala/Scala FP ecosystem

Unfortunately what many of them don’t seem to realize or accept is that semantics _do_ matter. Behavioral science also teaches us that how you anchor what you are “selling” has a huge impact on how easy it is to sell. By saying 99% of programmers are not yet in this “market”, you end up excluding, not enticing, that 99%.

It is not my place to tell other people how to spend their time. So I certainly can’t ask FP proponents to be more generous of their time or more tolerant of novices. However, to those who are already being generous and who obviously feel leading more people to the FP promised land is a worthwhile endeavor, I do feel comfortable giving some advice.

Avoid language that sounds like you are judging other people, even if that is not your intention. Yes I understand the terms “pure” and “principled” are not referring to character, but to mathematical aspects of the concepts. But your uninitiated audience won’t understand that. Ban “ethical” and “principled”  and perhaps even “pure” from your lexicon. Reserve terms like “unprincipled” and “unethical” for when you are talking about programmers who, for example, help companies like VW or Uber cheat!

On the positive side, work on broadening the tent of functional programming. Sure FP is not simply pipelines, and pipelines are not necessarily FP. But thinking of FP in its broadest sense, allows you to point out to programmers that they have likely already taken their first steps into the FP world. People often joke that Scala is a “gateway drug” to Haskell. Leverage that idea to persuade people FP really isn’t that scary. 

In fact, what got me moving down the path of learning pure FP, was using optics in the _Circe_ library. I still don’t fully understand them, but they were easy to use and made my code simpler and far easier to understand than the alternatives.  Using _Option_ or _Either_ or _for comprehensions_ may be just baby steps in the big FP picture. But those steps can be a springboard to persuading programmers that FP is worthwhile and can be usefully applied even before you fully understand it. They also provide simple examples that can help in educating novices.

Which is a good segue into the topic of education. Currently there aren’t enough resources for novices to help us wrap our head around pure FP.  The people in the vanguard of adopting pure FP are the smartest programmers out there. Very smart people often have great difficulty being able to get down to the level of the rest of us. Moreover many of the smartest people are busy doing FP, not necessarily teaching it. 

Fortunately, precisely because the vanguard are so generous with their time, more and more learning resources for explaining pure FP are being developed—books, articles, blog posts, conference talks etc. Again, here is some advice to help be more effective when talking to us novices.

FP proponents argue we can’t use just any words to describe FP concepts because mathematics is precise and so terminology needs to be precise. Fuzzy terminology will lead to fuzzy thinking and will do more harm than good. But as in all fields of mathematics, the terminology has to be build up by layers of examples and simpler concepts. If you want to get people to reach a precise understanding, you have build up those layers. Along the way, you have to be tolerant of fuzzy thinking and foster intuitions not definitions, because mathematical discovery is a voyage. 

Try to build off of concepts and intuitions that your novice FP programmer might already have. Don’t talk down, but do bring down your language to simpler terms, when you want to reach a wider audience. Remember, there are lots of holes in people’s knowledge so don’t assume they already know. Repetition doesn’t hurt. Also don’t forget that there is a far larger audience of novices out there, than experts. Try to step back to help shepard them along into the tent.

A great example of someone taking many of the above points into consideration, is [this presentation][6] by Rob Norris. It was extremely helpful to me in making more intuitive the difference between effects and side effects, and what these thingees called monads, applicative etc. are all about. Watching it, I had more than one “a-ha” moment. It’s still a bit complex and many points went over my head, but that was more a result of the limited time available. 

Finally, we come to choice architecture, which essentially is about making it easier for people to choose doing the right thing. One of the best ways to get programmers to adopt good programming paradigms and practices is to build a development process that focuses on/values code quality, over code and feature quantity. The fact that the guy who wrote that blog post on “Go vs Scala” brags about doing the opposite, shows how this type of process is not as prevalent as it should be. 

Ultimately, the best incentive for programmers is providing them tools that makes for less work and more play. The more programmers use FP, the more they learn that it actually reduces the time they have to spend coding, testing and debugging.  So gently encouraging programmers to go down the FP path (instead of chastising them) will itself create a positive, virtuous circle. 

[1]:	../functional-programming-for-the-unprincipled-1
[2]:	https://plato.stanford.edu/entries/platonism-mathematics/
[3]:	https://movio.co/en/blog/migrate-Scala-to-Go/
[4]:	http://yager.io/programming/go.html
[5]:	http://degoes.net/articles/fp-is-not-the-answer
[6]:	https://www.youtube.com/watch?v=po3wmq4S15A&feature=youtu.be