---
title: Regarding that A**** thing
---
I've participated in efforts to deliver software for more than 15 years now. The first five using the good old waterfall approach with infrequent, big releases; the last 10 years in teams that followed one of the flavors of the agile method. 

Some of the teams I was working on were using `Scrum`. Others used `Kanban`. Some used a mixture of both. The worst application of the agile method I encountered in the last 10 years (and probably the most common one) is what I would generally describe as `Agile without a soul` or like Martin Fowler calls it [faux-agile](https://martinfowler.com/articles/agile-aus-2018.html). You know, the version that heavily focuses on the prescriptive process portions. Which sometimes has teams whose members don't meet on eye level because the Product Owner actually turns out to be a manager in disguise, othertimes has developers that don't care at all about business outcomes but celebrate technical excellence to the deatch, often in places where it doesn't really matter. Where removal of impediments and/or continuous improvement is seen similarly often as unicorns. The only thing that does turn out to be continuous is the nagging sentiment in higher management levels that "This Agile thing is fraud/doesn't deliver what it promises/hurts us more than it actually helps". 

> Well at least with the capital A version of agile, they might have a point

But guess what, I've seen those unicorns. And I've seen them more than once. Highly productive, self organized software engineering teams, that constantly inspect and adapt how they're delivering software. Teams that are conscious of the value that they provide to others, that collaborate closely with their stakeholders to deliver high quality results in a given time-frame. I still consider myself a believer in what slowly is somehow becoming similar to Voldemort (he who should not be named, for you non Harry Potter folks). 

If you now got the impression that this is going to be an epic post about how to do agile "the right way", I have to disappoint you. That's not going to be what I would like to talk about today. I doubt that there is "the right way". It all depends on context. And even if we accept that, I think it's still a big hairy audacious goal to describe how to be agile in all its intricacies. 

Because of that I would like to talk about something much simpler today. Something that is often overlooked when trying to deliver software in an agile way: The frickin technical and semi-technical stuff that supports you being agile. And I don't want to approach this in an abstract way, but reflect a bit on what we actually did for our `XING One` project. Especially the things I look back to thinking "Yeah, that was a good idea and saved our back more than once". So let's have a look at those.

# 1. Coding with the right mindset
You can go into a new software adventure with the "I'm going to rock this" attitude. Especially if you're coming from other successful stints or projects and are highly confident in your capabilities. 

Or you can choose to be a bit more humble. 

You can accept that you're not perfect, that you're going to make mistakes and some sub-optimal decisions along the way, that requirements likely will change in an unforeseen way and that new opportunities may arise that you would like to follow-up on. 

If you accept that as a starting point, my personal standpoint is that you look at your technical software and your setup differently. That was more our stance with `XING One`. 

Just to give you some idea what we had to correct during our first year:

* We completely ripped out our first `REST` client (the HTTP layer talking to the internal APIs, based on `akka-http`) and replaced it with Twitters `Finagle` (because our application was dying in overload scenarios and profiling pointed to `akka-http`)
* The HTTP layer itself was refactored and revised numerous times to adapt to new requirements that were introduced with new capabilities (primarily caused by new custom `SDL` directives)
* We proactively replaced the `JSON` library we were initially using (`json4s`) after we had been live for several months, because we learned at some point in the project while profiling large `GraphQL` queries, that the `JSON` library we used implemented key lookup on top of a list (e.g. the larger the `JSON` document that was selected from, the longer the key lookup would take)
* The metadata layer was refactored numerous times (we convert a lot of the `SDL` directives into `Sangria` `FieldTags` which then control the execution in the execution layer) 
* We switched how you would extend `XING One` from using a `Scala DSL` to `SDL` after 10 months, once we were sure that this would work
* We changed the way how you'd call from SDL into native `Scala` function at least twice

and probably some more changes that I don't remember off the top of my head right now. 

What I want to say is this: Even though our outside `GraphQL` server interface didn't change much over the course of the first year, the internals were constantly revised, rewritten and improved, on a system that after 6 month had already real production traffic and real users on it.

# 2. Use an refactoring friendly language stack
I'm repeating myself here, but I want to emphasize the point. If you can't change your software fast and in a fairly cheap manner, you will have a hard time trying to work with agile and iterative product development. The ability to pull of refactoring with confidence, low ceremony and fairly low effort is key to a successful agile implementation. Move fast and break things sounds super sexy until you actually start breaking things and turn your users against your product. Your product customers like when things are predictable and they've got a feeling of certainty the product. Your boss probably, too .... and wait ... I guess you as well. So make sure that you can refactor with ease.

There are different opinions on what makes a codebase easy to refactor out there. Dynamic typing advocates usually mention that you have less code to work with and less abstractions that you need to deal with, that it's faster because the compiler is usually slow. People from the static typing camp usually bring up the better tool support and that the compiler does a great job for you (whose absence you have to compensate in dynamic languages for instance by writing more tests).

I've build production systems in `C#`, `Ruby`, `Elixir` and `Scala` now, with a bit patching and bug-fixing in `Objective-C`, `Perl` and `Erlang` sprinkled in. So compared to a lot of people out there who have strong opinions regarding this, I can at least say that I spend significant time in each technology to feel its benefits and downsides first hand. I always liked the feeling of speed that you have when you're working on a new `Ruby` or `Rails` codebase. But I also have to admit that working on large `Ruby` codebases, at least for me, was almost always outside the fun category. And refactoring `Ruby` applications even today ends up with a glorified 'search and replace' and 'fingers crossed that you found all references' (yes, I've also tried `Rubymine` and didn't see a lot of improvements there).

Once a codebase has reached a certain size I can definitely see a lot for value in static typing. Having `Resharper` in `C#` or `IntelliJ` in `Scala` at your disposal for me makes one hell of a difference. And I also think a good refactoring tool changes the way you work. You rename more often and you move stuff around more often. You can easier check where code is actually used in the codebase. And much much more.

# 3. Throw out refactoring unfriendly language features


# 4. Actual unit tests

# 5. Use a mono repository 