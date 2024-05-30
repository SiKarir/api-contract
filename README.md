# SiKarir API Contract

`BASE_URL` = `https://example.com/api`

# Features

## User
---

### Register
* **URL** <br>
`/register`

* **Method** <br>
`POST`

* **Request Body** <br>
`username` as `string`, must be unique <br>
`name` as `string` <br>
`email` as `string`, must be unique <br>
`password` as `string`, must be at least 8 characters

* **Response** <br>
```
{
  "error": false,
  "message": "User Created"
}
```

### Login
* **URL** <br>
`/login`

* **Method** <br>
`POST`

* **Request Body** <br>
`username` as `string` <br>
`password` as `string`

* **Response** <br>
```
{
    "error": false,
    "message": "success",
    "loginResult": {
        "userId": "user-yj5pc_LARC_AgK61",
        "name": "Arif Faizin",
        "isTakenQuiz": false
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiJ1c2VyLXlqNXBjX0xBUkNfQWdLNjEiLCJpYXQiOjE2NDE3OTk5NDl9.flEMaQ7zsdYkxuyGbiXjEDXO8kuDTcI__3UjCwt6R_I"
    }
}
```

### Edit Account
* **URL** <br>
`/edit-account`

* **Method** <br>
`PUT`

* **Request Body** <br>
`username` as `string`, must be unique <br>
`name` as `string` <br>
`email` as `string`, must be unique <br>
`password` as `string`, must be at least 8 characters
* **Response** <br>
```
{
  "error": false,
  "message": "User Updated"
}
```


## Catalog
---

### Get All Careers
* **URL** <br>
`/catalog/careers`

* **Method** <br>
`GET`

* **Headers** <br>
`Authorization`: `Bearer <token>`

* **Paramaters** <br>
`page` as `int`, optional <br>
`size` as `int`, optional

* **Response** <br>
```
{
  "error": false,
  "message": "Careers fetched successfully",
  "listCareer": [
    {
      "id": "career-FvU4u0Vp2S3PMsFg",
      "name": "Software Engineer",
      "description": "Lorem Ipsum",
      "photoUrl": "https://story-api.dicoding.dev/images/stories/photos-1641623658595_dummy-pic.png",
      "listJurusanTerkait": [
        {
          "id": "major-FvU4u0Vp2S3PMsFg",
          "name": "S1 Sistem Informasi",
          "description": "Lorem Ipsum",
          "photoUrl": "https://story-api.dicoding.dev/images/stories/photos-1641623658595_dummy-pic.png"
        }
      ]
    }
  ]
}
```

### Get All Majors
* **URL** <br>
`/catalog/majors`

* **Method** <br>
`GET`

* **Headers** <br>
`Authorization`: `Bearer <token>`

* **Paramaters** <br>
`page` as `int`, optional <br>
`size` as `int`, optional

* **Response** <br>
```
{
  "error": false,
  "message": "Majors fetched successfully",
  "listMajor": [
    {
      "id": "major-FvU4u0Vp2S3PMsFg",
      "name": "S1 Sistem Informasi",
      "description": "Lorem Ipsum",
      "photoUrl": "https://story-api.dicoding.dev/images/stories/photos-1641623658595_dummy-pic.png",
      "listUniversitasTerkait": [
        {
          "name": "Fakultas Ilmu Komputer Universitas Indonesia"
        }
      ]
    }
  ]
}
```

## Quiz
---

### Get Quiz By UserID
* **URL** <br>
`/quiz/user/:id`

* **Method** <br>
`GET`

* **Headers** <br>
`Authorization`: `Bearer <token>`

* **Response** <br>
```
{
  "error": false,
  "message": "Quiz fetched successfully",
  "listResultQuiz": [
    {
      "id": "quiz-FvU4u0Vp2S3PMsFg",
      "quizDate": "2024-05-30",
      "result": "Cognitive abilities allow you to do reasoning, problem solving, planning, abstract thinking, and critical thinking. In the workplace, you can use these skills to process information and make sound judgements, understand instructions, and finding solutions to potential problems.",
      "listCareer": [
        {
          "id": "career-FvU4u0Vp2S3PMsFg",
          "name": "Software Engineer",
          "description": "Lorem Ipsum",
          "photoUrl": "https://story-api.dicoding.dev/images/stories/photos-1641623658595_dummy-pic.png",
          "listJurusanTerkait": [
            {
              "id": "major-FvU4u0Vp2S3PMsFg",
              "name": "S1 Sistem Informasi",
              "description": "Lorem Ipsum",
              "photoUrl": "https://story-api.dicoding.dev/images/stories/photos-1641623658595_dummy-pic.png"
            }
          ]
        }
      ]
    }
  ]
}
```

### Get Quiz Questions
* **URL** <br>
`/quiz`

* **Method** <br>
`GET`

* **Headers** <br>
`Authorization`: `Bearer <token>`

* **Response** <br>
```
{
  "error": false,
  "message": "Quiz fetched successfully",
  "listQuiz": [
    {
      "id": "quiz-1",
      "question": [
        "Lorem Ipsum?",
        "Lorem Ipsum?"
      ],
      "userAnswer": [
        0,
        1
      ]
    }
  ]
}
```

### Post Quiz Answer
* **URL** <br>
`/quiz`

* **Method** <br>
`POST`

* **Headers** <br>
`Authorization`: `Bearer <token>`

* **Parameter** <br>
`listUserAnswer` as `list[int]`

* **Response** <br>
```
{
  "error": false,
  "message": "success"
}
```
