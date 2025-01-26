# MongoDB Installation and Basic CRUD Operations and Aggregation framework

![image](https://github.com/user-attachments/assets/32e13dfd-57f1-4218-9256-936111249c30)

## Introduction to MongoDB

MongoDB is a popular NoSQL database that provides high performance, high availability, and easy scalability. It stores data in flexible, JSON-like documents, which means fields can vary from document to document, and data structure can be changed over time.

![image](https://github.com/user-attachments/assets/68e6a01c-f362-4ff5-8e02-a08d989f8cac)

Let’s see how RDBMS and MongoDB differ:

![image](https://github.com/user-attachments/assets/5f561646-c0a0-4940-a061-09b5e2dc48a4)

### Key Features:
- 🗄️ Schema-less database (NoSQL)
- 📄 Document-oriented
- 🔄 High availability through replication
- 📊 Horizontal scalability with sharding
- ⚡ Indexing for better query performance
- 🛠️ Support for aggregation and rich queries

---

## Installation

### Step 1: Download MongoDB
1. Go to the [MongoDB Download Center](https://www.mongodb.com/try/download/community).
2. Select the appropriate version for your operating system (Windows, macOS, or Linux).

### Step 2: Install MongoDB
- **Windows:**
  1. Run the downloaded `.msi` file and follow the installation instructions.
  2. Add the MongoDB `bin` directory to your system's PATH environment variable.
- **macOS:**
  1. Use Homebrew to install: `brew tap mongodb/brew` and `brew install mongodb-community`.
- **Linux:**
  1. Use the package manager for your distribution (e.g., `apt` for Ubuntu or `yum` for CentOS).

### Step 3: Start MongoDB
1. Start the MongoDB server:
   ```bash
   mongod --dbpath <path_to_data_directory>
   ```
   Replace `<path_to_data_directory>` with the path where you want MongoDB to store data.

2. Open the MongoDB shell:
   ```bash
   mongo
   ```

---

## Basic CRUD Operations

CRUD stands for Create, Read, Update, and Delete. These are the basic operations you can perform in MongoDB.

![image](https://github.com/user-attachments/assets/3f5cf922-a9b2-4ed9-b0e0-a60eacd708fe)

### 1. Create (Insert)
To insert documents into a collection, use the `insertOne()` or `insertMany()` methods.

```javascript
// Insert a single document
use myDatabase;
db.users.insertOne({ name: "John Doe", age: 30, email: "john@example.com" });

// Insert multiple documents
db.users.insertMany([
  { name: "Alice", age: 25 },
  { name: "Bob", age: 35 }
]);
```

### 2. Read (Find)
To query documents, use the `find()` method.

```javascript
// Find all documents
db.users.find();

// Find documents with a specific condition
db.users.find({ age: { $gte: 30 } });

// Find one document
db.users.findOne({ name: "Alice" });
```

### 3. Update
To update documents, use the `updateOne()`, `updateMany()`, or `replaceOne()` methods.

```javascript
// Update a single document
db.users.updateOne(
  { name: "John Doe" },
  { $set: { age: 31 } }
);

// Update multiple documents
db.users.updateMany(
  { age: { $lt: 30 } },
  { $set: { status: "young" } }
);

// Replace a document
db.users.replaceOne(
  { name: "Alice" },
  { name: "Alice", age: 26, email: "alice@example.com" }
);
```

### 4. Delete
To delete documents, use the `deleteOne()` or `deleteMany()` methods.

```javascript
// Delete a single document
db.users.deleteOne({ name: "Bob" });

// Delete multiple documents
db.users.deleteMany({ age: { $gte: 30 } });
```

---

## Basic Aggregation Example

Aggregation is used to process data and return computed results. It allows for operations like filtering, grouping, and sorting.

```javascript
// Group by age and count the number of users in each group
db.users.aggregate([
  { $group: { _id: "$age", count: { $sum: 1 } } },
  { $sort: { _id: 1 } }
]);

// Find the average age of users
db.users.aggregate([
  { $group: { _id: null, avgAge: { $avg: "$age" } } }
]);
```

---

## Additional Commands

### List Databases
```javascript
show dbs;
```

### Switch/Create a Database
```javascript
use myDatabase;
```

### Show Collections
```javascript
show collections;
```

---

## Conclusion
MongoDB is a flexible and powerful database solution suitable for various applications. Understanding and mastering basic CRUD operations is the first step to utilizing its full potential. Aggregation allows for advanced data analysis, making MongoDB a versatile tool for developers.

---

## References
- [Introduction to MongoDB on CodeProject](https://www.codeproject.com/Articles/1037052/Introduction-to-MongoDB)
- [MongoDB CRUD Operations](https://www.mongodb.com/docs/manual/crud/)
- [MongoDB Aggregation Framework](https://www.mongodb.com/docs/manual/aggregation/)

