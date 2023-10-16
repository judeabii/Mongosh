# Mongosh
A journal to document the learning od MongoDB using mongosh 
### Creating a deleting a database
To create a database, where the name of the database is school:
```test> use school```

To drop the database:
```school> db.dropDatabase()```
### Create a collection
```school> db.createCollection("students")```
### Inserting documents into a collection
```school> db.students.insertOne({name:"Spongebob",age:21,gpa:3.2})```

To view the documents:
```school> db.students.find()
[  
  {
    _id: ObjectId("652c3d933f0549a30df74c2b"),
    name: 'Spongebob',
    age: 21,
    gpa: 3.2
  }
]
```

Inserting Many:
```school> db.students.insertMany([{name:"Patrick",age:22,gpa:2.7},{name:"Squidward",age:33,gpa:3.5}])```
<<<<<<< HEAD

All documents in the collection need not have the same keys. You can also store values as the date, null - for placeholder, array or list and nested document
```
school> db.students.insertOne({name:"Larry",
... age:32,
... gpa:2.8,
... isFullTime:false,
... registerDate:new Date(),
... graduationDate:null,
... courses:["Biology","Chemistry","Math"],
... address:{street:"Nick street",
... city:"Bottom",
... zipCode:123456}
... })
```
### Sorting and Limit
"1" to sort in ascending order and "-1" for descending order.
You can limit the number of results obtained too, eg, onlt the top 2 youngest students:
```
school> db.students.find().sort({age:1}).limit(2)
```
=======
>>>>>>> f4d6f301b7ac0d9f1ce6f0e9882e4e0f30804dc6
