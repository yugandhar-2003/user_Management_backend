# User Management REST API (Node.js + Express + SQLite)

This is a sample User Management REST API intended for a backend developer assignment.
It uses **Express.js** and **Sequelize ORM** with **SQLite** (zero-config DB).

## Features
- CORS enabled
- RESTful endpoints for CRUD operations on users
- Basic validation and error handling
- Sequelize models and easy sync script

## Quickstart

1. Install dependencies
```bash
npm install
```

2. Copy `.env.example` to `.env` and adjust if needed
```bash
cp .env.example .env
```

3. (Optional) Sync database schema
```bash
npm run migrate
```

4. Start server
```bash
npm start
# or for development with auto-reload
npm run dev
```

By default the server runs on `http://localhost:4000`.

## API Endpoints

- `GET /api/users` — List all users
- `GET /api/users/:id` — Get single user by id
- `POST /api/users` — Create new user
- `PUT /api/users/:id` — Update a user
- `DELETE /api/users/:id` — Delete a user

### Example `curl` requests

Create user:
```bash
curl -X POST http://localhost:4000/api/users \
  -H "Content-Type: application/json" \
  -d '{
    "name":"Alice",
    "email":"alice@example.com",
    "phone":"1234567890",
    "company": { "name": "Acme Co", "catchPhrase": "We deliver" },
    "address": { "street":"MG Road", "city":"Bengaluru", "zipcode":"560001", "geo": { "lat":"12.9716", "lng":"77.5946" } }
  }'
```

Get all users:
```bash
curl http://localhost:4000/api/users
```

Update user:
```bash
curl -X PUT http://localhost:4000/api/users/1 -H "Content-Type: application/json" -d '{"phone":"999999"}'
```

Delete user:
```bash
curl -X DELETE http://localhost:4000/api/users/1
```

## .env.example
Included - copy to `.env` before running.

## Notes for evaluation
- Uses proper HTTP status codes (201 for create, 204 for delete, 404 for not found, 400 for validation, 409 for conflict).
- Database schema intentionally flattened for simple JSON mapping; can be extended to related tables.
- Error handling is centralized in Express.
