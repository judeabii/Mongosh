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
