# Inter Database Query Results

## Dataset Info
- Database: inter
- Collection: devices
- Total: 5 devices

## Query 16: Check if price field exists, show name and price

**Query:**
```javascript
db.devices.find(
  { price: { $exists: true } },
  { name: 1, price: 1, _id: 0 }
);
```

**Results:**
```json
[
  { "name": "IPhone", "price": 799 },
  { "name": "xTablet", "price": 899 },
  { "name": "Redmi Note", "price": 899 },
  { "name": "Samsung", "price": 699 },
  { "name": "Vivo", "price": 599 }
]
```

Found all 5 devices - they all have price info.

## Query 17: Look for profit field

**Query:**
```javascript
db.devices.find({ profit: { $exists: true } });
```

**Results:**
```json
[]
```

Empty result - no profit field in any device.

## Query 18: Find devices with price > 699

**Query:**
```javascript
db.devices.find({ price: { $gt: 699 } });
```

**Results:**
```json
[
  {
    "_id": 1,
    "name": "IPhone",
    "price": 799,
    "releaseDate": "2011-05-14T00:00:00Z",
    "spec": { "ram": 4, "screen": 6.5, "cpu": 2.66 },
    "color": ["white", "black"],
    "storage": [64, 128, 256]
  },
  {
    "_id": 2,
    "name": "xTablet",
    "price": 899,
    "releaseDate": "2011-09-01T00:00:00Z",
    "spec": { "ram": 16, "screen": 9.5, "cpu": 3.66 },
    "color": ["white", "black", "purple"],
    "storage": [128, 256, 512]
  },
  {
    "_id": 3,
    "name": "Redmi Note",
    "price": 899,
    "releaseDate": "2015-01-14T00:00:00Z",
    "spec": { "ram": 12, "screen": 9.7, "cpu": 3.66 },
    "color": ["blue"],
    "storage": [16, 64, 128]
  }
]
```

Got 3 expensive devices: IPhone (799), xTablet (899), Redmi Note (899).
Samsung is exactly 699 so doesn't count, Vivo is only 599.

---


