# NoSQL

## Embedding

| Pro | Con |
| --- | --- |
| First Item | Second Item |


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
