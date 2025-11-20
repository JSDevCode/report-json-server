# JSON-Server Technical Guide

## Overview

This is an example project and a technical guide for running a JSON-server as a mock API. It provides a simple setup to quickly test REST API calls without a real backend.

It is useful for testing when the backend code is not written or fully developed yet, or simply to quickly experiment without affecting your real database. It starts a mock API server based on the `db.json` file.

## Contents

- [Purpose](#purpose)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Example Data](#example-data)
- [Usage](#usage)
- [Pros](#pros)
- [Cons](#cons)
- [Conclusion](#conclusion)
- [Notes](#notes)
- [References](#references)

## Purpose

The purpose of this technical report is to demonstrate how to:

- Set up JSON-server in a project.
- Create a `db.json` with example data
- Make HTTP requests (GET, POST, PUT, DELETE) to a mock API
- Serve as a reference for testing frontend applications, learning REST, and experimenting with API routes.

## Prerequisites

- `Node.js` installed on your machine.

## Getting Started

1. Open a terminal in the folder where you want the project.

2. Clone the repository:

```
git clone git@github.com:JSDevCode/report-json-server.git
```

3. Change directory into the project:

```
cd report-json-server
```

4. Install dependencies:

```
npm install
```

5. Start JSON-server:

- To run the server once:

```
npx json-server db.json
```

- To automatically reload when `db.json` changes:

```
npx json-server --watch db.json
```

6. Open http://localhost:3000
   to access the API.

## Example Data

The `db.json` file contains a sample collection like the one below. You can create
the data manually in the `db.json` file, or use tools like Postman to POST new data and watch it
appear in the file with JSON-server–generated IDs:

```
{
  "users": [
    {
      "id": "0b48",
      "name": "test",
      "email": "test.example.com"
    }
  ]
}
```

### Example POST body

When sending a POST request to create a new item, for example a new user, the request body can look like this:

```
{
  "name": "New User",
  "email": "new.user@example.com"
}
```

JSON-server automatically creates an id for the new item and adds it to the collection in db.json.

## Usage

You can use different tools to test API calls. Postman is used in the screenshot as an example, but any HTTP client will work.

- GET: /users
- POST: /users
- PUT: /users/:id
- DELETE: /users/:id

It is important that at least one collection exists in your `db.json` file,
so that requests (GET, POST, PUT, DELETE, etc.) to `http://localhost:3000/<collection>` work correctly.

![Postman request and response](/assets/postman.png)

You can test the API in several ways besides Postman, such as:

- Using `curl` in the terminal:

```
 curl http://localhost:3000/users
```

Or for better JSON formatting:

```
curl http://localhost:3000/users | jq

```

- Opening GET endpoints directly in the browser:

```
http://localhost:3000/users

```

- Using any HTTP client or frontend code that sends requests (fetch, Axios, etc.)

## Pros

- Fast setup, Quick installation

- Minimal coding required and easy to understand

- Several ways to test the API, including using a web browser, curl, or tools like Postman.

- Perfect for frontend testing and learning REST APIs

- Good for quickly creating an early version of an app to try out ideas.

## Cons

- Limited functionality (cannot handle complex logic, such as generating data or testing authentication)

- Static data

- Must be updated manually or via POST/PUT.

## Conclusion

JSON-server is a simple and effective tool for quickly setting up a mock API.
While it has limited functionality and is not suitable for production, it is excellent for learning REST APIs, testing frontend applications, and experimenting with API requests in a safe environment.

## Notes

- json-server is installed as a devDependency.

- node_modules/ is ignored in Git.

- This project is intended as a learning and testing resource only.

## References

[1] "json-server," npm. [Online]. Available: https://www.npmjs.com/package/json-server [Accessed: Nov. 17, 2025].
