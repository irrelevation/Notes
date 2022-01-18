# NoSQL


## Embedding vs. Referencing

1. Favor embedding over referencing (to avoid JOINs & $lookups) unless you have a compelling reason not to.
2. Needing to access data on its own *is* a compelling reason for referencing.
3. Arrays should *not* grow without bound. Use reverse referencing instead.
4. Model your data according to your application's access pattern.

[Further reading](https://www.mongodb.com/blog/post/6-rules-of-thumb-for-mongodb-schema-design-part-1)


### Embedding

| Pro | Con |
| --- | --- |
| Retrieve all data with a single query | Large documents === more overhead |
| Avoids expensive JOINs or $lookups | Document size limits (16mb @ mongoDB) |
| Update all Data with a single atomic operation |


### Referencing

| Pro | Con |
| --- | --- |
| Smaller documents | More queries or $lookups |
| Less likely to exceed document size limits |
| No duplication of data |
| Infrequently accessed data not accessed on every query |


## Relationships

| Relationship | Implementation |
| --- | --- |
| One to One | Key-Value pair |
| One to Few | Embedding |
| One to Many | Referencing (One --> Many) |
| One to too Many | Referencing (One <-- Many) |
| Many to Many | Referencing (Many <--> Many) |


## Design Patterns

[Further reading](https://www.mongodb.com/blog/post/building-with-patterns-a-summary)


### Outlier Pattern

If you have a One to too Many relationship that needs to be stored as **One --> Too Many** create overflow Documents (use the same id with an incrementing postfix). Indicate in your original and overflow documents whether there are extra entries (via some boolean key-value pair).

### Extended Reference Pattern

Duplicate some but not all of the data you are querying for to avoid expensive $lookups. Only duplicate the part that is frequently accessed together.


## Anti Patterns (MongoDB)

### Separating data that is accessed together

### Massive arrays

#### Problems
- bad index performance
- can exceed document size limit (16MB in MongoDB)

Solutions
- embed the other way around
- use reference instead of embedding
- use [Extended Reference Pattern](#Extended-Reference-Pattern)


### Massive number of collections

### Unnecessary indexes

### Bloated documents

### Case insensitive queries without case insensitive indexes

## Firebase

Keep your collections **large** and your documents **small**.


### Cloud Firestore vs. Realtime DB

Pick Realtime DB if:

- you have a ton of small reads & writes per second
- you require extra low latency (although they are pretty close)

Pick Cloud Firestore otherwise


### Querying

1. Create a reference to the parent key.
2. Use an Ordering function. (optional)
3. Use a querying function. (optional).


#### Ordering Functions

1. `orderByKey()`
2. `orderByChild('childProperty')`
3. `orderByValue()`
4. `orderByPriority()`

## References

- [Schema Design Anti-Patterns](https://www.youtube.com/watch?v=8CZs-0it9r4)
