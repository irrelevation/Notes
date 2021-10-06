# GraphQL

## Types

There are 6 basic types:

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
