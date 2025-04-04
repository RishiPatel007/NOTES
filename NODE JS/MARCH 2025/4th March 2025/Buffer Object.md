## **What is Buffer in Node?**

- **Buffer in Node is a built-in object used to perform operations on raw binary data**. The buffer class allows us to handle the binary data directly.

- Examples of binary data include images, audio and video files, and raw data from a network.

- Generally, **Buffer refers to the particular memory location in memory**. Buffer and array have some similarities, but the difference is array can be any type, and it can be resizable. Buffers only deal with `binary data`, and it can not be `resizable`. Each integer in a buffer represents a byte. console.log() function is used to print the Buffer instance.

- Buffers are highly efficient when dealing with large amounts of binary data or when performance is critical, as they bypass the overhead of encoding/decoding data into JavaScript’s native string format.

## **Buffer Methods:**

| **No** | **Method**                             | **Description**                                       |
| ------ | -------------------------------------- | ----------------------------------------------------- |
| 1      | Buffer.alloc(size)                     | It creates a buffer and allocates size to it.         |
| 2      | Buffer.from(initialization)            | It initializes the buffer with given data.            |
| 3      | Buffer.write(data)                     | It writes the data on the buffer.                     |
| 4      | toString()                             | It read data from the buffer and returned it.         |
| 5      | Buffer.isBuffer(object)                | It checks whether the object is a buffer or not.      |
| 6      | Buffer.length                          | It returns the length of the buffer.                  |
| 7      | Buffer.copy(buffer,subsection size)    | It copies data from one buffer to another.            |
| 8      | Buffer.slice(start, end=buffer.length) | It returns the subsection of data stored in a buffer. |
| 9      | Buffer.concat([buffer,buffer])         | It concatenates two buffers.                          |

