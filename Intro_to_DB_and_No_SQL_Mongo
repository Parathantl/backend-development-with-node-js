# Database Systems & Entity Relationship Diagrams

---

## Course Overview (5 minutes)
**Learning Objectives:**
- Understand different types of database systems
- Master Entity Relationship Diagram (ERD) concepts and notation
- Learn ERD design principles and best practices
- Introduction to NoSQL databases and MongoDB

**Today's Schedule:**
- Part 1: Database Types & Fundamentals
- Part 2: Entity Relationship Diagrams
- Part 3: ERD Design - In-class Exercise
- Part 4: NoSQL & MongoDB Introduction
- Part 5: Review & Homework Assignment

---

## Part 1: Types of Database Systems

### What is a Database?
A **database** is an organized collection of structured information, or data, typically stored electronically in a computer system. A database is usually controlled by a database management system (DBMS).

### Major Database Categories

#### 1. Relational Databases (SQL)
**Characteristics:**
- Data stored in tables with rows and columns
- ACID properties (Atomicity, Consistency, Isolation, Durability)
- Uses SQL (Structured Query Language)
- Strong consistency and data integrity

**Popular Examples:**
- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server
- SQLite

**Use Cases:**
- Financial systems
- E-commerce platforms
- Enterprise applications
- Data warehousing

#### 2. NoSQL Databases
**Characteristics:**
- Flexible schema design
- Horizontal scalability
- Eventually consistent (in many cases)
- Optimized for specific data models

**Types of NoSQL:**

**Document Databases:**
- Store data as documents (JSON, BSON, XML)
- Examples: MongoDB, CouchDB, Amazon DocumentDB

**Key-Value Stores:**
- Simple key-value pairs
- Examples: Redis, Amazon DynamoDB, Riak

**Column-Family:**
- Data stored in column families
- Examples: Cassandra, HBase

**Graph Databases:**
- Data stored as nodes and relationships
- Examples: Neo4j, Amazon Neptune, ArangoDB

#### 3. In-Memory Databases
**Characteristics:**
- Data stored in RAM for faster access
- Volatile storage (data lost on restart unless persisted)
- Examples: Redis, Memcached, SAP HANA

#### 4. Time-Series Databases
**Characteristics:**
- Optimized for time-stamped data
- Examples: InfluxDB, TimescaleDB, Prometheus

---

## Part 2: Entity Relationship Diagrams

### What is an ERD?
An **Entity Relationship Diagram (ERD)** is a visual representation of data and relationships between entities in a database system. It serves as a blueprint for database design.

### Core Components of ERD

#### 1. Entities
**Definition:** Objects or concepts that can have data stored about them

**Types:**
- **Strong Entity:** Can exist independently
- **Weak Entity:** Depends on another entity for existence

**Notation:**
- Rectangle for strong entities
- Double rectangle for weak entities

**Examples:**
- Customer (Strong)
- Order (Strong)
- Order_Item (Weak - depends on Order)

#### 2. Attributes
**Definition:** Properties or characteristics of entities

**Types:**
- **Simple:** Cannot be divided (e.g., Age)
- **Composite:** Can be divided into sub-parts (e.g., Full Name → First, Last)
- **Derived:** Calculated from other attributes (e.g., Age from Birth Date)
- **Multivalued:** Can have multiple values (e.g., Phone Numbers)

**Notation:**
- Oval for simple attributes
- Double oval for multivalued
- Dashed oval for derived
- Composite shown with connected sub-attributes

#### 3. Relationships
**Definition:** Associations between entities

**Types by Cardinality:**
- **One-to-One (1:1):** One entity relates to exactly one other
- **One-to-Many (1:M):** One entity relates to many others
- **Many-to-Many (M:N):** Many entities relate to many others

**Notation:**
- Diamond shape
- Lines connecting entities with cardinality notation

### ERD Design Process

#### Step 1: Identify Entities
- Look for nouns in requirements
- Consider what data needs to be stored
- Group related attributes

#### Step 2: Identify Attributes
- Determine properties of each entity
- Identify primary keys
- Consider attribute types

#### Step 3: Define Relationships
- Analyze how entities interact
- Determine cardinality
- Identify foreign keys

#### Step 4: Resolve Many-to-Many Relationships
- Create junction/bridge tables
- Move relationship attributes to junction table

### ERD Example: University System

**Entities:**
- Student (StudentID, Name, Email, Major)
- Course (CourseID, Title, Credits, Department)
- Professor (ProfessorID, Name, Department, Office)
- Enrollment (Grade, Semester, Year)

**Relationships:**
- Student ⟷ Course (M:N through Enrollment)
- Professor ⟷ Course (1:M - Professor teaches Course)
- Student ⟷ Professor (M:N through Course enrollment)

### Advanced ERD Concepts

#### Participation Constraints
- **Total Participation:** Every entity must participate (double line)
- **Partial Participation:** Some entities may not participate (single line)

#### Specialization/Generalization
- **IS-A Relationships:** Subclasses inherit from superclass
- **Disjoint vs. Overlapping:** Can entity belong to multiple subclasses?
- **Total vs. Partial:** Must every superclass entity belong to a subclass?

---

## Part 3: ERD Design - In-class Exercise

### In-Class Exercise: Library Management System

**Scenario:** Design an ERD for a library management system with the following requirements:

**Requirements:**
1. Library has multiple branches
2. Each branch has books, librarians, and members
3. Members can borrow books
4. Books can have multiple copies
5. Track borrowing history with due dates
6. Some books are reserved for reference only
7. Librarians manage specific sections

**Your Task:** Work in pairs to create an ERD including:
- At least 6 entities
- Appropriate attributes for each entity
- Primary keys identified
- Relationships with correct cardinality
- Handle the many-to-many relationships properly

