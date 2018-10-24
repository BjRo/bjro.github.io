---
---
When I try to trace back why I think `GraphQL` is a good fit for us, I always end up somewhere in the years 2012, 2014 and 2016. Apologies upfront, this is going to be a long one.

# 2012
In 2012 I started working for `XING` in the API - team. Together we launched `XING`s public `REST` API that same year. The infrastructure for that had already been in place for roughly two years (I think) and was also the data source for `XING`s own native mobile applications. In fact many of the APIs that you would find later in the public `REST` API originated in the context of those applications and at least for a short time there was a 100% overlap between the public API and what the mobile apps were using. 

One thing we already had at that time was a query parameter called `fields` on the users API and `user_fields` on every API that was referencing users. These query parameters expected a comma separated list of field names and if you would call the API that way, you'd only get back what you had requested. It even supported nesting so you could request `business_address.city` to only get the city portion of the business address. If you look at it now from a `GraphQL` perspective, you might think "wait a minute, that sounds almost like a mini selection set" and I think this isn't too far off. It had the same benefits (tracking, e.g. who is using what and bandwidth optimization, e.g. only transfer what the client actually needs) but obviously ours was a very simple, poor mans version of the idea.

Unfortunately, driven by the overarching goal to make things as straightforward to use as possible, the team looked at this only as an optimization. If you didn't specify the fields, you would get everything. I bet you can already guess what happened: While our mobile applications made good use of this, most of the other consumers of the public API didn't, which kinda neglects at least the transparency benefit.

Talking about change, I think there's a field of tension if you're attempting to re-use a public API for your mobile applications (or the other way around) like we did. Good public APIs are like a promise of stability. They change very infrequently. You can rely on them and build solid, long living integrations on them. And judging from my experience, it takes significant time to design them that way. 

On the other end of the spectrum are your own mobile applications where you (or at least the company) more often than not want to iterate fast, get features out as fast as you can and learn based on actual usage. These two things were always at odds at the time. Often the desired change some of our product teams wanted to make wasn't easily possible without breaking exising consumers of the public API, or introducing some kind of versioning which we tried not to do at the time (since we just had come out with the v1 of the API). 

> Side joke: Guess what the version number of the public API is in 2018?

Usually we would end up with either additional API calls to get the necessary data or adding the necessary data to existing APIs. The former with the downside of complicating life for the frontend people (request coordination, timeouts and partial results where one API succeeded while the other didn't) and the latter with delivering data to consumers that they didn't need and would simply throw away.

> This is usually the spot where somebody from the internet storms in and points out in good old [Kevin Sorbo style](https://www.youtube.com/watch?v=9JymfHFTLUg) that "this ain't REST !!!". Congrats, you're correct. Like most people at the time we were labeling our API as `REST` even though what we actually had (also like most people :)) was just a good old CRUD API implemented with `HTTP` and `JSON`. Let's move on, shall we?

But we did have a lot of talks about the "real `REST`", this elusive unicorn. My colleagues from that time can probably acknowledge that I in particular might have been pretty much a pain in the ass about that one, at least for some time. Like many people at the time I've read Fieldings thesis and the few available books for that topic. I was exited about it because it seemed to offer a way out of the coupling problems we experienced with our API consumers (if the client played by the rules). 

Whenver I tried to convince my peers though, the exitement grinded to halt in record time. Discussions usually ended with blank stares, when we came to the point clients had to do in order to make the `Hypermedia` game work. 

> ME: So, what do you think about that?

> MOBILE DEV: .... (silence) .... (more silence) ...

> API DEV COLLEAGUE: ... "So, you kinda want him to turn our mobile app into a browser?"

> MOBILE DEV: ... "Listen, I just want to get some data ..."

Remember part of the teams mission statement was to make the APIs as easy and self explaining as possible. Having an additional protocol in between wasn't on the "hot things" list. At the time this frustrated me, but with some distance I have to admit, they probably had a point. Part of their non-enthusiasm for the idea boiled down to the fact that there wasn't (and to my knowledge still isn't) a widely adopted standard (at least if you exclude HTML) with good tooling and library support in multiple programming languages. Everything would need to be created from scratch by us. 

Ultimately this experience made me realize that whatever solution might appear in the future that would improve the API game for mobile applications, it would be one with a very good developer experience and strong, multi platform tooling support.

# 2014
Between 2012 and 2014 something interesting happened somwhere else inside `XING`. When I started in the company in 2012, the majority of the developers was still working in one of two monolithic applications. One being written in `Perl` (the original `OpenBC`) and another one in `Ruby on Rails` (containing all recent developments). 

#TODO: insert picture here

But a larget project had been already started by the Architecture team to break apart the `Rails` monolith and introduce `HTTP+JSON` APIs in between. `XING` was already experiencing the first wave of organisational growth challenges and the platform architecture moved into the direction of something akin to a service oriented architecture. With that timeouts, concurrency and partial results also became something to deal with for the backend applications. 

#TODO: insert picture here.

I had moved on from the API team and after a short stint working on our hybrid `iPad` application, I found some new interesting challengines in the Architecture team. Even though it was not my responsibility anymore, the API topic never really let go of me and I kept constantly wondering about a better solution.

Another trend in 2014 emerged: Mobile first. And with that the development resources for the native mobile applications were heavily scaled up. What became obvious pretty fast was that the API team, as the primary data source for the mobile applications, became an organisational bottleneck, because more and more teams were waiting for new APIs to appear. It was a classic `Littles Law` effect. Demand went up, capacity stayed the same and waiting queues started to form. The organisation didn't take long to react and somewhere during 2014 we made the decision to distribute the responsibilities for building the mobile APIs to all backend applications. The infrastructure for the public API was again re-used and became a proxy that was dealing with authentication and ratelimiting. The actual business logic resides in the connected APIs.

#TODO: insert picture here

We lost some features along the way (the mentioned `fields` / `user_fields` being one of them), but this change allowed teams to break out of the public API conventions. Some teams experimented with new forms of APIs, screen based ones. We didn't call it that way but I think later the same idea was coined `Backends For Frontends` or just `BFF`. The idea with `BFF` in the mobile case being that request coordination closer to the APIs reduces the likelyhood of partial results and that performance shortcomings could be easier addressed in the backend. 

In general this change was perceived well at the time. But trouble was already showing up on the horizon. These freedoms were a double edged sword. Using different APIs with different concepts was not always considered as a win by mobile developers. Turns out they actually like the consistency the old public API was giving them. Even worse, since now everyone was building APIs (mostly in untyped languages), even more inconsistencies started to creep in that drove some people nuts. For example dates in one API were expressed as `iso8601` strings, in a different one as `seconds from epoc` and in a third one as a `JSON` object with `day`,`month`, etc fields.

# 2016

# So why GraphQL?