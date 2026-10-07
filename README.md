# Payment Form

Mini-app with a payment form: React frontend and Express REST API backend with MongoDB.

> This is a demo project. It does not process real payments. Do not enter real card data.

## Features

- Payment form with four fields: card number, expiry date (MM/YYYY), CVV, amount
- Client-side validation for each field
- The form data is sent to the Express API and saved to MongoDB
- The API returns the ID of the created order

## Tech stack

- Frontend: React 17, Material UI, axios (`react-app/`)
- Backend: Node.js, Express, MongoDB (`backend-server-for-react-app/`)

## Getting started

### 1. Start MongoDB

Install MongoDB Community Server [7.0](https://www.mongodb.com/try/download/community) locally (default port 27017).

Or with Docker:

```bash
docker run -d --name payment-mongo -p 27017:27017 mongo:7
```



### 2. Run the backend

```bash
cd backend-server-for-react-app
npm install
npm run dev
```

The server runs on http://localhost:8000 and connects to `mongodb://localhost:27017` by default. To use another database, set the `MONGO_URL` environment variable.

### 3. Run the frontend

In a separate terminal:

```bash
cd react-app
npm install
npm start
```

The app opens on http://localhost:3000. API requests are proxied to port 8000.

## API

`POST /createOrder`

Request body:

```json
{
  "CardNumber": "1234567812345678",
  "CVV": "123",
  "ExpiryDate": "12/2027",
  "Sum": "100"
}
```

Response:

```json
{
  "RequestId": "<order id>"
}
```

## Status and roadmap

This is an early version from 2022. Planned next steps:

- Refactoring with a clear separation of UI, logic and API layers
- Updating to the current stack (Vite, TypeScript, latest React and MongoDB driver)
- Server-side validation and security hardening (OWASP Top 10)
- Unit and integration tests for frontend and backend
- Evolving the app into a payment gateway demo