**Time:** 15 minutes design + 5 minutes discussion

### Solution Discussion Points:
- Entity identification strategy
- Handling book copies vs. book titles
- Borrowing transaction design
- Reference vs. borrowable books
- Historical data preservation

---

## Part 4: NoSQL & MongoDB Introduction (35 minutes)

### Why NoSQL?

#### Limitations of Relational Databases:
- **Rigid Schema:** Difficult to modify structure
- **Vertical Scaling:** Expensive to scale up
- **Complex Joins:** Performance issues with large datasets
- **Fixed Table Structure:** Doesn't handle varied data well

#### NoSQL Advantages:
- **Flexible Schema:** Easy to modify and evolve
- **Horizontal Scaling:** Scale across multiple servers
- **Performance:** Optimized for specific use cases
- **Big Data Handling:** Better for large, unstructured datasets

### MongoDB Deep Dive

#### What is MongoDB?
MongoDB is a document-oriented NoSQL database that stores data in flexible, JSON-like documents called BSON (Binary JSON).

#### Key Features:
- **Document-Based:** Store complex data structures
- **Dynamic Schema:** No predefined structure required
- **Scalability:** Built-in sharding and replication
- **Rich Query Language:** Powerful querying capabilities
- **Indexing:** Comprehensive indexing support

#### MongoDB Data Model:

**Document Structure:**
```json
{
  "_id": ObjectId("..."),
  "name": "John Doe",
  "email": "john@example.com",
  "address": {
    "street": "123 Main St",
    "city": "Anytown",
    "zipcode": "12345"
  },
  "hobbies": ["reading", "swimming", "coding"],
  "orders": [
    {
      "orderId": "ORD001",
      "date": "2024-01-15",
      "items": ["laptop", "mouse"]
    }
  ]
}
```

#### MongoDB vs. Relational Database Concepts:

| Relational DB | MongoDB |
|---------------|---------|
| Database | Database |
| Table | Collection |
| Row | Document |
| Column | Field |
| Index | Index |
| Join | Embedded Document or Reference |

#### When to Use MongoDB:

**Good Fit:**
- Rapid application development
- Flexible, evolving schemas
- Large volumes of structured/semi-structured data
- Real-time analytics
- Content management systems
- Internet of Things (IoT) applications

**Not Ideal For:**
- Complex transactions requiring ACID properties
- Applications requiring complex joins
- Highly structured data with fixed relationships
- Applications where data consistency is critical

#### MongoDB Operations Examples:

**Insert Document:**
```javascript
db.users.insertOne({
  name: "Alice Smith",
  email: "alice@example.com",
  age: 28,
  skills: ["JavaScript", "Python", "MongoDB"]
})
```

**Query Documents:**
```javascript
// Find all users with age greater than 25
db.users.find({ age: { $gt: 25 } })

// Find users with specific skills
db.users.find({ skills: "JavaScript" })
```

**Update Document:**
```javascript
db.users.updateOne(
  { email: "alice@example.com" },
  { $set: { age: 29 }, $push: { skills: "React" } }
)
```

#### MongoDB Architecture:

**Replica Sets:**
- Primary-Secondary architecture
- Automatic failover
- Data redundancy

**Sharding:**
- Horizontal partitioning
- Distribute data across multiple servers
- Automatic load balancing

---

## Part 5: Review & Assignments (5 minutes)

### Key Takeaways:
1. **Database Types:** Each serves specific use cases
2. **ERD Design:** Systematic approach to modeling data
3. **Relationships:** Understanding cardinality is crucial
4. **NoSQL:** Flexibility vs. structure trade-offs
5. **MongoDB:** Document-based approach for modern applications

### Quick Review Questions:
1. What's the difference between strong and weak entities?
2. How do you resolve many-to-many relationships in ERD?
3. When would you choose MongoDB over a relational database?
4. What does BSON stand for and why is it used?

---

## Homework Assignment: E-Commerce Platform Design

### Scenario:
You're designing a database for a multi-vendor e-commerce platform similar to Amazon or eBay.

### Requirements:
**Part A: ERD Design (60 points)**
Create a comprehensive ERD that includes:
1. **Entities (minimum 8):** Users, Vendors, Products, Categories, Orders, Reviews, etc.
2. **Attributes:** Include appropriate data types and constraints
3. **Relationships:** Show all relationships with correct cardinality
4. **Special Cases:** Handle inventory management, shipping, and payment processing

**Specific Features to Model:**
- Multi-vendor support (vendors can sell products)
- Product categories and subcategories
- Shopping cart functionality
- Order processing and tracking
- Customer reviews and ratings
- Payment methods
- Shipping addresses (users can have multiple)
- Product variants (size, color, etc.)

**Part B: NoSQL Alternative (40 points)**
Design the same e-commerce system using MongoDB:
1. **Document Structure:** Show 3-4 key document examples
2. **Collection Design:** Explain your collection strategy

**Deliverables:**
- ERD diagram (can be hand-drawn and scanned, or use tools like Lucidchart, draw.io)
- MongoDB document examples in JSON format

**Due Date:** Next class session
**Submission:** as PDF attachment

### Evaluation Criteria:
- **Completeness:** All requirements addressed
- **Accuracy:** Correct ERD notation and relationships
- **Design Quality:** Logical and efficient design
- **MongoDB Understanding:** Appropriate document structure

---

## Additional Resources

### Online Tools:
- **ERD Design:** Lucidchart, Draw.io, ERDPlus
- **MongoDB:** MongoDB Atlas (free tier), MongoDB Compass
- **Practice:** W3Schools SQL Tutorial, MongoDB University

### Next Week Preview:
- SQL fundamentals and advanced queries
- MongoDB Practical

---

*End of Lecture - Questions & Discussion*
