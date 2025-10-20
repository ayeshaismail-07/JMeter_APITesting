# JMeter_APITesting
# API Testing in JMeter – CRUD Operations with CSV Data

This project demonstrates API automation using "Apache JMeter" for CRUD (Create, Read, Update, Delete) operations on a public REST API.
It also implements "CSV Data-Driven Testing" to automate multiple POST requests dynamically.

---

## 1️⃣ Objective

The purpose of this project is to build an executable JMeter test plan that:

* Simulates user interaction with REST APIs.
* Automates the full CRUD workflow: POST → GET → PATCH → DELETE → GET.
* Uses CSV input data for POST requests.
* Validates API responses with Assertions.

---

## 2️⃣ Why JSONPlaceholder API

[JSONPlaceholder](https://jsonplaceholder.typicode.com) is a "free online fake REST API" designed for testing and prototyping.
It’s ideal for this assignment because:

* No authentication or tokens are required.
* All CRUD HTTP methods are supported (GET, POST, PUT, PATCH, DELETE).
* It allows data submission through JSON payloads.
* Safe to use — no real database or sensitive data involved.

Although JSONPlaceholder returns success responses, it "does not persist data".
That means any POST, PATCH, or DELETE request returns a mock success message but does not modify real data.

---

## 3️⃣ Understanding Post IDs (1–100)

JSONPlaceholder hosts "100 static posts" (IDs 1–100).
These are sample posts that never change, even if you send update or delete requests.
When you create a new post, the API responds with an "auto-generated ID = 101",
but that record exists only in the response — it is not stored permanently.

---

## 4️⃣ CSV Data-Driven Testing

A CSV file named "post-data.csv" is used to drive multiple POST requests dynamically.
Example file:

```
userId,title,body
1,First Title,Body One
2,Second Title,Body Two
3,Third Title,Body Three
```

Each iteration sends a POST request with unique data values from the CSV file.
JMeter reads these values using "CSV Data Set Config" and replaces variables in the request body.

---

## 5️⃣ CRUD Workflow

1. **POST** → Creates a mock post using CSV data.
2. **GET** → Retrieves the created post (static or mocked).
3. **PATCH** → Updates a field such as the post title.
4. **DELETE** → Deletes the post (returns 200 OK, not actually deleted).
5. **GET** → Confirms deletion (JSONPlaceholder still returns 200 due to mock behavior).

Assertions check for response codes "200", "201" or "404", depending on the step.

---

## 6️⃣ Folder Structure

```
JMeter_CRUD_Assignment/
├── CRUD_TestPlan.jmx
├── README.md
└── post-data.csv
```

Both `.jmx` and `.csv` files are kept in the same directory for portability.

---

## 7️⃣ Conclusion

This project successfully demonstrates:

* Building and executing JMeter test plans.
* Using CSV data-driven testing.
* Automating CRUD operations on REST APIs.
* Handling mock API behavior and response validation.

JSONPlaceholder provides an excellent environment for learning API automation while ensuring no real data is modified.
