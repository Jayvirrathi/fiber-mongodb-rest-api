# Golang Authentication API with Fiber MongoDB and JWT


```bash
# rename .env.sample to .env
# serve at http://localhost:8080

go run main.go
```

## Prerequisites

- Go
- MongoDB 

## Run Database on Docker

```bash
  docker run -it --rm --name mongodb_container -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=admin -v mongodata:/data/db -d -p 27017:27017 mongo

    docker exec -it mongodb_container /bin/bash

    mongo -u admin -p admin --authenticationDatabase admin

    use mydb

    db.createUser({user: 'user', pwd: 'password', roles:[{'role': 'readWrite', 'db': 'mydb'}]});

    # testing authentication with new user
    mongo -u user -p password --authenticationDatabase mydb

    use mydb

    show collections
```

## Run API

```bash
go run main.go
```

**Request:**

### User

```
POST signup
{
    "email":"elon@gmail.com",
    "password":"elon"
}
```

```
POST signin
{
    "email":"elon@gmail.com",
    "password":"elon"
}
```

## Authorization

### Users

```
GET users/

GET users/:id

DELETE users/:id
```

```
PUT users/
{
    "email":"elontest@gmail.com"
}
```
