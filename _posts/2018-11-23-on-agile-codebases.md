title: On agile codebases
---
I've participated in efforts to deliver software for more than 15 years now. The first five using the good old waterfall approach with infrequent, big releases; the last 10 years in teams that followed one of the flavors of the agile method. 

Some of the teams I was working on were using `Scrum`. Others used `Kanban`. Some used a mixture of both. The worst application of the agile method I encountered in the last 10 years (and sadly the most prominent one) is what I would generally describe as `Agile without a soul`, or as Martin Fowler calls it [faux-agile](https://martinfowler.com/articles/agile-aus-2018.html). You know, the version that heavily focuses on the prescriptive process portions. Which sometimes has teams whose members don't meet on eye level because the Product Owner actually turns out to be a manager in disguise, othertimes has developers that don't care at all about business outcomes but celebrate technical discussions about `KISS`, `DRY` and friends to the death, often in places where it doesn't really matter. 

> To be fair, I've been guilty of those discussions in the past as well :)

Maybe you know those kind of teams I'm talking about. Teams were removal of impediments and/or real continuous improvement is seen similarly often as unicorns. The only thing that does turn out to be continuous is the nagging sentiment in higher management levels that "This 'agile' thing is fraud / doesn't deliver what it promises / hurts us more than it actually helps". 

But guess what, I've seen those unicorns. And I've seen them more than once. Highly productive, self organized software engineering teams, that constantly inspect and adapt how they're delivering software. Teams that are conscious of the value that they provide to others, that collaborate closely with their stakeholders to deliver high quality results in a given time-frame. I still consider myself a believer in what slowly is somehow becoming similar to Voldemort (he who should not be named, for you non Harry Potter folks). 

If you now got the impression that this is going to be an epic post about how to do agile "the right way", I have to disappoint you. That's not going to be what I would like to talk about today. I doubt that there is "the right way", it all depends on context. And even if we accept that, I think it's still a big hairy audacious goal to describe how to be agile in all its intricacies. 

So, after bailing out on that, I would like to talk about something much simpler today. Something that is often overlooked when trying to deliver software in an agile way: Technical and semi-technical stuff that might help you being agile. And I don't want to approach this in an abstract way, but reflect a bit on what we actually did for our `XING One` project. Especially those "Yeah, that was a good idea", "saved our back more than once" or "would do that again" stuff. 

So let's have a look at those.

# 1. Coding with the right mindset
You can go into a new software adventure with the "I'm going to rock this" attitude. Especially if you're coming from other successful stints or projects and are highly confident in your capabilities. 

Or you can choose to be a bit more humble. 

You can accept that you're not perfect, that you're going to make mistakes and some sub-optimal decisions along the way, that requirements likely will change in an unforeseen way and that new opportunities may arise that you would like to follow-up on. If you accept that as a starting point, I believe that you look at your software and your setup differently. Consequently this was pretty much our stance with `XING One`. 

Just to give you some idea what we had to correct during our first year:

* We completely ripped out our first `REST` layer (the HTTP layer talking to the internal APIs, based on [akka-http](https://doc.akka.io/docs/akka-http/current/)) and replaced it with [Twitters Finagle](https://twitter.github.io/finagle/) (because our application was dying in overload scenarios and profiling pointed to `akka-http`)
* The HTTP layer itself was refactored and revised numerous times to adapt to new requirements that were introduced with new capabilities (primarily caused by new custom `SDL` directives)
* We proactively replaced the `JSON` library we were initially using ([json4s](http://json4s.org/)) after we had been live for several months, because we learned at some point in the project while profiling large `GraphQL` queries, that the `JSON` library we used implemented key lookup on top of a list (e.g. the larger the `JSON` document that was selected from, the longer the key lookup would take)
* The metadata layer was refactored numerous times (we convert a lot of the `SDL` directives into `Sangria` `FieldTags` which then control the execution in the execution layer) 
* We switched how you would extend `XING One` from using a `Scala DSL` to `SDL` after 10 months, once we were sure that this would work
* We changed the way how you'd call from `SDL` into native `Scala` function at least twice

and probably some more changes that I don't remember off the top of my head right now. 

What I want to say is this: Even though our outside `GraphQL` server interface didn't change much over the course of the first year, the internals were constantly revised, rewritten and improved, on a system that after 6 month had already real production traffic and real users on it.

# 2. Use an refactoring friendly language stack
I'm repeating myself here, but I want to emphasize the point. If you can't change your software fast and in a fairly cheap manner, you will have a hard time trying to work with agile and iterative product development. The ability to pull of refactoring with confidence, low ceremony and fairly low effort is key to a successful agile implementation. Move fast and break things sounds super sexy until you actually start breaking things and turn your users against your product. Your customers actually like when your application behaves predicatably. Your boss probably too .... and wait ... I guess you as well. So make sure that you can refactor with ease.

There are different opinions on what makes a codebase easy to refactor out there. Dynamic typing advocates usually mention that you have less code to work with and less abstractions that you need to deal with, that it's faster because the compiler is usually slow. People from the static typing camp usually bring up the better tool support and that the compiler does a great job for you (whose absence you have to compensate in dynamic languages for instance by writing more tests).

I've build production systems in `C#`, `Ruby`, `Elixir` and `Scala` now, with a bit patching and bug-fixing in `Objective-C`, `Perl` and `Erlang` sprinkled in. So compared to a lot of people out there who have strong opinions regarding this, I can at least say that I spend significant time in each technology to feel its benefits and downsides first hand. 

I always liked the feeling of speed that you have when you're working on a new `Ruby` or `Rails` codebase. But I also have to admit that working on large `Ruby` codebases, at least for me, was almost always outside the fun category. And refactoring `Ruby` applications even today ends up with a glorified 'search and replace' and 'fingers crossed that you found all references and/or everything is well covered by tests' (yes, I've also tried `Rubymine` and didn't see a lot of improvements there).

Once a codebase has reached a certain size I can definitely see a lot for value in static typing. Having `Resharper` in `C#` or `IntelliJ` in `Scala` at your disposal for me makes one hell of a difference. And I also think a good refactoring tool changes the way you work. You rename more often and you move stuff around more often. You can easier check where code is actually used in the codebase. And much much more.

`Scala` for me with `Intellij` fits well into this category, but it's not without it's caveats.

# 3. Throw out refactoring unfriendly language features
There is `"A better Java" - Scala` and there's `"I'd rather do Haskell but I'm stuck with this" - Scala`. The latter comes with one of the most refactoring unfriendly features I have actually seen in a static language, `implicts`. Not only do they slow down your IDE quite dramatically, they also cause puzzling looks on developers faces, when somebody removes an "import" by accident and the application doesn't compile anymore. 

You certainly can do cool things with them (Typeclasses anyone?), but I don't think `implicts` are worth the cost. Especially when you know that you want to rely on refactoring capabilities a lot. 

# 4. Remove unnecessary discussions about code style and conventions
Debates about code style are lovely time-sinks and I'm super grateful for the development of the recent years that brought more and more tools into the various tech stacks that do automated code formatting, based on some agreed upon time conventions. I'm not sure where it originated, but I think [gofmt](https://golang.org/cmd/gofmt/) started this. I definitely appreciate the idea. Consequently we relied on [scalafmt](https://scalameta.org/scalafmt/) from day one and since that day it's automatically ensuring that all our contributions are in a similar format. 

We also had fairly conservative [Scalastyle](http://www.scalastyle.org/) checks in place early on. `Scala` gives you many options on how to write your code (ranging from `obj.method()` to `obj function`). While I like the idea of the "scalable programming language", having multiple of those styles mixed together in one application, makes it more confusing to work with the code in a team and creates unnecessary distractions. Also here we favored the boring solution of `obj.method()` over the more functional syntax.

# 5. In-memory integration tests yield the most bang for the buck 
One thing that I've seen many teams struggle with that embraced automatic testing, is finding the right testing approach that brings not only safety, but also speed and confidence. Similar to agile, I think you can see quite a bit of cargo culting in the automated testing area. 

Don't get me wrong, automated tests are an essential part of everything I've done in the last years, but somehow more often than not when I look into different teams codebases, the typical setup falls into one of two categories:

1. Heavy focus on integration tests, that are usually slow, often you don't know 

The primary sin I've seen, is that tests are usually too much coupled to the implementation so that when the implementation changes the tests need to be completely rewritten. Usually those codebases made extensive use of mocks or stubs and similarly often they test things on multiple levels again and again. 

The strategy we chose may not be applicable for other contexts, but it served us very well. In a nutshell we use a multi-layered test strategy consisting out of 

* unit tests (for functionality that can easily be tested in isolation, e.g. verification of signatures, decomposing a cookie, etc.), 
* in-memory integration tests (running a full `GraphQL` engine against a stub `HTTP` backend)
* and end to end integration tests (running the actual server against a sandboxed version of the `XING` platform).

I would specifically like to elaborate on the middle strategy here, the in-memory integration tests. These are in my opinion our most important tests and are fully used to describe what our `GraphQL` servers capabilities and behavior. 

Tests typically follow the following format:

1. Given a `GraphQL` engine with the following middlewares configured
2. Given the following schema definition
3. Stubbing the following HTTP requests (Optional)
4. When I run the following query 
5. It should 
6. It should produce the following result

TODO: Simple example

```scala
```

# 6. Re-use your benchmarks
# 6. Use a mono repository 