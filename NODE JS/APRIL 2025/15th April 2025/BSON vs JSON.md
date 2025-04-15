# MongoDB BSON Overview

## What is BSON?

BSON (Binary JSON) is a binary encoded serialization format that extends the JSON model—a textual object notation widely used to transmit and store data across web-based applications. While JSON is human-readable and easy to understand, BSON offers superior performance and flexibility with additional data types. BSON encodes type and length information, making it easier and faster for machines to parse.

---

## BSON Data Types

|     Data Type Supported by BSON      |
| :----------------------------------: |
|                Double                |
|                String                |
|     Object (embedded documents)      |
|                Array                 |
|             Binary data              |
|        Undefined (deprecated)        |
|    ObjectId (12-byte identifier)     |
|               Boolean                |
| Date (milliseconds since Unix epoch) |
|                 Null                 |
|          Regular Expression          |
|        DBPointer (deprecated)        |
|              JavaScript              |
|         Symbol (deprecated)          |
|            32-bit integer            |
|              Timestamp               |
|            64-bit integer            |
|              Decimal128              |
|               Min key                |
|               Max key                |

---

## Binary Data Storage in MongoDB

MongoDB provides multiple approaches for storing binary files like images and videos:

1. **Binary Data Type**:
    
    - Store files directly using BSON's Binary data type
    - Limited by MongoDB's 16MB document size limit
    - Suitable for smaller files (icons, thumbnails, etc.)
2. **GridFS**:
    
    - MongoDB's solution for larger files exceeding the 16MB limit
    - Splits files into chunks stored in separate collections
    - Uses two collections: `fs.files` (metadata) and `fs.chunks` (binary data)
    - Provides streaming capabilities and partial retrieval
3. **File References**:
    
    - Store files in a filesystem or cloud storage service (S3, etc.)
    - Store only metadata and file paths/references in MongoDB
    - Recommended for most production applications
    - Offers better performance, scalability, and easier backups

---

## BSON's Key Advantages for MongoDB

BSON offers MongoDB a strategic combination of technical and practical benefits:

1. **Efficient Binary Format**: More compact storage and faster transmission than text-based JSON.
2. **Rich Type System**: Extends JSON with critical database types (dates, binary data, ObjectIds, various numeric formats).
3. **Performance Optimizations**: Fast encoding/decoding and efficient field traversal with length indicators that allow skipping to specific fields.
4. **Database-Oriented Design**: Purpose-built for document databases with features like efficient traversal and document metadata.
5. **Developer-Friendly Approach**: Maintains direct JSON compatibility while adding database functionality, leveraging existing JSON knowledge and offering intuitive object mapping in programming languages.
6. **Strategic Compromise**: Balances human readability, machine efficiency, schema flexibility, and type richness better than alternatives like Protocol Buffers, Thrift, or ASN.1, which had various limitations when MongoDB was developed.
7. **Cross-Platform Support**: Implementations available across many programming languages, making it versatile for diverse tech stacks.
8. **Indexing Support**: The structured format facilitates efficient indexing of fields within documents.



# 📘 BSON Type Comparison Order – MongoDB Notes

---

## 🔢 BSON Type Sort Order (From Lowest to Highest)

1. `MinKey` (internal)
2. `Null`
3. Numbers (`Int32`, `Int64`, `Double`, `Decimal128`)
4. `Symbol`, `String`
5. `Document` (Object)
6. `Array`
7. `Binary Data`
8. `ObjectId`
9. `Boolean`
10. `Date`
11. `Timestamp`
12. `Regular Expression`
13. `MaxKey` (internal)

---

## 🔍 Comparison Rules and Behavior

### ✅ **Numbers**
- All numeric types are compared as equal types.
- MongoDB converts them internally before comparing.

### 🔤 **Strings**
- Compared using **binary** (byte-wise) comparison by default.
- Use **collation** to apply locale-based rules (e.g., case-insensitive).

### 🧾 **Arrays**
- **Ascending sort**: uses the **smallest** element.
- **Descending sort**: uses the **largest** element.
- **Empty array**: considered **less than** `null` or missing fields.

### 🧱 **Objects (Documents)**
- Compared **recursively** by:
  1. Field names (in insertion order)
  2. Field types
  3. Field values
- A shorter document with fewer fields is less than a longer one with the same prefix.

### 🕒 **Date vs Timestamp**
- `Date` < `Timestamp`
- `Date` stores **milliseconds**, `Timestamp` is used internally and includes **seconds + increment**.

### ❌ **Missing Fields**
- Treated as **empty BSON Object**.
- Missing and `null` fields behave similarly in sort order.

### 📦 **Binary Data**
- Compared in order:
  1. **Length**
  2. **Subtype**
  3. **Byte-by-byte value**

---

## 🧠 Special BSON Types

- `MinKey`: Always sorts lowest.
- `MaxKey`: Always sorts highest.
- Mainly used in range queries.
