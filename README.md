# Fianl-Task-6

# Query
## 1. Get all documents.
- Code: db.movies.find()



# 2. Get all documents with "Writer" set to "Quentin Tarantino".
- Code: db.movies.find({writer:"Quentin Tarantino"})



# 3. Get all documents where "actor" includes Brad Pitt.
- Code: db.movies.find({actors:"Brad Pitt"})



# 4. Get all documents with "Franchise" set to "The Hobbit".
- Code: db.movies.find({franchise:"The Hobbit"})



# 5. Get all movies released in the 90s.
- Code: db.movies.find({year:{$gt:"1990", $lt:"2000"}})


# 6. Get all movies released before the year 2000 or after 2010.
- Code: db.movies.find({$or:[{year:{$gt:"2010"}},{year: {$lt:"2000"}}]})



# Documents Update
## 1. Add a synopsis to "The Hobbit An Unexpected Journey": "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home and the gold within it - from the dragon Smaug."

- Code: db.movies.update({title: "The Hobbit An Unexpected Journey"}, {$set: {synopsis: "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home and the gold within it - from the dragon Smaug."}})


## After Update:


## 2. Add a synopsis to "The Hobbit: The Desolation of Smaug": "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."

- Code: db.movies.update({title: "The Hobbit: The Desolation of Smaug"}, {$set: {synopsis: "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."}})


## After Update:


## 3. Add an actor named "Samuel L. Jackson" to the movie "Pulp Fiction"

- Code: db.movies.update({title: "Pulp Fiction"}, {$push: {actors: "Samuel L. Jackson"}})



## After Update:



# Text Search
## 1. Find all movies that have a synopsis that contains the word "Bilbo".
- Code: db.movies.find({synopsis:{$regex:"Bilbo"}})


## 2. Find all movies that have a synopsis that contains the word "Gandalf".
- Code: db.movies.find({synopsis:{$regex:"Gandalf"}})



## 3. Find all movies that have a synopsis that contains the word "Bilbo" and not the word "Gandalf".
Code: db.movies.find({$and:[{synopsis:{$regex:"Bilbo"}}, {synopsis:{$not:/Gandalf/}}]})



## 4. Find all movies that have a synopsis that contains the word "dwarves" or "hobbit".
- Code: db.movies.find({$or:[{synopsis:{$regex:"dwarves"}}, {synopsis:{$regex:"hobbit"}}]})



## 5. Find all movies that have a synopsis that contains the word "gold" and "dragon".
- Code: db.movies.find({$and:[{synopsis:{$regex:"gold"}}, {synopsis:{$regex:"dragon"}}]})


# Deleting Documents
## 1. delete the movie "Pee Wee Herman's Big Adventure".
- Code: db.movies.deleteOne ({_id: ObjectId('68280f11172fdf11a7fdf6f0')})

Text for Query 5

## 2. Delete the movie "Avatar".
- Code: db.movies.deleteOne ({_id: ObjectId('72280f91472fdf11a0fdf6f0')})

Text for Query 5

# Relationships
## Insert the following to user collection.
- Code: db.users.insertMany([{ _id: 1, username: "GoodGuyGreg", first_name: "Good Guy", last_name: "Greg" }, { _id: 2, username: "ScumbagSteve", full_name: { first: "Scumbag", last: "Steve" } }])


## After Insert Results:


## Insert the following documents into a posts collection.
- Code: db.comments.insertMany([{ username: "GoodGuyGreg", comment: "Hope you got a good deal!", post: ObjectId("68282cda172fd1a7fdf6f2") }, { username: "GoodGuyGreg", comment: "What's mine is yours!", post: ObjectId("68282cec172fd1a7fdf6f6") }, { username: "GoodGuyGreg", comment: "Don't violate the licensing agreement!", post: ObjectId("68282cf0172fd1a7fdf6f7") }])


## Insert the following documents into a comments collection.
## Code:
- db.comments.insert({username:"GoodGuyGreg", comment:"Hope you got a good deal!", post:ObjectId("5ca0b7e96435f98b5901f463")});
- db.comments.insert({username:"GoodGuyGreg", comment:"What's mine is yours!", post:ObjectId("5ca0b9706435f98b5901f46a")});
- db.comments.insert({username:"GoodGuyGreg", comment:"Don't violate the licensing agreement!", post:ObjectId("5ca0b8766435f98b5901f467")});
- db.comments.insert({username:"ScumbagSteve", comment:"It still isn't clean", post:ObjectId("5ca0b8546435f98b5901f466")});
- db.comments.insert({username:"ScumbagSteve", comment:"Denied your PR cause I found a hack", post:ObjectId("5ca0b9256435f98b5901f469")});



## Relational Afterwards:
## Final Relational Result

# Query
## 1. Find all users
- db.users.find().pretty()



## 2. Find all posts
- db.posts.find().pretty()



## 3. Find all posts authored by "GoodGuyGreg"
- db.posts.find({username: "GoodGuyGreg"})



## 4. Find all posts authored by "ScumbagSteve"
- db.posts.find({username: "ScumbagSteve"})



## 5. Find all comments
- db.comments.find().pretty()


## 6. Find all comments authored by "GoodGuyGreg"
- db.comments.find({username: "GoodGuyGreg"})



## 7. Find all comments authored by "ScumbagSteve"
- db.comments.find({username: "ScumbagSteve"})



## 8. Find all comments belonging to the post "Reports a bug in your code"
- db.comments.find({post: ObjectId("682862155750a49fa77b8e7b")})



## [BACK TO PORTFOLIO](https://tatinzzz.github.io/EDM-Portfolio/)

