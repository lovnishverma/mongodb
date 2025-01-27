# MongoDB Installation and Basic CRUD Operations

![image](https://github.com/user-attachments/assets/32e13dfd-57f1-4218-9256-936111249c30)

## What is MongoDB?
MongoDB is a NoSQL database that stores data in flexible, JSON-like documents. It’s schema-less, meaning the structure of the data can evolve over time.

![image](https://github.com/user-attachments/assets/68e6a01c-f362-4ff5-8e02-a08d989f8cac)

---
Let’s see how RDBMS and MongoDB differ:

![image](https://github.com/user-attachments/assets/5f561646-c0a0-4940-a061-09b5e2dc48a4)

### Key Features:
- 📄 Document-oriented (stores data in JSON-like documents).
- 📊 High scalability and performance.
- 🗄️ Schema-less, meaning flexible data structures.
- 🔄 High availability through replication.
- 🛠️ Supports complex queries with the Aggregation Framework.

---

## Installation Steps

### **Step 1: Download MongoDB**
1. Visit the [MongoDB Download Center](https://www.mongodb.com/try/download/community).
2. Select your operating system (Windows, macOS, or Linux) and download the appropriate version.

### **Step 2: Install MongoDB**
- **For Windows:**
  - Run the `.msi` file and complete the setup.
  - Add the MongoDB `bin` folder to your system PATH for easy access.
- **For macOS (Homebrew):**
  ```bash
  brew tap mongodb/brew
  brew install mongodb-community
  ```
- **For Linux:**
  Use your package manager, e.g., `apt` for Ubuntu:
  ```bash
  sudo apt update
  sudo apt install -y mongodb
  ```

### **Step 3: Start MongoDB**
1. Start the MongoDB server:
   ```bash
   mongod --dbpath <path_to_data_directory>
   ```
   Replace `<path_to_data_directory>` with the path where you want to store data.

2. Connect to the MongoDB shell:
   ```bash
   mongo
   ```

---

## Basic CRUD Operations in MongoDB

CRUD stands for **Create**, **Read**, **Update**, and **Delete**. Let’s use a collection named `students` with Indian names as examples.

![image](https://github.com/user-attachments/assets/3f5cf922-a9b2-4ed9-b0e0-a60eacd708fe)

### **1. Create (Insert)**
Use the `insertOne()` or `insertMany()` methods to add data.

```javascript
// Insert one document
use school;
db.students.insertOne({ name: "Rajesh Kumar", age: 20, city: "Delhi" });

// Insert multiple documents
db.students.insertMany([
  { name: "Priya Sharma", age: 19, city: "Mumbai" },
  { name: "Amit Singh", age: 22, city: "Bangalore" }
]);
```

---

### **2. Read (Find)**
Query data using the `find()` or `findOne()` methods.

```javascript
// Find all documents
db.students.find();

// Find documents with a specific condition
db.students.find({ city: "Mumbai" });

// Find documents with age greater than 20
db.students.find({ age: { $gt: 20 } });

// Find one document
db.students.findOne({ name: "Priya Sharma" });
```

---

### **3. Update**
Use `updateOne()`, `updateMany()`, or `replaceOne()` to modify data.

```javascript
// Update one document
db.students.updateOne(
  { name: "Rajesh Kumar" },
  { $set: { age: 21 } }
);

// Update multiple documents
db.students.updateMany(
  { city: "Mumbai" },
  { $set: { status: "Active" } }
);

// Replace a document
db.students.replaceOne(
  { name: "Amit Singh" },
  { name: "Amit Singh", age: 23, city: "Hyderabad" }
);
```

---

### **4. Delete**
Use `deleteOne()` or `deleteMany()` to remove data.

```javascript
// Delete one document
db.students.deleteOne({ name: "Priya Sharma" });

// Delete multiple documents
db.students.deleteMany({ city: "Mumbai" });
```

---

## Aggregation Framework

Aggregation allows processing and analyzing data. Let’s explore with examples:

### **Example 1: Grouping**
Count the number of students by city:
```javascript
db.students.aggregate([
  { $group: { _id: "$city", count: { $sum: 1 } } }
]);
```

### **Example 2: Average Age**
Calculate the average age of students:
```javascript
db.students.aggregate([
  { $group: { _id: null, avgAge: { $avg: "$age" } } }
]);
```

### **Example 3: Sorting**
Sort students by age in descending order:
```javascript
db.students.aggregate([
  { $sort: { age: -1 } }
]);
```

---

## Useful Commands

### List all databases:
```javascript
show dbs;
```

### Switch to (or create) a database:
```javascript
use school;
```

### List all collections in a database:
```javascript
show collections;
```

### Drop a collection:
```javascript
db.students.drop();
```

---

## Summary

MongoDB’s flexibility and simplicity make it a great choice for beginners and professionals alike. Start by mastering basic CRUD operations, then explore the powerful Aggregation Framework for advanced queries.😊
