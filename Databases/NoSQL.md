# NoSQL

## Embedding

| Pro | Con |
| --- | --- |
| Retrieve all data with a single query | Large documents === more overhead |
| Avoids expensive JOINs or $lookups | Document size limits (16mb @ mongoDB) |
| Update all Data with a single atomic operation |

## Referencing

| Pro | Con |
| --- | --- |
| Smaller documents | More queries or $lookups |
| Less likely to exceed document size limits |
| No duplication of data |
| Infrequently accessed data not accessed on every query |

## Firebase

Keep your collections **large** and your documents **small**.

### Cloud FIrestore vs. Realtime DB

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
