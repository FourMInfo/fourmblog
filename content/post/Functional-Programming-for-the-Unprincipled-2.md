---
title: "Functional Programming for the Unprincipled Part 2"
date: 2018-03-03
tags: ["FP", "scala", "rant"]
draft: false
---

## Frodo, Don’t Wear the Ring!
The [first part of this article][1] discussed why FP in general, and pure FP in particular, is a critically important programming paradigm that all software developers should add to their tool chest. We concluded by asking why isn’t the whole programming world rushing to adopt functional programming? We answer that here.

[This article][2] essentially provides most of the reasons (excuses) why people, even people who claim to be sympathetic to FP, don’t want to do it. Put aside his comparison of Go and Scala, which is just apples and oranges, and his exaggerated critiques of Scala. What’s relevant are the attitudes he displays about pure FP. Tl;dr: 

1.  Pure FP requires you to think hard before you do it. You write less code so you are less productive.
2.  Pure FP  requires you to think hard and it’s complicated. Hence very few programmers want to bother to learn it.
3.  Pure FP code is obscure to read and full of weird math thingees.
4. 2+3 = if the one pure FP person you have on staff is on vacation, you’re doomed.
5. Go, by contrast, is super easy. Even PhP programmers (“the bottom of the heap?”) can learn it fast, and spit out reams of code and new features really quickly.

Most of these “reasons” are just wrong. The reality is that all programming paradigms require you to think hard about your problem before you start pumping out the code. The difference is that pure FP actually makes parts of this thinking easier, by  providing formal guidelines on how to solve your computational problems. The formal elegance of FP allows you to produce more features, with less code in less time. Most importantly, your code will likely be more secure, consistent and error free. 

Of course it takes effort, perhaps a lot of effort, to learn FP concepts and learn them well. But as noted previously, there are a far fewer patterns you need to learn in FP vs OOP. Moreover, you can use FP quite productively, even when you just know a few of its patterns. 

The one good argument he makes is that different applications require different programming languages. Something like Kubernetes needs to be written in something like Go because otherwise it would have been written in C  or C++ (not Scala or Haskell). Perhaps it would have been better if it had been written in Rust, but Go and Kubernetes are both Google babies, so…

Unlike the author’s startup, Google, Microsoft and Red Hat can and are applying enormous amounts of resources and brain power to ensure that Kubernetes, despite being written in Go, is safe, secure, consistent and reliable. By contrast, a typical startup, and more importantly even large enterprises ranging from financial institutions to nuclear reactors, don’t have these level of resources and so do have to worry about all the [flaws in Go][3]. Hence for all the rest of us, languages that encourage formal methods have big payoffs and are worth the effort of learning.

Actually the article does give us insight into the the real barrier to the adoption of FP.  It is definitely true that the concepts needed for learning how to properly handle effects and the programming frameworks that are used for doing so are not easy or even relatively easy. They require time and effort to learn how to read, and even more effort to learn how to use properly. Behavioral science teaches us, that by nature humans are lazy. So there is a great deal of psychological inertia to overcome in learning something like pure FP or even FP. 

Unfortunately, software project managers are usually rewarded for pushing features out the door, not for investing in training programmers to create safe, secure, consistent and reliable software. Go is so appealing for the same reason Fortran and Cobol stuck around for half a century—it is based on the most primitive of all programming paradigms and it’s super easy to learn. Essentially the author is advocating we throw out 40 years of lessons learned in creating good software, so we can pump out code quickly. When the disastrous breach or the project collapse inevitably happens, the programmers and project managers who created the awful code will have almost surely moved on. So yes, give us the Go hammer, so we can quickly bang at all the nails.

## FP for the Unprincipled
While the ultimate measure of a successful software project is the agile definition _working code that meets customer needs_, excellent systems are also reliable (safe, secure, consistent) and maintainable (easy to change, easy to bring on new team members). We all know that many (perhaps most) software systems are the opposite of that! Formal thinking using pure FP helps us not only with reliability but also maintainability, and so serves as an important and useful tool for helping us programmers create excellent software. 

So how do we encourage programmers and project managers to use FP (and other “hard”) tools to become better at our craft? There are three methods that behavioral economics teaches us we can use to change human behavior: persuasion, education, and choice architecture. 

Let’s start with persuasion. The original Tweet that started this rant, had a correct intuition that pure FP has to be “marketed”. The problem is that pure FP proponents are terrible at marketing. I have often heard as part of conference talks, pure FP referred to as _principled_ or even _ethical_, seemingly implying that the rest of us programmers who don’t use pure FP are unprincipled and perhaps even unethical! Even the term _purity_ can be off-putting. Layer on top the terminology being thrown around in discussions of pure FP—functors, monads, monoids, Kleisli, etc.—and you can see why FP proponents sound like real snobs in an elite club that the _hoi polloi_ of programmers will never, ever, be able to join.

