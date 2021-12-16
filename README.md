# Practo Backend

API documentation

## 1. install packages

```sh
npm i
```

## 2. Run The App

```sh
npm run start:dev
```

# Practo API

### Create a user Account

`POST /api/user/signup`

Request body:

    {
      "name":"hamza",
      "email":"hamza@gmail.com",
      "password":"Al123456",
      "role":"Doctor"  <-- User
    }

### Response

    {
      "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ"
    }

## Login User

`POST /api/user/signin`

Request body:

    {
      "email":"hamza@gmail.com",
      "password":"Al123456"
    }

### Response

    {
      "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ"
    }

## Update User Account

`PATCH /api/user`

Request body:

    {
      "name":"hamza",
      "email":"hamza@gmail.com",
      "username":"hamza",
      "password":"Al123456"
    }

### Response

    {
        "id": 1,
        "createdAt": "2021-10-22T21:49:48.443Z",
        "updatedAt": "2021-10-23T02:00:05.634Z",
        "email": "hamza@gmail.com",
        "username": "hamza",
        "name": "hamza",
        "role": "Doctor",
        "verified": false
    }

## Delete User Account only --> Admin,Supervisor

`DELTE /api/user/4`

Request Param /api/user/:id

### Response

    {
       User Deleted Successfully
    }

## Update User Role Only --> Admin,Supervisor

`PATCH /api/user/role`

Request body:

    {
        "id":2,
        "role":"Supervisor" <-- Admin, User, Supervisor
    }

### Response

    {
        "id": 2,
        "createdAt": "2021-10-23T07:52:21.594Z",
        "updatedAt": "2021-10-23T21:53:30.247Z",
        "email": "hamza2@gmail.com",
        "username": null,
        "name": "hamza",
        "role": "Supervisor",
        "verified": false
    }

## Get List of Users Only --> Admin,Supervisor

`GET /api/user/users`

No Request body

### Response

    [
        {
            "id": 3,
            "createdAt": "2021-10-23T15:24:07.300Z",
            "updatedAt": "2021-10-23T21:41:06.255Z",
            "email": "hamza3@gmail.com",
            "username": null,
            "name": "hamza",
            "role": "Doctor",
            "verified": false
        },
        {
            "id": 1,
            "createdAt": "2021-10-23T05:36:31.187Z",
            "updatedAt": "2021-10-23T21:44:03.151Z",
            "email": "hamza@gmail.com",
            "username": "hamza",
            "name": "hamza",
            "role": "Admin",
            "verified": false
        },
        {
            "id": 2,
            "createdAt": "2021-10-23T07:52:21.594Z",
            "updatedAt": "2021-10-23T21:53:30.247Z",
            "email": "hamza2@gmail.com",
            "username": null,
            "name": "hamza",
            "role": "Supervisor",
            "verified": false
        }
    ]
