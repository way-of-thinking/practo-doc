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
      "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ",
      "success": "please verify your email address"
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

`PATCH /api/user/role/2`

Request Param /api/user/role/:id

Request body:

    {
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

### Create a Admin Account

`POST /api/user/admin-signup`

Request body:

    {
        "name":"hamza",
        "email":"hamza5@gmail.com",
        "password":"Al123456",
        "role":"Admin",
        "secret":"Ht=MuEADDMuU=h@!g6252qs!xGT4=M%ME"
    }

### Response

    {
      "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ"
    }

### Forgot Password Request

`POST /api/user/forgot`

Request body:

    {
     "email":"hamza@gmail.com"
    }

### Response

    {
     "success": "password reset link has been sent to your email"
    }

### Reset Password

`POST /api/user/reset-password/:code` <- 84a07ff4

Request Param /api/user/reset-password/:code

Request body:

    {
     "password":"Al123456",
     "passwordConfirm":"Al123456"
    }

### Response

    {
     "success": "Password Reset successfully"
    }

## Create or Update Doctor Profile --> Doctor

`PUT /api/profile/create-or-update-doctor`

Request body:

    {
        "phone":"017123456789100",
        "designation":"Doctor update",
        "bio":"cardiologist update",
        "about":"Osteopaths Doctors of osteopathic medicin(DO) are fully"
    }

### Response

    {
        "phone": "017123456789100",
        "designation": "Doctor update",
        "bio": "cardiologist update",
        "about": "Osteopaths Doctors of osteopathic medicine (DO) are ",
        "user": 3,
        "picture": "18d60de7-037a-4442-a6bf-58124273fef0",
        "id": 42,
        "createdAt": "2021-11-05T07:31:08.547Z",
        "updatedAt": "2021-11-05T07:31:08.547Z",
        "medicalRegistrationVerified": false,
        "numVote": 0
    }

## Doctor Avatar --> Doctor

`PUT /api/profile/doctor-avatar`

Request body: form-data

    {
        key:"img"
        value:"file"
    }

### Response

    {
        "pic": "https://practoo.s3.amazonaws.com/18d60de7-037a-4442-a6bf-58124273fef0"
    }

## Verification Label Create Or Update --> Doctor

`PUT /api/profile/verification-create-or-update`

Request body:

    {
        "title":"ths is title",
        "firstName":"this is firstName",
        "lastName":"this is lastName",
        "dateOfBirth":"2000-06-31",
        "gender":"Male",
        "nidPassport":"UK9293",
        "registerIdMBDC":"0094UBUO",
        "MedicalDegreeOrDiploma":"Diploma"
    }

### Response

    {
        "id": 8,
        "title": "ths is title",
        "firstName": "this is firstName",
        "lastName": "this is lastName",
        "dateOfBirth": "2000-06-31",
        "gender": "Male",
        "nidPassport": "UK9293",
        "registerIdMBDC": "0094UBUO",
        "MedicalDegreeOrDiploma": "Diploma"
    }

## Upload Medical Degree Transcript Image --> Doctor

### Verification Documents

`PUT /api/profile/verification-medical-dgree`

Request body: form-data

    {
        key:"img"
        value:"file"
    }

### Response

    {
        "pic": "https://practoo.s3.amazonaws.com/18d60de7-037a-4442-a6bf-58124273fef0"
    }

## Upload Internship Image --> Doctor

### Verification Documents

`PUT /api/profile/verification-internship`

Request body: form-data

    {
        key:"img"
        value:"file"
    }

### Response

    {
        "pic": "https://practoo.s3.amazonaws.com/18d60de7-037a-4442-a6bf-58124273fef0"
    }

## Upload Post Graduate Training Image --> Doctor

### Verification Documents

`PUT /api/profile/verification-post-gra-training`

Request body: form-data

    {
        key:"img"
        value:"file"
    }

### Response

    {
        "pic": "https://practoo.s3.amazonaws.com/18d60de7-037a-4442-a6bf-58124273fef0"
    }

## Upload Specialty Certificate Image --> Doctor

### Verification Documents

`PUT /api/profile/verification-specialty-certificate`

Request body: form-data

    {
        key:"img"
        value:"file"
    }

### Response

    {
        "pic": "https://practoo.s3.amazonaws.com/18d60de7-037a-4442-a6bf-58124273fef0"
    }

## Upload Medical License Or Registration Image --> Doctor

### Verification Documents

`PUT /api/profile/verification-medical-license-or-registration`

Request body: form-data

    {
        key:"img"
        value:"file"
    }

### Response

    {
        "pic": "https://practoo.s3.amazonaws.com/18d60de7-037a-4442-a6bf-58124273fef0"
    }

### Get Verifications --> Admin, Supervisor

`POST /api/profile/get-verifications?page=1&limit=10&status=Done`

    Request Param page, limit, status

### Response

    {
        "verifications": [
            {
                "id": 8,
                "createdAt": "2021-11-07T10:47:20.382Z",
                "updatedAt": "2021-11-07T10:50:04.626Z",
                "title": "ths is title",
                "firstName": "this is firstName",
                "lastName": "this is lastName",
                "dateOfBirth": "2000-06-31",
                "gender": "Male",
                "nidPassport": "UK9293",
                "registerIdMBDC": "0094UBUO",
                "MedicalDegreeOrDiploma": "Diploma",
                "status": "Pending"
            },
            {
                "id": 9,
                "createdAt": "2021-11-08T10:50:27.516Z",
                "updatedAt": "2021-11-08T10:50:27.516Z",
                "title": "ths is title",
                "firstName": "this is firstName",
                "lastName": "this is lastName",
                "dateOfBirth": "2000-06-31",
                "gender": "Male",
                "nidPassport": "UK9293",
                "registerIdMBDC": "0094UBUO",
                "MedicalDegreeOrDiploma": "Diploma",
                "status": "Pending"
            }
        ],
        "verificationsCount": 2
    }

### Doctor Verification Label --> Admin, Supervisor

`PATCH /api/profile/verifed-doctor-varification-label/8?status=Progressing`

    Request Param --> id, status=Progressing,Done

### Response

    {
        "success": "Verification Label  Progressing"
    }
    {
        "success": "Doctor Profile Verified Successfully"
    }

### Get Verification Details --> Admin, Supervisor

`GET /api/profile/get-verification-details/8`

    Request Param --> id

### Response

    {
        "verificationDocument": {
            "id": 2,
            "createdAt": "2021-11-08T00:02:26.413Z",
            "updatedAt": "2021-11-08T00:29:46.740Z",
            "MedicalDegreeTrascript": "https://practoo.s3.amazonaws.com/06fb5d5f-5745-4c10-abd7-f3d8f8c25f3b",
            "internship": "https://practoo.s3.amazonaws.com/9a4435a1-1cd2-4cd1-938b-9e94aa90308c",
            "postgraduationTraining": "https://practoo.s3.amazonaws.com/9ec78510-fe25-442e-975c-635c37c581a9",
            "SpecialityCertificate": "https://practoo.s3.amazonaws.com/ab30d2b8-dcc5-4697-80d7-667a0e363f82",
            "medicalLicenseOrRegistration": "https://practoo.s3.amazonaws.com/c3ca45b6-8605-4205-b728-d8746b94c8b8"
        },
        "verificationLabel": {
            "id": 8,
            "createdAt": "2021-11-07T10:47:20.382Z",
            "updatedAt": "2021-11-09T01:39:24.885Z",
            "title": "ths is title 8",
            "firstName": "this is firstName",
            "lastName": "this is lastName",
            "dateOfBirth": "2000-06-31",
            "gender": "Male",
            "nidPassport": "UK9293",
            "registerIdMBDC": "0094UBUO",
            "MedicalDegreeOrDiploma": "Diploma",
            "status": "Progressing",
            "doctorProfile": {
                "id": 42,
                "createdAt": "2021-11-05T07:31:08.547Z",
                "updatedAt": "2021-11-09T01:39:24.846Z",
                "phone": "017123456789100",
                "designation": "Doctor update",
                "bio": "cardiologist update",
                "about": "Osteopaths Doctors of osteopathic medicine (DO) are fully licensed medical update",
                "picture": "https://practoo.s3.amazonaws.com/18d60de7-037a-4442-a6bf-58124273fef0",
                "medicalRegistrationVerified": false,
                "numVote": 0
            }
        },
        "doctor": {
            "id": 42,
            "createdAt": "2021-11-05T07:31:08.547Z",
            "updatedAt": "2021-11-09T01:39:24.846Z",
            "phone": "017123456789100",
            "designation": "Doctor update",
            "bio": "cardiologist update",
            "about": "Osteopaths Doctors of osteopathic medicine (DO) are fully licensed medical update",
            "picture": "https://practoo.s3.amazonaws.com/18d60de7-037a-4442-a6bf-58124273fef0",
            "medicalRegistrationVerified": false,
            "numVote": 0
        }
    }

## Create a medical --> User

### User Dashboard

`POST /api/medical/create-medical`

Request body:

    {
        "isClinic":true,
        "name":"name of medical",
        "location":"medical location",
        "description":"medical description",
        "phone":"0178888888899",
        "phone_description":"phone_description",
        "to":"2018-01-01T00:00:00.000Z",
        "from":"2018-01-01T00:00:00.000Z",
        "day":["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
    }

### Response

    {
        "isClinic": true,
        "name": "name of medical",
        "location": "medical location",
        "description": "medical description",
        "phone": "0178888888899",
        "phone_description": "phone_description",
        "to": "2018-01-01T00:00:00.000Z",
        "from": "2018-01-01T00:00:00.000Z",
        "day": [
            "Mon",
            "Tue",
            "Wed",
            "Thu",
            "Fri",
            "Sat",
            "Sun"
        ],
        "service": {
            "id": 1,
            "createdAt": "2021-11-09T04:43:42.701Z",
            "updatedAt": "2021-11-09T04:43:42.701Z"
        },
        "id": 9,
        "createdAt": "2021-11-18T18:20:14.899Z",
        "updatedAt": "2021-11-18T18:20:14.899Z",
        "medical_img": "",
        "clinic_votes": 0,
        "clinic_Rating": 0,
        "numDoctors": 0
    }

## Update a medical --> User

### User Dashboard

`PATCH /api/medical/update-medical/10`

Request Param --> id

Request body:

    {
        "isClinic":true,
        "name":"name of medical",
        "location":"medical location",
        "description":"medical description",
        "phone":"0178888888899",
        "phone_description":"phone_description",
        "to":"2018-01-01T00:00:00.000Z",
        "from":"2018-01-01T00:00:00.000Z",
        "day":["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
    }

### Response

    {
        "isClinic": true,
        "name": "name of medical",
        "location": "medical location",
        "description": "medical description",
        "phone": "0178888888899",
        "phone_description": "phone_description",
        "to": "2018-01-01T00:00:00.000Z",
        "from": "2018-01-01T00:00:00.000Z",
        "day": [
            "Mon",
            "Tue",
            "Wed",
            "Thu",
            "Fri",
            "Sat",
            "Sun"
        ],
        "service": {
            "id": 1,
            "createdAt": "2021-11-09T04:43:42.701Z",
            "updatedAt": "2021-11-09T04:43:42.701Z"
        },
        "id": 9,
        "createdAt": "2021-11-18T18:20:14.899Z",
        "updatedAt": "2021-11-18T18:20:14.899Z",
        "medical_img": "",
        "clinic_votes": 0,
        "clinic_Rating": 0,
        "numDoctors": 0
    }

## Upload Medical Image --> User

### User Dashboard

`PUT /api/medical/medical-image/10`

Request Param Medical Id --> id

Request body: form-data

    {
        key:"img"
        value:"file"
    }

### Response

    {
         "pic": "https://res.cloudinary.com/db3vfaosa/image/upload/v1637610926/practo/flujudabwxd9jilo95yd.png"
    }

## Upload Medical Gallary Image 1 and Update Image and Delete By Query Params --> User

### User Dashboard

`PUT /api/medical/image-1/10`

`PUT /api/medical/image-1/10?remove=DELETE`

Request Param Medical Id --> id

Request Query Param remove --> DELETE

### please make sure when delete the image not upload any image required

Request body: form-data

    {
        key:"img"
        value:"file"
    }

### Response

    {
         "pic": "https://res.cloudinary.com/db3vfaosa/image/upload/v1637610926/practo/flujudabwxd9jilo95yd.png"
    }

### Delete Image Response

    {
         "result": "ok"
    }

## Upload Medical Gallary Image 2 and Update Image and Delete By Query Params --> User

### User Dashboard

`PUT /api/medical/image-2/10`

`PUT /api/medical/image-2/10?remove=DELETE`

Request Param Medical Id --> id

Request Query Param remove --> DELETE

### please make sure when delete the image not upload any image required

Request body: form-data

    {
        key:"img"
        value:"file"
    }

### Response

    {
         "pic": "https://res.cloudinary.com/db3vfaosa/image/upload/v1637610926/practo/flujudabwxd9jilo95yd.png"
    }

### Delete Image Response

    {
         "result": "ok"
    }

## Upload Medical Gallary Image 3 and Update Image and Delete By Query Params --> User

### User Dashboard

`PUT /api/medical/image-3/10`

`PUT /api/medical/image-3/10?remove=DELETE`

Request Param Medical Id --> id

Request Query Param remove --> DELETE

### please make sure when delete the image not upload any image required

Request body: form-data

    {
        key:"img"
        value:"file"
    }

### Response

    {
         "pic": "https://res.cloudinary.com/db3vfaosa/image/upload/v1637610926/practo/flujudabwxd9jilo95yd.png"
    }

### Delete Image Response

    {
         "result": "ok"
    }

## Upload Medical Gallary Image 4 and Update Image and Delete By Query Params --> User

### User Dashboard

`PUT /api/medical/image-4/10`

`PUT /api/medical/image-4/10?remove=DELETE`

Request Param Medical Id --> id

Request Query Param remove --> DELETE

### please make sure when delete the image not upload any image required

Request body: form-data

    {
        key:"img"
        value:"file"
    }

### Response

    {
         "pic": "https://res.cloudinary.com/db3vfaosa/image/upload/v1637610926/practo/flujudabwxd9jilo95yd.png"
    }

### Delete Image Response

    {
         "result": "ok"
    }

