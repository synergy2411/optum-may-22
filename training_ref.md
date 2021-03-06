# Breaks
Tea Break - 11:30 - 11:50 (20Minutes)
Lunch Break - 01:30 - 02:20 (50 Minutes) 
Tea Break - 04:00 - 04:20 (20 Minutes)


# Node Installer -
- Node Runtime Environment
- Node Package Manager (NPM)
- Node Core Modules



REST API -> /api/books

isbn
name
author
page


isbn
name

GraphQL -> 
books { isbn name }


Employee - empName, empNumber, reportingTo

employee {
    empName
    reportingTo {
        manageName
        managerRank
    }
    subordinates {
        name
        rank
    }
}

# npm init -y

# GraphQL Basics
- apollo-server
- graphql


# Scalar Types - holds only one Value
- String
- Boolean
- Int
- Float
- ID ->


# to install nodemon
- npm i nodemon -g

# to run the project
- npm run start

# GraphQL Operations-
- Queries : to fetch the data
- Mutations : to create create, update and delete
- Subscriptions : to get the realtime updates
    : WebSocket : bi-directional full duplex Communication
    : PubSub : Publish/Subscribe

# Mutation (User Post Comment)
- Create
- Update
- Delete

> npm i uuid

# Subscription

# MongoDB Integration

# Authentication using JWT



# Queries
- USER
query {
users {
  id
  name
  email
  age
  posts {
    id
    title
  }
  comments {
    id
    text
  }
}
}

- POST
query {
  posts {
    id
    title
    body
    published
    author {
      name
    }
    comments {
      id
      text
      creator {
        name
      }
    }
  }
}

- Comment
query{
  comments {
    id
    text
    creator {
      id
      name
    }
    post{
      id
      title
      author {
        name
      }
    }
  }
}


# Mutation
- CreateUser
mutation {
  createUser(name : "sumit K", email: "sumit@test"){
    id
    name
    email
    age
  }
}

- CreatePost
mutation{
  createPost(data : {
    title : "New Title 2",
    body:"...",
    authorId : "102"
    published : true
  }){
    id
    title
    body
    published
  }
}

- CreateComment
mutation {
  createComment(data : {
    text : "My New Comment",
    authorId : "101",
    postId : "204"
  }){
    id
    text
  }
}

- DeleteUser
mutation{
  deleteUser(userId : "103"){
    id
    name
  }
}

- DeletePost
mutation{
  deletePost(postId : "201"){
    id
    title
  }
}

- DeleteComment
mutation {
  deleteComment(id: "301"){
    id
    text
  }
}

- UpdateUser
mutation{
  updateUser(userId : "103", data : {
     email : "new@test.com"
     }){
    id name email age
  }
}



# Subscription
> npm install
> npm install graphql-ws ws @graphql-tools/schema apollo-server-core
> npm install express apollo-server-express
> npm install graphql-subscriptions

- Single Endpoint - /graphql

query {
  employees(id: "") {
    empName
    empAddress
  }
}

- REST API : Multiple Endpoints
> GET - /api/employees
> GET - /api/employees/:id
> POST - /api/employees


> npm i mongoose -> ODM form MongoDB

# Mongoose - connect(URL)
MongoDB Connection /db/index.js

# Model/Schema
UserModel -> userSchema /model/user.model.js

# CreateUser Mutation
/graphql - CreateUser(name, email, password)
UserModel.save(name, email, password)

- CREATE
mutation {
  createUser(data : {
    name : "john",
    email : "john@test",
    password: "jon123"
  }){
    _id 
    name
    email
    password
  }
}

- READ
query{
  users {
    _id
    name
    email
    password
    age
  }
}

- UPDATE
mutation($updateUserId: ID!){
  updateUser(id: $updateUserId, data : {
    age : 32,
    name : "Alice Doe"
  }) {
    _id
    name
    age
  }
}

- DELETE
mutation($deleteUserId: ID!) {
  deleteUser(id: $deleteUserId) {
    _id name 
  }
}


# Authentication (JWT)

# Run GraphQL Queries in browser

# Test GraphQL Queries
- @apollo/client (fetch API)
- graphql
- react
- cross-fetch
- jest

# Deployment steps (Heroku)
- Make app deployable ready
  > write the "start" script in package.json
  > make the PORT dynamic -> process.env.PORT || 4044
  > local MongoDB instance -> Migrate to Mongo Cloud Version (Mongo Atlas)
- Project upload on GIT
- create account on Heroku
- download heroku cli -> npm run heroku -g
- heroku commands
  > heroku login
  > optional step 
    -> open Powershell 
    -> ssh-keygen
  > heroku keys:add
  > heroku create sk-optum-graphql
  > git remote
  > git push heroku main












- Login Query
query{
  login(data: {
    email: "alice@test",
    password:"alice123"
  }){
    token,
    user {
      _id
    name
    email
    password
    }
  }
}


- CreateUser
mutation{
  createUser(data : {
    name : "alice",
    email : "alice@test",
    password : "alice123"
  }){
    _id
    name
    email
    password
  }
}

- Query Users
query{
  users {
    _id
    email
    password
    posts {
     ...postFields
    }
  }
}

fragment postFields on Post{
  _id
  title
  body
  published
}


- CreatePost
mutation{
  createPost(data : {
    title:"New Post 101",
    body: "....",
    authorId : "628489a9e053500115779e79"
  }){
    ...postFields
  }
}

fragment postFields on Post{
  _id
  title
  body
  published
}

- Post Query
query{
  posts{
    ...postFields,
    author {
      _id
      name
      email
    }
  }
}

fragment postFields on Post{
  _id
  title
  body
  published
}

- Delete User
mutation{
  deleteUser {
    _id
    name
    email
  }
}


# Create UI to consume GraphQL API
- @apollo/client
- react
- graphql

- XHR Request - REST API
- axios - REST API
- jQuery - REST API
- fetch - REST API



- GraphQL ORM - PRISMA
- ProgresSQL
- ORacle
- MySQL
- MongoDB
- Sqlite