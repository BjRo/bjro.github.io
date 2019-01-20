A belated happy new year everyone! I hope everyone of you had a good start into the new year. Todays post is going to be of a different kind compared to the [rest of the the series so far](/per-aspera-ad-astra/). In the last posts I talked in depth about the "why?", the initial project decisions and the preparations we took to ensure that we'd be able to deliver on our promise. But I haven't yet talked about our actual experience of introducing `GraphQL` into our organization. 

At the end of the first year (2017) our initiative was already seen as a success and it continued to thrive in 2018 (though slower than in 2017, mostly for reasons that were outside of our control). Most of the benefits we expected from `GraphQL` turned out to be true. It's quite eye opening to see colleagues play with `GraphiQL` (or later `GraphQL Playground`) for the first time. Pretty much all of them instantly realize the (positive) impact this could have one their work. Some also instantly get that `GraphQL` has an impact on collaboration between the various disciplines.

But it's not all roses. Our road was and continues to be bumpy. In 2018 you can find an ocean full of resources about why `GraphQL` "is the new sexy", "superior to REST", "to REST what REST was to SOAP" and in general "the best next thing after slided bread". In order to have a meaningful discussion about a technology though, I believe that we also need openly talk about our unexpected outcomes, mistakes and also areas where maybe room for improvement exists in a technology. Only then can we have a more nuanced view on a piece of technology. 

To give you some context about the company I'm working in (and that is worth understanding before going into the individual points): 

* My employer has roughly __1,3k employees__ of which __~300+ are developers__ 
* Of these to my knowledge roughly __70+ are native mobile developers__ 
* For the rest I don't have concrete numbers, but my feeling is that it's roughly __2/3 backend developers__ and __1/3 web frontend developers__. 
* Most of the engineering teams are setup to build __all representations of their product__ (backend, ios, android & web)
* In comparison the teams that are dealing with platform topics are fairly small. 
  * The system architecture team (which primarily is concerned with running our `PAAS` platform based on `Kubernetes` these days) is __~10 people__. 
  * My team that was pushing the `GraphQL` initiative counts __4 people__ (including myself and we also had to maintain our OAuth gateway on the sidelines).
* In general our engineering organization tries to give a lot of freedom and autonomy to individual product teams, but in general shields them from platform related work. As a consequence there's always the lingering pressure for platform related teams to [find ways to do their work without interrupting or even blocking product teams](https://www.youtube.com/watch?v=cIpBpGQ0XTI) and as a consequence a lot of the larger technology initiatives by their nature need to be incremental and non-blocking in how they're rolled out.

That being out of the way, let's dive into our findings from year one (2017):

# 1. Expectations on GraphQL vary dramatically between web and native mobile developers
Have you ever called into a `GraphQL` service by hand, without some `GraphQL` specific tooling? Like with `curl` or `fetch`? If you've tried that and have understood the format that a `GraphQL` server expects, then you realize that everyone who is able to do a `REST` call is also able to interact with a `GraphQL` server. They are not too far apart. Sure, the error handling differs significantly, but the general mechanics of obtaining data a very close. 

This enables a more or less straight forward iterative rollout plan. First get rid of the `BFFs` and use `GraphQL` to talk to the platform instead. Then in case there's value seen from the frontend teams, move higher into the client stack. Always assuming that we need to manage the risk of `GraphQL` turning out to be such a great fit for our landscape. We tried to be lean and adaptive.

So much for the theory, now comes the practice part.

Our mobile developers pretty did exactly that. It kinda seems logical now, looking back at the last two years, since a [lot of our motivation came from mobile challenges](what-made-us-interested-in-graphql). That group treated `GraphQL` as a drop-in replacement for `REST` that freed them from a lot of the request coordination logic. They had some gripes with error handling (more on that later) and the available native libraries (both mobile teams opted against using the available `Apollo` library, because they deemed them not ready yet), but all I think they were pretty happy with our proposition.

On the web side, things became slightly interesting though. [`React`](https://reactjs.org/) had already been in place for quite a while as the default client side library, together with [`Redux`](https://redux.js.org/) as the client side state management solution. [`BFFs`](https://samnewman.io/patterns/architectural/bff/) were the norm and supplied the frontend with data. Our `GraphQL` gateway would make these `BFFs` obsolete. Not so different to the mobile side, or so we assumed.

In retrospect this assumption is one of the larger mistakes that I personally made. Let's say it this way, this idea created quite a bit of friction between the API pushing the `GraphQL` topic and the team responsible for the frontend architecture. It turns out for them, `GraphQL` wasn't only about an API. It was a whole new way to build applications end-to-end (basically API + client side state management + self contained `React` components that specify their data requirements via co-located `GraphQL` queries and fragments). And they wanted to have all of that experience immediately. All of the great `Apollo` talks and demos in that area certainly also didn't make it easier for us.

The only problem though was this: We lacked the client side experience and the frontend colleagues lacked the resources / time to properly accompany this. Which led to introducing `Apollo` at a later point and a time where we significantly lacked guidance on how to bring all the pieces together in the frontend. Introducing `Apollo` later resulted in some surprises, for instance in the caching behavior which we initially weren't aware of. 

The point to take away from this is that you should plan and setup your `GraphQL` introduction end to end, with all necessary client resources available. While mobile developers were fine with an incremental adoption, trying to follow the same approach on the web created friction for us. The `GraphQL` buzz today primarily happens on the web side and in the `Javascript` world. With that expectations of what `GraphQL` is able to deliver differ dramatically from their mobile counterparts.

> It's a bit ironic, if you know the history of `GraphQL`. If you trace back the `GraphQL` story to its origins within `Facebook` you realize that it came from a mobile background and then expanded further into the company. Basically what happened is that some pretty clever people built the first version of the concept for the new, native mobile newsfeed. That was when `Facebook` was still primarily following their `HTML5` approach within their mobile applications. When the decision was made to switch the strategy to go all in on native development instead of web technology, it was a combination of "having a great, working concept" and "being at the right spot, at the right time". They pretty much created the blueprint for things to come. `GraphQL` didn't start out on the web or even `Javascript` side. I believe the original `GraphQL` server was and is still written in `Hack`. Only when they came to the conclusion that "this could really be a thing", they created the spec and the reference implementation in `Javascript`. But this happened at a later point. 
>
> In case you wondering: In 2017 I sat next to [Dan Schaefer](https://twitter.com/dlschafer) in the cab on the way to the speakers dinner for the `GraphQL EU` conference and had the chance to pester him with all sorts of questions. Dan is one of the original `GraphQL` creators (besides [Nick Schrock](https://twitter.com/schrockn) and [Lee Byron](https://twitter.com/leeb)).

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