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
```
school> db.students.find()
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
```
school> db.students.insertMany([{name:"Patrick",age:22,gpa:2.7},{name:"Squidward",age:33,gpa:3.5}])
```

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
### Find
You can use the find() function for queries and projection.
Similar to WHERE and SELECT in SQL.
```
school> db.students.find({age:32},{name:true})
[ { _id: ObjectId("652c3eec3f0549a30df74c2e"), name: 'Larry' } ]
```
```
school> db.students.find({age:32},{name:true,_id:false})
[ { name: 'Larry' } ]
```
### Update documents
First {} is to filter, second {} is to apply the update(s)
#### Update One
Example, to update the age of a student. If the given key does not exist, it will be created.
```
school> db.students.updateOne({name:"Spongebob"},{$set:{age:25}})
```
To delete a key in a document, where the key "isFullTime" will be deleted
```
school> db.students.updateOne({name:"Spongebob"},{$unset:{isFullTime:""}})
```
#### Update Many
If you leave the filter query blank, updates will apply to all documents
```
school> db.students.updateMany({},{$set:{isFullTime:false}})
```
Example, check if any of the documents have the "isFullTime" key and apply updates to only those documents
```
school> db.students.updateMany({isFullTime:{$exists:false}}, {$set:{isFullTime:true}})
```
### Delete documents
You put in a filter criteria in {}
#### Delete One
Deleting the student whose name is "SpongeBob"
```
school> db.students.deleteOne({name:"SpongeBob"})
```
#### Delete Many
Deleting all students who do not have the key - "registrationDate"
```
school> db.students.deleteMany({registrationDate:{$exists:false}})
```
### Comparison Operators
Find all students whose age is greater than or equal to 33
```
school> db.students.find({age:{$gte:33}})
```
```
school> db.students.find({age:{$lte:32}})
```
Multiple comparision operators in one statement
```
school> db.students.find({gpa:{$gt:3,$lte:4}}, {name:true})
```