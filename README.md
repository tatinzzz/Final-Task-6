# Fianl-Task-6 - MongoDB Practice

# Queries
## 1. Get all documents.
- Code: db.movies.find()
- ![image](https://github.com/user-attachments/assets/4bf30c69-dccd-4854-9d49-63a4c84593e9)

https://i.imgur.com/1TNR0VS.png


# 2. Get all documents with "Writer" set to "Quentin Tarantino".
- Code: db.movies.find({writer:"Quentin Tarantino"})
![image](https://github.com/user-attachments/assets/e8cb2787-4371-4607-8228-8ae9d0e64503)

https://i.imgur.com/jB1fFZ7.png

# 3. Get all documents where "actor" includes Brad Pitt.
- Code: db.movies.find({actors:"Brad Pitt"})

![image](https://github.com/user-attachments/assets/0ae108f3-9d41-4813-842e-5de5fef3fd67)

https://i.imgur.com/ywGKPBR.png

# 4. Get all documents with "Franchise" set to "The Hobbit".
- Code: db.movies.find({franchise:"The Hobbit"})

![image](https://github.com/user-attachments/assets/64529d68-89a2-4d6f-8677-799f441c5f41)

https://i.imgur.com/ZRIy2uy.png

# 5. Get all movies released in the 90s.
- Code: db.movies.find({year:{$gt:"1990", $lt:"2000"}})

https://i.imgur.com/VB1ymNm.png

![image](https://github.com/user-attachments/assets/39289e1f-e027-4d02-a2c8-41010898e12d)

# 6. Get all movies released before the year 2000 or after 2010.
- Code: db.movies.find({$or:[{year:{$gt:"2010"}},{year: {$lt:"2000"}}]})

![image](https://github.com/user-attachments/assets/6fa5c4eb-7b28-4531-9eca-7834b9b40eec)

https://i.imgur.com/HXmmCrA.png

# Documents Update
## 1. Add a synopsis to "The Hobbit An Unexpected Journey": "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home and the gold within it - from the dragon Smaug."

- Code: db.movies.update({title: "The Hobbit An Unexpected Journey"}, {$set: {synopsis: "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home and the gold within it - from the dragon Smaug."}})


![image](https://github.com/user-attachments/assets/0da8ba6b-cabc-40d8-b482-fe7a0149f2a0)

https://i.imgur.com/VB3PxkA.png

## After Update:
![image](https://github.com/user-attachments/assets/7cc17db6-b09c-4501-819a-3ef5b9210819)

https://i.imgur.com/SWa52gy.png

## 2. Add a synopsis to "The Hobbit: The Desolation of Smaug": "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."

- Code: db.movies.update({title: "The Hobbit: The Desolation of Smaug"}, {$set: {synopsis: "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."}})

https://i.imgur.com/TAbaIp4.png


![image](https://github.com/user-attachments/assets/7ed914a8-f4d5-418d-9735-6e609206a763)


## After Update:


## 3. Add an actor named "Samuel L. Jackson" to the movie "Pulp Fiction"

- Code: db.movies.update({title: "Pulp Fiction"}, {$push: {actors: "Samuel L. Jackson"}})

https://i.imgur.com/8TnKeWH.png

## After Update:
https://i.imgur.com/U7Qp8nP.png


# Text Search
## 1. Find all movies that have a synopsis that contains the word "Bilbo".
- Code: db.movies.find({synopsis:{$regex:"Bilbo"}})

https://i.imgur.com/i17i6Jd.png
## 2. Find all movies that have a synopsis that contains the word "Gandalf".
- Code: db.movies.find({synopsis:{$regex:"Gandalf"}})
https://i.imgur.com/gVAnM7x.png


## 3. Find all movies that have a synopsis that contains the word "Bilbo" and not the word "Gandalf".
Code: db.movies.find({$and:[{synopsis:{$regex:"Bilbo"}}, {synopsis:{$not:/Gandalf/}}]})

https://i.imgur.com/Kqeg2q2.png


## 4. Find all movies that have a synopsis that contains the word "dwarves" or "hobbit".
- Code: db.movies.find({$or:[{synopsis:{$regex:"dwarves"}}, {synopsis:{$regex:"hobbit"}}]})

https://i.imgur.com/khW8zYY.png

## 5. Find all movies that have a synopsis that contains the word "gold" and "dragon".
- Code: db.movies.find({$and:[{synopsis:{$regex:"gold"}}, {synopsis:{$regex:"dragon"}}]})

https://i.imgur.com/zdQwEic.png

# Deleting Documents
## 1. delete the movie "Pee Wee Herman's Big Adventure".
- Code: db.movies.deleteOne ({_id: ObjectId('68280f11172fdf11a7fdf6f0')})
https://i.imgur.com/kIip1XL.png

## 2. Delete the movie "Avatar".
- Code: db.movies.deleteOne ({_id: ObjectId('72280f91472fdf11a0fdf6f0')})
https://i.imgur.com/iAnEckl.png


# Relationships
## Insert the following to user collection.
- Code: db.users.insertMany([{ _id: 1, username: "GoodGuyGreg", first_name: "Good Guy", last_name: "Greg" }, { _id: 2, username: "ScumbagSteve", full_name: { first: "Scumbag", last: "Steve" } }])

https://i.imgur.com/QHxjbck.png
## After Insert Results:
https://i.imgur.com/e5gjp4p.png

## Insert the following documents into a posts collection.
- Code: db.comments.insertMany([{ username: "GoodGuyGreg", comment: "Hope you got a good deal!", post: ObjectId("68282cda172fd1a7fdf6f2") }, { username: "GoodGuyGreg", comment: "What's mine is yours!", post: ObjectId("68282cec172fd1a7fdf6f6") }, { username: "GoodGuyGreg", comment: "Don't violate the licensing agreement!", post: ObjectId("68282cf0172fd1a7fdf6f7") }])

https://i.imgur.com/BIqFb72.png

## Insert the following documents into a comments collection.
## Code:
- db.comments.insert({username:"GoodGuyGreg", comment:"Hope you got a good deal!", post:ObjectId("5ca0b7e96435f98b5901f463")});
- db.comments.insert({username:"GoodGuyGreg", comment:"What's mine is yours!", post:ObjectId("5ca0b9706435f98b5901f46a")});
- db.comments.insert({username:"GoodGuyGreg", comment:"Don't violate the licensing agreement!", post:ObjectId("5ca0b8766435f98b5901f467")});
- db.comments.insert({username:"ScumbagSteve", comment:"It still isn't clean", post:ObjectId("5ca0b8546435f98b5901f466")});
- db.comments.insert({username:"ScumbagSteve", comment:"Denied your PR cause I found a hack", post:ObjectId("5ca0b9256435f98b5901f469")});

https://i.imgur.com/5RMDgZa.png
https://i.imgur.com/TLzwYOY.png


## Relational Afterwards:
https://i.imgur.com/cOK8YBt.png


# Query
## 1. Find all users
- db.users.find().pretty()

https://i.imgur.com/tB1Cs8K.png

## 2. Find all posts
- db.posts.find().pretty()

https://i.imgur.com/Qvgvqr7.png

## 3. Find all posts authored by "GoodGuyGreg"
- db.posts.find({username: "GoodGuyGreg"})
https://i.imgur.com/xQBlTr0.png


## 4. Find all posts authored by "ScumbagSteve"
- db.posts.find({username: "ScumbagSteve"})
https://i.imgur.com/X5bmp5X.png


## 5. Find all comments
- db.comments.find().pretty()
https://i.imgur.com/noVf8in.png

## 6. Find all comments authored by "GoodGuyGreg"
- db.comments.find({username: "GoodGuyGreg"})

https://i.imgur.com/45dFDMS.png

## 7. Find all comments authored by "ScumbagSteve"
- db.comments.find({username: "ScumbagSteve"})

https://i.imgur.com/wiBZtM1.png

## 8. Find all comments belonging to the post "Reports a bug in your code"
- db.comments.find({post: ObjectId("682862155750a49fa77b8e7b")})
https://i.imgur.com/m3TbiTA.png


## [BACK TO PORTFOLIO](https://tatinzzz.github.io/EDM-Portfolio/)

