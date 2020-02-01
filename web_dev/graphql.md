
# Features

* declarative data fetching
* No Overfetching with GraphQL
* Single Source of Truth: GraphQL schema
* GraphQL Schema Stitching
  * Each microservice can have its own GraphQL endpoint, where one GraphQL API gateway consolidates all schemas into one global schema
* GraphQL Introspection
  * autogenerating API documentation
* Strongly Typed GraphQL
  * autocomplete, compile-time validation
* GraphQL Versioning
  * possible to deprecate the API on a field level
* ecosystem
  * graphql playground
  * gatsbyjs

# Cons

* query complexity still exists
  * problems arise when a client requests too many nested fields at once
* Rate Limiting
* Caching