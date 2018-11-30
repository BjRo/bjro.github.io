---
title: On adaptive Software Design
---
I've participated in efforts to deliver software for more than 15 years now. The first five using the good old waterfall approach with infrequent, big releases; the last 10 years in teams that followed one of the flavors of the agile method. 

Some of the teams I was working on were using `Scrum`. Others used `Kanban`. Some used a mixture of both. The worst application of the agile method I encountered in the last 10 years (and probably the most common one) is what I would generally describe as `Agile without a soul` or like Martin Fowler calls it [faux-agile](https://martinfowler.com/articles/agile-aus-2018.html). You know, the version that heavily focuses on the prescriptive process portions; which has teams whose members don't meet on eye level because the Product Owner actually turns out to be a manager in disguise; where removal of impediments and/or continuous improvement is seen similarly often as unicorns. The only thing that does turn out to be continuous is the nagging sentiment in higher management levels that "This Agile thing is fraud/doesn't deliver what it promises/hurts us more than it actually helps". 

> Well at least with the capital A version of agile, they might have a point

But guess what, I've seen those unicorns. And I've seen them more than once. Highly productive, self organized software engineering teams, that constantly inspect and adapt how they're delivering software. Teams that are conscious of the value that they provide to others, that collaborate closely with their stakeholders to deliver high quality results in a given time-frame. I still consider myself a believer in what slowly is somehow becoming similar to Voldemort (he who should not be named, for you non Harry Potter folks). 

If you now got the impression that this is going to be an epic post about how to do agile "the right way", I have to disappoint you. That's not going to be what I would like to talk about today. I doubt that there is "the right way". It all depends on context. And even if we accept that, I think it's still a big hairy audacious goal to describe how to be agile in all its intricacies. Because of that I would like to talk about something much simpler today. Something that is often overlooked when trying to deliver software in an agile way: The frickin technical and semi-technical stuff that supports you being agile. 

And I don't want to approach this in an abstract way, but reflect a bit on what we actually did for our `XING One` project. Especially the things I look back to thinking "Yeah, that was a good idea and saved our back more than once". So let's have a look at those.

# 1. Coding with the right mindset
You can go into a new software adventure with the "I'm going to rock this" attitude. Especially if you're coming from other successful stints or projects and are highly confident in your capabilities. Or you can choose to be a bit more humble. You can accept that you're not perfect, that you're going to make mistakes and some sub-optimal decisions along the way and prepare that these are moderately easy, cheap and fast to fix. That was more our stance with `XING One`. 

Just to give you some idea what we had to correct during our first year:

* We completely ripped out our first `REST` client (based on `akka-http`) and replaced it with Twitters `Finagle` (because our application was dying in overload scenarios and profiling pointed to `akka-http`)
* The HTTP layer itself was refactored and revised multiple times to adapt to new requirements that were introduced with new capabilities (primarily caused by new custom `SDL` directives)
* We had to replace the `JSON` library we were initially using (`json4s`) because we learned at some point in the project while profiling large `GraphQL` queries, that the `JSON` library we used implemented key lookup on top of a list (e.g. the larger the `JSON` document that was selected from, the longer the key lookup would take)
* The metadata layer was refactored numerous times (we convert a lot of the `SDL` directives into `Sangria` `FieldTags` which then control the execution in the execution layer) 

and probably some more changes that I don't remember off the top of my head right now. What I want to say is this: Even though our outside `GraphQL` server interface didn't change much over the course of the first year, the internals were constantly revised, rewritten and improved, on a system that after 6 month had already real production traffic and real users on it.

# 2. Changes need to be cheap and with low coordination overhead
I'm repeating myself here, but I want to emphasize the point. If you can't change your software fast and in a fairly cheap manner, you will have a hard time trying to work with agile and iterative product development. The ability to pull of refactoring with confidence, low ceremony and fairly low effort is key to a successful agile implementation. Move fast and break things sounds super sexy until you actually start breaking things and turn your users against your product. Your product customers like when things are predictable and they've got a feeling of certainty the product.

So how do you bring those two together? In retrospect I think 3 things helped us quite a lot with `XING One`

- Static typing
- Having a good testing story
- Using a mono repository for `XING One`

## Static typing
I'm not going to rant on dynamically typed languages here, but I prefer static styping once the codebase has reached a certain size and 

My employer has a long history with dynamically typed languages, such as `Ruby` and `Perl`. Before joining `XING` I was mostly doing `C#` and using `Visual Studio` with `Jetbrains Resharper`. In the early days of working with `XING` I was primarily developing `Ruby` (later `Elxir` applications) using commandline tools and `Vim`. 



While I always enjoyed the initial coding experience in `Ruby` (and `Rails` for that matter) and still use `Ruby` for quickly hacking stuff together, refactoring a large `Ruby` codebase is one of those particular things that I 


. Ok, "nightmare" is probably a bit drastic, but it never came close to the experience and confidence in refactorings I knew from the old `C#` days. The reason for this varies:

* The obvious one is the lack of good tooling for refactoring, that often causes refactorings ending up to be search and replace
* More often than not you found a code path that wasn't properly covered by tests during refactoring
* Either the code was extensively using mocking or stubbing (and thus often required a rewrite of tests when refactoring the actual code) or 

## Stable tests

## Using a mono respository