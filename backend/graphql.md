# GraphQL

# General notes
1. GraphQL uses a query langauge called `schema definition language`.
2. the `type definitions` represents the interface of our API or simple what the client can request, while the `resolver` are the implementation. They provide the code that knows how to return the actual value.
3. In GraphQL `null` is like `undefined` in javascript. It means that the field is not available.
4. Resolver functions always used first and has the priority over the actual valuse if the resolved field originally exists in the results.


# Questions
1. Can GraphQL APIs used with a protocol other than HTTP?
2. What is the N+1 issue?
3. 