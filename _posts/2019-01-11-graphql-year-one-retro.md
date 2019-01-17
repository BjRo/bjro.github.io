A belated happy new year everyone! I hope everyone of you had a good start into the new year. Todays post is going to be of a different kind compared to the [rest of the the series so far](/per-aspera-ad-astra/). In the last posts I talked in depth about the "why?", the initial project decisions and the preparations we took to ensure that we'd be able to deliver on our promise. But I haven't yet talked about our actual experience of introducing `GraphQL` into our organization. 

At the end of the first year (2017) our initiative was already seen as a big success and it continued to thrive in 2018 (though slower than in 2017, mostly for reasons that were outside of our control). Most of the benefits we expected from `GraphQL` also turned out to be true. It's quite eye opening to see colleagues play with `GraphiQL` (or later `GraphQL Playground`) for the first time. Pretty much all of them instantly realize (positive) impact this could have one their work and the rest of the organization around them.

But it's not all roses. In 2018 you can find an ocean full of resources about why `GraphQL` "is the new sexy", "superior to REST", "to REST what REST was to SOAP" and in general "the best next thing after slided bread". In order to have a meaningful discussion about a technology though, I believe that we also need to be open about shortcomings of `GraphQL`, our surprises along the way and also specifically the mistakes we made along the way. Only then can we have a more balanced view of a technology. 

To give you some context about the company I'm working in (and that is worth understanding before going into the individual points): 

* XING has roughly __1,3k employees__ of which __~300 are developers__ 
* Of these to my knowledge roughly __70 are native mobile developers__ 
* For the rest I don't have concrete numbers, but my feeling is that it's roughly __2/3 backend developers__ and __1/3 web frontend developers__. 
* Most of the engineering teams at XING are setup to build __all representations of their product__ (backend, ios, android & web)
* In comparison the teams that are dealing with cross cutting concerns like "the platform" are fairly small. 
  * The system architecture team (which primarily is concerned with running our `PAAS` platform based on `Kubernetes` these days) is __~10 people__. 
  * My team that was pushing the `GraphQL` initiative used to be __4 people in 2017 and 2018__ (and we also had to maintain our OAuth gateway on the sidelines).
* In general, XINGs engineering organization tries to give a lot of freedom and autonomy to the individual teams. As a consequence there's always the lingering pressure for infrastructure related teams to [find ways to do their work without interrupting or even blocking product teams](TODO: LINK) and as a consequence a lot of the larger technology initiatives by their nature need to be incremental and non-blocking in how they're rolled out.

That being out of the way, let's dive into our findings from year one (2017):

# 1. Expectations on GraphQL vary dramatically between web and native mobile developers
If you trace back the `GraphQL` story back to its beginning within `Facebook` you realize that it originated from a mobile background and then expanded further into the company. Basically what happened is that some pretty clever people build the first version of the concept for the new, native mobile newsfeed. That was when `Facebook` was still primarily following their `HTML5` approach within their mobile applications. When the decision was made to switch the strategy to go all in on native development instead of web technology, it was a combination of "having a great, working concept" and "being at the right spot, at the right time". They pretty much created the blueprint for things to come. `GraphQL` didn't start out on the web or even `Javascript` side. I believe the original `GraphQL` server was and is still written in `Hack`. Only when they came to the conclusion that "this could really be a thing", they created the spec and the reference implementation in `Javascript`. But this happened at a later point. 

> In case you wondering: In 2017 I sat next to [Dan Schaefer](https://twitter.com/dlschafer) in the cab on the way to the speakers dinner for the `GraphQL EU` conference and had the chance to pester him with all sorts of questions. Dan is one of the original `GraphQL` creators (besides [Nick Schrock](https://twitter.com/schrockn) and [Lee Byron](https://twitter.com/leeb)).

Now fast forward to `2017`. The `GraphQL` buzz primarily happened on the web side and in the `Javascript` world. The rise of `React` coupled with the fact that the company behind [`Meteor`](https://www.meteor.com/) joined-in and heavily invested into the `GraphQL` ecosystem might have played a part in that. Now they're more well known as [`Apollo`](https://www.apollographql.com/). What was mostly absent in the buzz interestingly was mobile.

I can only deduct that this is one of the reasons for why mobile and web developers at our company had (and to this day have) a distinctively different stance towards `GraphQL`. That our initiative was mostly driven (at least in the start) by backend people might also have played into it.

  - all-in or nothing mentality for the web
  - drop in replacement for BFFs on mobile

# 2. Client libraries weren't on par when we started
  - different clients developed different strategies
  - ios/android -> hand-rolled their client
  - web -> started with fetch but soon went changed to apollo client  

# 3. All client developers struggled with error-handling and partial results

- The first web frontends didn't properly shift away from the REST mindset

# 4. Even though GraphQL documentation is great, onboard carefully
  - don't assume people will read the existing documentation 
  - Make sure that everyone understands how a GraphQL server works
  - negative example: query deduplication, apollo batching

# 5. GraphQL type system feels (sometimes) too basic
  - Lack of namespaces
  - Lack of tags / annotations

# 6. GraphQL spec lacks a pagination abstraction

# 7. Don't be naive with file uploads

# 8. We changed our mutation design at least twice (and still struggle with it)

# 9. Consider caching early 

# 10. Schema-first is only half of the story
  - what about resolvers?
  - Custom directives are beautiful

 End to end type safety, I'm having a deja-vu