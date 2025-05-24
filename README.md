# MANGO MongoDB Project

MongoDB project with device and student databases demonstrating various query operations.

## Project Overview

Contains two MongoDB databases with device and student data. Implements queries demonstrating field existence checks, conditional filtering, and logical operators (OR, NOT, NOR).

## Project Structure

```
MANGO PROJECT/
├── README.md                         # Project documentation
├── LICENSE                           # MIT License
├── package.json                      # Node.js dependencies
├── .gitignore                       # Git ignore rules
├── datasets/
│   ├── inter_db_devices.json        # Inter database - Device dataset (5 records)
│   └── basicmango_db_students.json  # BasicMango database - Student dataset (6 records)
├── queries/
│   ├── inter_db_queries.mongodb     # Inter database queries (field existence, filtering)
│   └── basicmango_db_queries.mongodb # BasicMango database queries (OR, NOT, NOR operators)
└── outputs/
    ├── inter_db_results.md           # Inter database query results (readable)
    ├── inter_db_raw_outputs.json     # Inter database raw JSON outputs
    ├── basicmango_db_results.md      # BasicMango database query results (readable)
    └── basicmango_db_raw_outputs.json # BasicMango database raw JSON outputs
```

## Quick Start

### Prerequisites
- MongoDB installed
- MongoDB Compass
- Node.js (optional)

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd MANGO-PROJECT
   ```

2. **Install dependencies** (optional)
   ```bash
   npm install
   ```

3. **Import datasets using MongoDB Compass**

   **For Inter Database (Device Data):**
   - Create database: `inter`
   - Create collection: `devices`
   - Import `datasets/inter_db_devices.json`

   **For BasicMango Database (Student Data):**
   - Create database: `basicmango_db`
   - Create collection: `students`
   - Import `datasets/basicmango_db_students.json`

## 🎯 Assignment Queries

This project implements MongoDB queries demonstrating various operators and techniques:

## 📊 Dataset Information

### **Dataset 1: Inter Database (Device Data)**
**File**: `datasets/inter_db_devices.json`
- **Database**: `inter`
- **Collection**: `devices`
- **Records**: 5 devices (IPhone, xTablet, Redmi Note, Samsung, Vivo)
- **Fields**: _id, name, price, releaseDate, spec, color, storage
- **Queries**: Field existence checks, conditional filtering

### **Dataset 2: BasicMango Database (Student Data)**
**File**: `datasets/basicmango_db_students.json`
- **Database**: `basicmango_db`
- **Collection**: `students`
- **Records**: 6 students (Mukesh, Dechamma, Akash, Geetha, Bhomika, Nitin)
- **Fields**: _id, std_name, Gender, class, age, grd_point
- **Queries**: OR, NOT, NOR operators

## 🔍 Query Details

### Query 16: Price Field Existence Check
```javascript
db.devices.find(
  { price: { $exists: true } },
  { name: 1, price: 1, _id: 0 }
);
```
**Expected Result**: All 5 devices with name and price

### Query 17: Profit Field Existence Check
```javascript
db.devices.find({ profit: { $exists: true } });
```
**Expected Result**: Empty array `[]` (no profit field exists)

### Query 18: Price > 699 Filter
```javascript
db.devices.find({ price: { $gt: 699 } });
```
**Expected Result**: 3 devices (IPhone: 799, xTablet: 899, Redmi Note: 899)

## 📊 Query Results & Outputs

This project includes comprehensive output documentation:

- **`outputs/inter_db_results.md`** - Inter database query results (readable format)
- **`outputs/inter_db_raw_outputs.json`** - Inter database raw JSON outputs
- **`outputs/basicmango_db_results.md`** - BasicMango database query results (readable format)
- **`outputs/basicmango_db_raw_outputs.json`** - BasicMango database raw JSON outputs
- **Query files include inline outputs** - See actual results directly in the `.mongodb` files

### Quick Results Summary:
- ✅ **Query 16**: Found 5/5 devices with price field
- ✅ **Query 17**: Correctly returned empty array `[]` for non-existent profit field
- ✅ **Query 18**: Found 3/5 devices with price > 699

## 🛠️ Tools Used

- **MongoDB Compass** - Database management and visualization
- **VS Code MongoDB Extension** - Query development and testing
- **Node.js** - Runtime environment
- **MongoDB Driver** - Database connectivity

## 📝 Usage Instructions

1. **Run Queries in VS Code**:
   - Open `queries/assignment-queries.mongodb`
   - Select query and press `Ctrl+Shift+R`

2. **Run Queries in MongoDB Compass**:
   - Navigate to `devices_db` → `devices`
   - Use the query bar or Aggregations tab


