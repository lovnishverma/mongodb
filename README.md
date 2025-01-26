# MongoDB Installation and Basic CRUD Operations

## Introduction to MongoDB

MongoDB is a popular NoSQL database that provides high performance, high availability, and easy scalability. It stores data in flexible, JSON-like documents, which means fields can vary from document to document, and data structure can be changed over time.

### Key Features:
- Schema-less database (NoSQL)
- Document-oriented
- High availability through replication
- Horizontal scalability with sharding
- Indexing for better query performance
- Support for aggregation and rich queries

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
MongoDB is a flexible and powerful database solution suitable for various applications. Understanding and mastering basic CRUD operations is the first step to utilizing its full potential.

