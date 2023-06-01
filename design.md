# Database Design

## User Schema
- Id
- Username: String, required

## Question Schema
- Id
- question: String, required
- options: Array (null in case of select time and sleep duration)

## Answer Schema
- Id
- userId: ref to User
- questionId: ref to Question
- Answer: Mixed


# API Design

## User Registration
- Endpoint: POST /api/user
- Request body:
{
"name": "Test User"
}

- Response:
{
"token": <jwt-token>
}


## Get All Questions with options API
- Endpoint: GET /api/questions
- Request body: None
- Response:
[
{
"questionId": "xyz123",
"question": "title-of-question",
"hasOptions": true/false,
"options": [Array of options]
}
]


## Save Answer from User
- Endpoint: POST /api/answer
- Request Headers: Authorization: Bearer <token>
- Request Body:
{
"questionId": "abc123",
"answer": ["option 1", "option 3"] OR "10:00"
}

- Response: Status 201
{
"message": "Answer added successfully"
}