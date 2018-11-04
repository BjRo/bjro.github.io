---
title: Choosing the right technology for XING One
---
Figuring out what technology to use for a large scale, long term project is never an easy feat. 8 years ago `XING` was pretty much only using `Perl` and `Ruby (on Rails)` in the backend. Nowadays we've got plenty of options to choose from: `Java`, `Scala`, `Elixir`, `Go`, `PHP` and `Ruby`. Most of them offer `GraphQL` implementations. So how do you skin that cat?

First of all, I made the conscious decision not to make my personal skills or the widespread availability of knowhow within `XING` a trumping factor in the decision. 

I had successfully delivered products and projects in `Ruby` and `Elixir` within `XING` and a longer history with `C#` before that. I even had done [Martin Oderskys Functional Programming Principles in Scala course](https://www.coursera.org/learn/progfun1) in my free-time one or two years prior to the project. All in all I was confident enough that I would manage to get proficient enough in any programming language if I really had to. 

I also felt that our project shouldn't be restricted by heritage and that we should pick the best solution for the company with a forward oriented mindset. If I were to base the decision predominantly on the availability of knowhow within `XING`, the answer would involuntarily lead me to `Ruby`, which is still the most used technology stack within our company. But I had my doubts whether `Ruby` would be a good implementation choice for our proxy. More on that later.

"Opinions", "doubts", let's be honest, we're all more or less biased one way or another. I definitely know I was biased a bit when it came to certain technologies I had used before (at the time I was a heavy advocate for `Elixir` for example). But I thought it was a good idea to counter balance that bias through a more transparent and structured selection process.

# Enter the Premortem
Some months prior, I had read [Decisive by Chip and Dan Heath](https://www.goodreads.com/book/show/15798078-decisive) and one of the tools that was described in there, was a `Premortem`. In a nutshell a `Premortem` is the hypothetical opposite of a `Postmortem`: You don't analyze the failure after the fact, but instead hypothesize what could turn the project into a spectacular failure and then ask the simple questions of **"Why?"** and **"What would I have done about it, if I had known earlier?"**. 

Done collaboratively it allows you to surface risk and brainstorm detection and mitigation strategies from multiple viewpoints in the earlier phases of an initiative. Those phases when you can still do something about the risks. Of course this doesn't rule out `Black Swans`, the [unknown unknowns](https://de.wikipedia.org/wiki/There_are_known_knowns), but it certainly helps to form the right mindset: To be proactive, instead of reactive. Since it was only me back then, I mostly used my boss as the sparring partner for the identified risks, which also helped me to understand the project from a management perspective. 

> We did another larger `Premortem` for our rollout strategy into the company. I'll show this in a separate blog post, because this one contained one  additional element that I find fascinating: Tripwires, or how you would know when something goes on.

You don't need some sophisticated tech for this. Our first version was an `Excel` sheet that was later moved to `Confluence` for documentation purposes. To give you some general idea how this might look like, ours kinda looked like this:  

{% include figure image_path="/assets/images/premortem.png" %}

# The checklist
You probably know this famous quote from Yogi Berra: **"In theory there is no difference between theory and practice. In practice there is."**. During the `Premortem` phase we developed strong hunch that the technology decision for needed to contain some amount of hands-on coding in the respective options. 

Because of that we decided to do something that was unusual and uncommon for technology projects at `XING` (and to my knowledge still is): __We spend the first 1,5 months actually implementing a throwaway prototype of our idea in all the relevant options__

We extracted all gaps of knowledge and risks we surfaced in the `Premortem` that could be validated in the prototyping phase into a simple checklist. You can see those in the screenshot above in the "Prototype relevant" column. 

In the end the shortlist of candidates for us was this:

* `Ruby` with [graphql-ruby](https://github.com/rmosolgo/graphql-ruby)
* `Javascript` with [graphql-js](https://github.com/graphql/graphql-js) and [apollo-server](https://github.com/apollographql/apollo-server)
* `Elixir` with [absinthe](https://github.com/absinthe-graphql/absinthe)
* and `Scala` with [Sangria](https://github.com/sangria-graphql/sangria)

The reason for this shortlist is two-fold. First, we made a pre-requisite that for every technology stack at least some people in the company had already some production experience with it. This was primarily intended as a fallback scenario when our problem solving or troubleshooting skills hit an impasse.

Second, we didn't want to to have deep integration into our monitoring and deployment infrastructure in the critical project path. (I was just coming of a stint in our messenger product where I spend 1,5 months of building integration with our in-house messaging system for `Elixir`)

The checklist contained an example schema, 3 different `GraphQL` queries and 1 `GraphQL` mutation to execute against the server. That was primarily for observing and comparing the execution behavior. On top of that it contained a whole bunch of things to investigate: 

* Does it tick more like a library or a framework?
* How easy is it to customize behavior here and there?
* How good is the documentation?
* How active and inclusive are the maintainers?
* How easy is it to get changes in when necessary?
* As a gut feeling how big is the part that we need to build on top and what was our gut feeling whether we could pull this of?

I wrote the prototypes for `Ruby`, `Scala` and `Javascript`. During the third week of the prototyping phase [Alexis Mas](https://www.xing.com/profile/Alexis_Mas/cv) joined the project, coming over from a different part of the company. He build the `Elixir` prototype. And finally I wasn't alone in this anymore.

We had planned to use only 1 month for the evaluation. In the end it took us 1 and half. Still not bad for roughly 6 consecutive hackweeks. 

The net result of the prototyping phase can be seen in the following two pictures. The symbols you see in the checklist follow the following scheme:

{% include figure image_path="/assets/images/checklist-legend.png" %}

Please note that the following is just an overview and internally a longer descriptive version of this still exists in the documentation of the project.

{% include figure image_path="/assets/images/checklist.png" %}

> I'm pretty certain that the above assessment invites a lot of challenges and critique. These are our conclusions and we tried hard to make them somewhat transparent and comprehensible, but they still contained very subjective impressions. Not everyone might arrive at the same conclusions. Please also note that we were doing this evaluation in February 2017. Some implementations, Apollo in particular, have made a larger jump in their capabilities. Re-doing the implementation today might result in a different ranking for us.

# Why we chose Sangria
In the end `Sangria`, the Scala solution, turned out to be our favorite. 

* The [documentation](https://sangria-graphql.org/learn/) was top-notch
* Conceptually, it quacked more like a library than a framework. As a consequence it was fairly easy to change and extend the behavior of the `GraphQL` engine. Even better, a lot of those extension points also had high quality documentation. 
* The concurrency capabilities of the platform looked like a good fit for our proxy scenario and `Sangria` provided a lot of interesting batching and execution out of the box. 
* Some features were already implemented in `Sangria` that were still being discussed in the `GraphQL` community at the time and lacking in some of the other implementations (for instance the complexity analysis or SDL based schema materialization)

Last but not least, I had a good gut feeling about `Sangria` as an open source project itself. In the short contacts and conversations I had with its maintainer [Oleg Ilyenko](https://github.com/OlegIlyenko) I was amazed how knowledgable and at the same time humble and helpful he was. My impression was that if we would ever run into dead-ends with `Sangrias` code, most of the time we wouldn't have to run a fork, because a `Sangrias` extensibility. And for the cases where this wasn't enough, we could work with him to bring the necessary changes to `Sangria`. This gut feeling turned out to be true multiple times.
