---
title: On adaptive Software Design
---
I've participated in efforts to deliver software for more than 15 years now. The first five using the good old waterfall approach with infrequent, big releases; the last 10 years in teams that followed one of the flavors of the agile method. 

Some of the teams I was working on were using `Scrum`. Others used `Kanban`. Some used a mixture of both. The worst application of the agile method I encountered in the last 10 years (and probably the most common one) is what I would generally describe as `Agile without a soul` or like Martin Fowler calls it [faux-agile](https://martinfowler.com/articles/agile-aus-2018.html). You know, the version that heavily focuses on the prescriptive process portions; which has teams whose members don't meet on eye level because the Product Owner actually turns out to be a manager in disguise; where removal of impediments and/or continuous improvement is seen similarly often as unicorns. The only thing that does turn out to be continuous is the nagging sentiment in higher management levels that "This Agile thing is fraud/doesn't deliver what it promises/hurts us more than it actually helps". 

> Well at least with the capital A version of agile, they might have a point

But guess what, I've seen those unicorns. And I've seen them more than once. Highly productive, self organized software engineering teams, that constantly inspect and adapt how they're delivering software. Teams that are conscious of the value that they provide to others, that collaborate closely with their stakeholders to deliver high quality results in a given time-frame. I still consider myself a believer in what slowly is somehow becoming similar to Voldemort (he who should not be named, for you non Harry Potter folks). 

If you now got the impression that this is going to be an epic post about how to do agile "the right way", I have to disappoint you. That's not going to be what I would like to talk about today. I doubt that there is "the right way". It all depends on context. And even if we accept that, I think it's still a big hairy audacious goal to describe how to be agile in all its intricacies. Because of that I would like to talk about something much simpler today. Something that is often overlooked when trying to deliver software in an agile way: The frickin technical stuff that supports you being agile. And I don't want to approach this in an abstract way, but reflect a bit on what we actually did for our `XING One` project. Especially the things I look back to thinking "Yeah, that was a good idea and saved our back more than once"

# Code with the right mindset
It's probably a minor thing, but I think it's still worth pointing out. You can go into a new software adventure with the "I'm going to rock this" attitude. Especially if you're coming from other successful stints or projects and are highly confident in your capabilities. Or you can choose to be a bit more humble. A more healthy, realistic alternative to this is to accept that mistakes and some sub-optimal decisions are going to happen and to prepare that these are moderately easy to fix and aren't costly. That was more our stance with `XING One`. 

Just to give you some idea what we had to correct during our first year:

* We completely ripped out our `akka-http` based `REST` client and replaced it with Twitters `Finagle`
* The HTTP layer itself was refactored multiple times to adapt to new requirements that were introduced with new `SDL` directives
* We had to replace the `JSON` library we were initially using (`json4s`) because we learned at some point in the project while profiling large `GraphQL` queries, that the `JSON` library implemented key lookup on top of a list (e.g. the larger the `JSON` document that was selected from, the longer the key lookup takes)
* The metadata layer was refactored numerous times (we convert some of the directives into `Sangria` `FieldTags`) 

# Refactorings need to be cheap and with low coordination overhead
# Mono-repo
# A good testing story
# Be conscious about your interfaces to the outside world
# Stick with what you know