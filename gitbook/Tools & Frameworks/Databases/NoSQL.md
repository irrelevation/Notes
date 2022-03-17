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

### Polymorphic Pattern

Keeping documents in a collection wich are similar but not identical.

- grouping documents into collections based on access/queries increases performance
- good for merging heterogenous data sources, eg. in Single View Applications

### Attribute Pattern

Use it when
- a document has similar fields we want to query together 
- only a small number of documents has the field we want to query

Under those circumstances you would usually need to build a lot of indexes wich is bad for (write) performance and we'd have to write clunky queries. 
Grouping the fields by their common attributes solves this problem.

### Bucket Pattern

Often applied when working with time series data. The idea is to bucket the data (usually by timespan) and add some aggregation metrics (eg average/sum of measurements) to each bucket. This will reduce index size and let's you use pre-aggregated data directly and write simpler queries. If you are doing a lot of range queries and calculate aggregated metrics, give bucketing a try.

### Outlier Pattern

Outlier can pose problems especially in terms of performance. But changing our entire schema only to deal with those outliers is undesirable. The Outlier Pattern tries to address this problem.
If you have a One to too Many relationship that needs to be stored as **One --> Too Many** create overflow Documents (use the same id with an incrementing postfix). Indicate in your original and overflow documents whether there are extra entries (via some boolean key-value pair).

### Computed Pattern
The Computed Pattern addresses the problem of constantly recalculating values in read heavy scenarios.

You can
- calculate computations on write, or in intervals and use the precomputed value, instead of computing on read.
- compute on read and save the computed value, maybe with a timestamp, to judge wether it must be recomputed.

### Extended Reference Pattern

Duplicate some but not all of the data you are querying for to avoid expensive $lookups. Only duplicate the part that is frequently accessed together.

## Anti Patterns (MongoDB)

### Separating data that is accessed together

#### Problems
- $lookups are slow and resource-intensive

#### Solutions
- embedding data
- partially embedding data

### Massive arrays

#### Problems
- bad index performance
- can exceed document size limit (16MB in MongoDB)

#### Solutions
- embed the other way around
- use reference instead of embedding
- use [Extended Reference Pattern](#Extended-Reference-Pattern)

### Massive number of collections
Thou shalt not exceed 10,000 collections (per replica set).

#### Problems
- empty and unused indexes drain resources
- decreased performance

#### Solutions
- remove empty collections
- $merge collections whose size is mostly indexes into other collections

### Unnecessary indexes

Though shalt not exceed 50 indexes per collection.

#### Problems
- decreases read performance (wiredtiger will open all collection and index files on startup)
- decreases write performance
- take up space

#### Solutions
- drop rarely used indexes
- drop redundant indexes (eg. covered by compound index)

### Bloated documents

Thou shalt keep thy documents small. Wiredtiger (the MongoDB storage engine) caches indexes and frequently used documents.
If your documents are too big, they wont all fit in the cache and slow disk access is necessary. Wiredtiger's cache is 
```javascript
const CACHE_SIZE = MATH.max((totalRAM - 1GB) * 0.5, 256MB);
```

#### Problems
- slow queries

#### Solutions
- Make sure your working sert fits in your cache
  - get more RAM
  - slim down your frequently accessed documents

### Case insensitive queries without case insensitive indexes

#### Problems
- slow (eg. $regex queries)

#### Solutions
- Create a case insensitive index
  - Add an index with a **collation** of strength 1 or 2. Match that collation strength in your query.
  - Create a collection with a default collation strength of 1 or 2. All indexes and queries in that collection will automatically be case insensitive.

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

- [Schema Design Patterns](https://www.mongodb.com/blog/post/building-with-patterns-a-summary)
- [Schema Design Anti-Patterns](https://www.youtube.com/watch?v=8CZs-0it9r4)