I stress that I use the phrase “sound like” because in reality, almost all the people I have encountered in the pure FP community are the opposite of snobs. They genuinely want more people to join them in using pure FP and are eager to teach people what it is, and how and why to use it. And they put their money where their mouth is. They spend enormous amounts of personal time developing FP tools and frameworks and hours on Gitter and other forums voluntarily teaching people how to do pure FP. All of them, especially the ones I had the Gitter/Twitter discussions with, are people I highly respect and admire for their enormous contributions to the Scala/Scala FP ecosystem

Unfortunately what many of them don’t seem to realize or accept is that semantics _do_ matter. How you “anchor” what you are “selling” has a huge impact on how easy it is to sell. By saying 99% of programmers are not yet in this “market”, you end up excluding, not enticing, that 99%.

It is not my place to tell other people how to spend their time. So I certainly can’t ask FP proponents to be more generous of their time or more tolerant of novices. However, to those who are already being generous and who obviously feel leading more people to the FP promised land is a worthwhile endeavor, I do feel comfortable giving some advice.

Avoid language that sounds like you are judging other people, even if that is not your intention. Sure the terms “pure” and “principled” are not referring to character, but to mathematical aspects of the concepts. But your uninitiated audience won’t understand that. Ban “ethical” and “principled”  and perhaps even “pure” from your lexicon. Reserve terms like “unprincipled” and “unethical” for when you are talking about programmers who, for example, help companies like VW or Uber cheat!

On the positive side, work on broadening the tent of functional programming. Sure FP is not simply pipelines, and pipelines are not necessarily FP. But thinking of FP in its broadest sense, allows you to point out to programmers that they have likely already taken their first steps into the FP world. People often joke that Scala is a “gateway drug” to Haskell. Leverage that idea to persuade people FP really isn’t that scary. 

Using _Option_ or _Either_ or _for comprehensions_ or pipelines may be just baby steps in the big FP picture. But those steps can be a springboard to persuading programmers that FP is worthwhile and can be usefully applied even before you fully understand it. They also provide simple examples that can help in educating novices.

Which is a good segue into the topic of education. Currently there aren’t enough resources for _novices_ to help us wrap our head around pure FP.  The people in the vanguard of adopting pure FP are the smartest programmers out there. Very smart people often have great difficulty being able to get down to the level of the rest of us. Moreover many of the smartest people are busy doing FP, not necessarily teaching it. 

Fortunately, precisely because the vanguard are so generous with their time, more and more learning resources for explaining pure FP are being developed—books, articles, blog posts, conference talks etc. More of those have to be targeted at novices, beginners and even intermediate learners.

FP proponents correctly argue we can’t use just any words to describe formal FP concepts. Fuzzy terminology will lead to fuzzy thinking and will do more harm than good. But if you want to get people to reach a precise understanding, you have to build up with layers of examples and simpler concepts. Along the way, you have to be tolerant of fuzzy thinking. Foster intuitions to get people to understand the definitions. 

Try to build off of concepts and intuitions that your novice FP programmer might already have. Don’t talk down, but do bring down your language to simpler terms, when you want to reach a wider audience. Remember, there are lots of holes in people’s knowledge (particularly in the underlying math concepts) so don’t assume they already know the basics. Repetition doesn’t hurt. Also don’t forget that there is a far larger audience of novices out there, than experts. Try to step back to help lead them along into the tent.

A great example of someone taking many of the above points into consideration, is [this presentation][4] by Rob Norris. It was extremely helpful to me in making more intuitive the difference between effects and side effects, and what these thingees called monads, applicative etc. are all about. Watching it, I had more than one “a-ha” moment. It’s still a bit complex and many points went over my head, but that was more a result of the limited time available. 

Finally, we come to choice architecture, which essentially is about making it easier for people to choose doing the right thing. One of the best ways to get programmers to adopt good programming paradigms and practices is to build a development process that focuses on/values code quality, over code and feature quantity. The fact that the guy who wrote that blog post on “Go vs Scala” brags about doing the opposite, shows how this type of process is not as prevalent as it should be. 

Ultimately, the best incentive for programmers is providing them tools that makes for less work and more play. The more programmers use FP, the more they learn that it actually reduces the time they have to spend coding, testing and debugging.  So gently encouraging programmers to go down the FP path (instead of chastising them) will itself create a positive, virtuous circle.

In any case, we shouldn’t despair. It took years for structured programming and then OOP to take root. If FP is as advantageous as we believe it to be, in time it too will take a respected place in the programmers standard toolkit.

[1]:	../functional-programming-for-the-unprincipled-1
[2]:	https://movio.co/en/blog/migrate-Scala-to-Go/
[3]:	http://yager.io/programming/go.html
[4]:	https://www.youtube.com/watch?v=po3wmq4S15A&feature=youtu.be