
- Everybody loves GraphiQL (or GraphQL playground)
- Most of the benefits we expected from GraphQL turned out to be true
- At the end of the first year, our initiative was already seen as a big success and continues to do so after roughly 2 years 
- but it's not all roses and I would specifically talk about the things that caught us of-guard or by surprise regarding GraphQL. Some of the points are surely a result of how we specifically approached GraphQL, but I'm certain that some of our realizations might be shared by other companies out there. 

but

- Expectations on GraphQL vary dramatically between web and native mobile developers
  - all-in or nothing mentality for the web
  - drop in replacement for BFFs on mobile

- Client libraries weren't on par when we started
  - different clients developed different strategies
  - ios/android -> hand-rolled their client
  - web -> started with fetch but soon went changed to apollo client  

- All client developers struggled with error-handling and partial results

- The first web frontends didn't properly shift away from the REST mindset

- Even though GraphQL documentation is great, onboard carefully
  - don't assume people will read the existing documentation 
  - Make sure that everyone understands how a GraphQL server works
  - negative example: query deduplication, apollo batching

- Don't be naive with file uploads

- We changed our mutation design at least twice

- Schema-first is only half of the story
  - what about resolvers?
  - Custom directives are beautiful

- GraphQL type system feels (sometimes) too basic
  - Lack of namespaces
  - Lack of tags / annotations

- GraphQL spec lacks a pagination abstraction

- The code generation deja-vu