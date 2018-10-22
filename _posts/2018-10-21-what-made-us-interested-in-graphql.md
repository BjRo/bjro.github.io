---
---
When I try to trace back why I think `GraphQL` is a good fit for us, I always end up somewhere in the years 2012, 2014 and 2016.

# 2012
In 2012 I started working for `XING` in the API - team. Together we launched `XING`s public API that same year. The infrastructure for that had already been in place for roughly two years (I think) and was also the data source for `XING`s own native mobile applications. In fact many of the APIs that you would find later in the public API originated in the context of those applications and at least for a short time there was a 100% overlap between the public API and what the mobile apps were using. 

One thing we already had at that time was a query parameter called `fields` on the users API and `user_fields` on every API that was referencing users. These query parameters expected a comma separated list of field names and if you would call the API that way, you'd only get back what you had requested. It even supported nesting so you could request `business_address.city` to only get the city portion of the business address. If you look at it now from a `GraphQL` perspective, you might think "wait a minute, that sounds almost like a selection set" and I think this isn't too far off. It had the same benefits (tracking, e.g. who is using what and bandwidth optimization, e.g. only transfer what the client actually needs) but obviously ours was a very simple, poor mans version of the idea.

Unfortunately, driven by the overarching goal to make things as straightforward to use as possible, the team looked at this only as an optimization. If you didn't specify the fields, you would get everything. I bet you can already guess what happened: While our mobile applications made good use of this, most of the other consumers of the public API didn't, which gave us quite some headakes when we wanted to change something. 

Talking about change, I think there's a field of tension if you're attempting to re-use a public API for your mobile applications (or the other way around) like we did. Good public APIs are like a promise of stability. They change very infrequently. You can rely on them and build solid integrations on them. On the other end of the spectrum are your own mobile applications where you more often than not want to iterate fast, get features out as fast as you can and learn based on actual usage. These two things were always at odds at the time. Often the desired change some of our product teams wanted to make wasn't easily possible without breaking exising consumers of the public API. Usually it would result in either additional API calls to get the necessary data or adding data to existing APIs and consumers whould receive additional data they don't actually need. 

This is usually the place where somebody ...

- REST
- HATEOAS
- Lack of standards and tooling

# 2014

# 2016