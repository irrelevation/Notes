# GraphQL

## Types & Scalars

Basic types are called scalars. These are the most important basic types:

- String
- Int
- Float
- ID
- Boolean
- Query (the root type, required for every schema)

You can define further types based on those six or on other types you define.

---

## Schema

Defines the structure of your data.

---

## Queries

The Query type defines, what you can query for in the root level of a query.
If you want to query for a field that is not of a basic type, you need to specify containing fields you want to query for (and so on...).

---

## Connection
A connection is a  paginated field on an object.

---

## Edge
An Edge has metadata about an oject in a paginated list. It contains a reference to the actual object as well as a cursor for pagination

---

## Node
A Node represents the actual Object you were looking for.

---

## pageInfo
Indicates if there is more data to fetch

---

## Sources
[Apollo Blog](https://www.apollographql.com/blog/graphql/pagination/understanding-pagination-rest-graphql-and-relay/)

[GraphQL Homepage](https://graphql.org/)