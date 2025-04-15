# MongoDB ObjectId and \_id Field

## ObjectId Structure (12 bytes total)

An ObjectId in MongoDB is a 12-byte unique identifier automatically generated for each document when created if no _id value is specified.

| Component  | Size    | Description                                                  |
| :--------- | :------ | :----------------------------------------------------------- |
| Timestamp  | 4 bytes | Seconds since the Unix epoch (January 1, 1970)               |
| Machine ID | 3 bytes | Identifier of the machine where the ObjectId was generated   |
| Process ID | 2 bytes | Process ID of the MongoDB server that generated the ObjectId |
| Counter    | 3 bytes | Incrementing counter, initialized to a random value          |

## Key Characteristics of ObjectId

1. **Guaranteed uniqueness** across distributed systems without coordination
2. **Chronologically sortable** due to the timestamp component
3. **Compact** at only 12 bytes
4. **Contains creation time** which can be extracted
5. **Performs better** than UUID/GUID in many database operations

## Example

```
ObjectId("65fc1e3b7894f32b36d75297")
```

To extract creation time:

```javascript
ObjectId("65fc1e3b7894f32b36d75297").getTimestamp()
// Returns a date object with the creation time
```