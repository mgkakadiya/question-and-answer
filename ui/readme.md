# Difference between IndexedDB and Local Storage

IndexedDB and Local Storage are both web storage technologies that allow client-side storage of data, but they differ significantly in their capabilities and use cases. Here are the key differences:

## Local Storage

1. **Data Structure**: Local Storage is a simple key-value store. Data is stored as strings.
2. **Size Limit**: Local Storage has a limit of about 5MB per origin (domain).
3. **API Simplicity**: The API for Local Storage is very simple and synchronous, which means it can block the main thread and affect performance if used improperly.
4. **Use Cases**: Best for storing small amounts of simple data, such as user preferences or application state.
5. **Support**: Widely supported across all modern browsers.
6. **Persistence**: Data persists even after the browser is closed and reopened.

## IndexedDB

1. **Data Structure**: IndexedDB is a NoSQL database that can store more complex data types, including objects. It allows for complex querying and indexing.
2. **Size Limit**: IndexedDB has a much larger storage limit than Local Storage. The exact limit can vary but is generally in the hundreds of megabytes or more.
3. **API Complexity**: IndexedDB has an asynchronous API, which is more complex but better for performance as it doesn't block the main thread.
4. **Use Cases**: Best for storing large amounts of structured data, such as files, large datasets, and application data that require complex querying.
5. **Support**: Also widely supported across all modern browsers, but there might be slight differences in implementation.
6. **Persistence**: Data also persists after the browser is closed and reopened.

## Summary

- **Local Storage** is simple and suitable for small amounts of key-value data.
- **IndexedDB** is more complex but powerful, suitable for larger and more complex data storage needs.
