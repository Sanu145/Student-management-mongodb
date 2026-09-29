# Student Management System Using MongoDB

A NoSQL database implementation demonstrating database creation, batch document insertion, CRUD operations, logical filtering, and sorting using MongoDB and `mongosh`[cite: 1].

---

## 📌 Project Overview
This project replaces traditional relational table-based schemas with MongoDB's flexible, document-oriented data model[cite: 1]. It manages a collection of student profiles comprising academic attributes such as roll number, name, age, marks, and city[cite: 1].

### Objectives
- Understand fundamental NoSQL database operations[cite: 1].
- Create databases and collections via MongoDB Shell (`mongosh`) and MongoDB Compass[cite: 1].
- Perform full CRUD (Create, Read, Update, Delete) operations[cite: 1].
- Apply comparison and logical operators for targeted data retrieval[cite: 1].
- Implement sorting, limiting, and document counting methods[cite: 1].

---

## 🗂️ Data Schema
Each student record is stored as a JSON document structured as follows:

{
  "roll": 101,
  "name": "Riya",
  "age": 18,
  "marks": 72,
  "city": "Delhi"
}

---

## ⚡ Key Operations & MongoDB Queries

### 1. Database & Collection Setup

// Switch or create database
use Students;

// Create collection
db.createCollection("students");

### 2. Inserting Records

// Bulk document insertion
db.students.insertMany([
  { roll: 101, name: "Riya", age: 18, marks: 72, city: "Delhi" },
  { roll: 102, name: "Kunal", age: 19, marks: 89, city: "Mumbai" },
  { roll: 103, name: "Mehak", age: 20, marks: 64, city: "Pune" }
]);

### 3. Comparison Operators

* **Equal To (`$eq`):**

db.students.find({ marks: { $eq: 88 } });

* **Greater Than (`$gt`) & Greater Than or Equal (`$gte`):**

db.students.find({ marks: { $gt: 85 } });
db.students.find({ marks: { $gte: 90 } });

* **Less Than (`$lt`) & Less Than or Equal (`$lte`):**

db.students.find({ marks: { $lt: 60 } });
db.students.find({ marks: { $lte: 70 } });

### 4. Logical Operators

* **AND (`$and`):**

db.students.find({
  $and: [
    { marks: { $gt: 80 } },
    { age: 19 }
  ]
});

* **OR (`$or`):**

db.students.find({
  $or: [
    { city: "Delhi" },
    { city: "Pune" }
  ]
});

### 5. Update & Delete

* **Update Single Document (`$set`):**

db.students.updateOne({ roll: 105 }, { $set: { marks: 95 } });

* **Delete Single Document:**

db.students.deleteOne({ roll: 110 });

* **Delete Multiple Documents:**

db.students.deleteMany({ marks: { $lt: 60 } });

### 6. Data Organization & Utilities

* **Sort Ascending (1) & Descending (-1):**

db.students.find().sort({ marks: 1 });
db.students.find().sort({ marks: -1 });

* **Limit Results:**

db.students.find().limit(5);

* **Count Documents:**

db.students.countDocuments();

