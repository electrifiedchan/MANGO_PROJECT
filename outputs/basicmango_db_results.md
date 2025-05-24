# BasicMango Database Query Results

## Dataset Info
- Database: basicmango_db
- Collection: students
- Total: 6 students
- Fields: _id, std_name, Gender, class, age, grd_point

## Query 29: Find females OR students 20+ years old

**Query:**
```javascript
db.students.find({
  $or: [
    { Gender: "Female" },
    { age: { $gte: 20 } }
  ]
});
```

**Results:**
```json
[
  {
    "_id": 2,
    "std_name": "Dechamma",
    "Gender": "Female",
    "class": "VI",
    "age": 13,
    "grd_point": 30
  },
  {
    "_id": 4,
    "std_name": "Geetha",
    "Gender": "Female",
    "class": "X",
    "age": 17,
    "grd_point": 36.2514
  },
  {
    "_id": 5,
    "std_name": "Bhomika",
    "Gender": "Female",
    "class": "X",
    "age": 19,
    "grd_point": 35.5201
  }
]
```

Got 3 students - all the girls. No one is 20+ years old.

---

##  Query 30: Display Records Where grd_point >=36 or Gender=Male (OR Operator)

### Query:
```javascript
db.students.find({
  $or: [
    { grd_point: { $gte: 36 } },
    { Gender: "Male" }
  ]
});
```

### Output:
```json
[
  {
    "_id": 1,
    "std_name": "Mukesh",
    "Gender": "Male",
    "class": "VI",
    "age": 11,
    "grd_point": 33
  },
  {
    "_id": 3,
    "std_name": "Akash",
    "Gender": "Male",
    "class": "V",
    "age": 14,
    "grd_point": 35.1257
  },
  {
    "_id": 4,
    "std_name": "Geetha",
    "Gender": "Female",
    "class": "X",
    "age": 17,
    "grd_point": 36.2514
  },
  {
    "_id": 6,
    "std_name": "Nitin",
    "Gender": "Male",
    "class": "V",
    "age": 16,
    "grd_point": 35.5201
  }
]
```

###  Result Analysis:
- **Documents Found**: 4 out of 6
- **Reason**: 3 males (Mukesh, Akash, Nitin) + 1 female with grd_point >=36 (Geetha)

---

##  Query 31: Demonstrate NOT Operator (Opposite of Age>=15)

### Query:
```javascript
db.students.find({
  age: { $not: { $gte: 15 } }
});
```

### Output:
```json
[
  {
    "_id": 1,
    "std_name": "Mukesh",
    "Gender": "Male",
    "class": "VI",
    "age": 11,
    "grd_point": 33
  },
  {
    "_id": 2,
    "std_name": "Dechamma",
    "Gender": "Female",
    "class": "VI",
    "age": 13,
    "grd_point": 30
  },
  {
    "_id": 3,
    "std_name": "Akash",
    "Gender": "Male",
    "class": "V",
    "age": 14,
    "grd_point": 35.1257
  }
]
```

###  Result Analysis:
- **Documents Found**: 3 out of 6
- **Reason**: Students with age < 15 (Mukesh: 11, Dechamma: 13, Akash: 14)

---

##  Query 32: NOT Operator - Gender Not Equal To Female

### Query:
```javascript
db.students.find({
  Gender: { $ne: "Female" }
});
```

### Output:
```json
[
  {
    "_id": 1,
    "std_name": "Mukesh",
    "Gender": "Male",
    "class": "VI",
    "age": 11,
    "grd_point": 33
  },
  {
    "_id": 3,
    "std_name": "Akash",
    "Gender": "Male",
    "class": "V",
    "age": 14,
    "grd_point": 35.1257
  },
  {
    "_id": 6,
    "std_name": "Nitin",
    "Gender": "Male",
    "class": "V",
    "age": 16,
    "grd_point": 35.5201
  }
]
```

###  Result Analysis:
- **Documents Found**: 3 out of 6
- **Reason**: All male students (Mukesh, Akash, Nitin)

---

##  Query 33: Demonstrate NOR Operator

### Query:
```javascript
db.students.find({
  $nor: [
    { Gender: "Female" },
    { age: { $gte: 15 } }
  ]
});
```

### Output:
```json
[
  {
    "_id": 1,
    "std_name": "Mukesh",
    "Gender": "Male",
    "class": "VI",
    "age": 11,
    "grd_point": 33
  },
  {
    "_id": 3,
    "std_name": "Akash",
    "Gender": "Male",
    "class": "V",
    "age": 14,
    "grd_point": 35.1257
  }
]
```

### Result Analysis:
- **Documents Found**: 2 out of 6
- **Reason**: Students who are NOT Female AND NOT age>=15 (Male students under 15)

---


