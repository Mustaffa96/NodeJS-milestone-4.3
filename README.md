# Secure API with JWT Authentication and Rate Limiting

A secure Node.js REST API featuring JWT authentication with refresh tokens, rate limiting, and Swagger documentation.

## Features

- 🔐 JWT Authentication with refresh tokens
- 🚦 Rate limiting for API protection
- 📚 Swagger API documentation
- 🔒 Secure password hashing with bcrypt
- 🍪 HTTP-only cookies for refresh tokens
- 🛡️ Security headers with Helmet
- 📝 MongoDB for user management
- ⚡ Express.js for fast routing

## Prerequisites

- Node.js (v14+ recommended)
- MongoDB (v4+ recommended)
- npm or yarn

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd NodeJS-milestone-4.3
```

2. Install dependencies:
```bash
npm install
```

3. Create environment variables:
```bash
cp .env.example .env
```

4. Update the `.env` file with your configuration:
```env
PORT=3000
NODE_ENV=development
CORS_ORIGIN=http://localhost:3000
JWT_ACCESS_SECRET=your_access_token_secret_here
JWT_REFRESH_SECRET=your_refresh_token_secret_here
MONGODB_URI=mongodb://localhost:27017/secure-api
```

5. Generate JWT secrets:
```bash
node generate-secrets.js
```

Copy the generated secrets to your `.env` file.

## Running the Application

1. Start MongoDB:
```bash
# Make sure MongoDB is running on your system
mongod
```

2. Start the server:
```bash
# Development mode
npm run dev

# Production mode
npm start
```

The server will start on http://localhost:3000 (or the PORT specified in your .env)

## API Documentation

Access the Swagger documentation at: http://localhost:3000/api-docs

### Main Endpoints

- POST `/api/auth/register` - Register a new user
- POST `/api/auth/login` - Login and get access token
- POST `/api/auth/refresh-token` - Get new access token using refresh token
- POST `/api/auth/logout` - Logout and clear refresh token
- GET `/api/auth/protected` - Example protected route

### Example Usage

1. Register a new user:
```bash
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "your_password",
    "name": "Your Name"
  }'
```

2. Login:
```bash
curl -X POST http://localhost:3000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "your_password"
  }'
```

## Security Features

- JWT tokens with short expiry for access tokens
- Secure HTTP-only cookies for refresh tokens
- Rate limiting to prevent brute force attacks
- Password hashing using bcrypt
- Security headers with Helmet
- CORS protection
- Error handling middleware

## Rate Limiting

The API implements rate limiting with the following defaults:
- 100 requests per 15 minutes per IP
- Applies to all `/api` routes

## Error Handling

The API implements centralized error handling with appropriate HTTP status codes and error messages.

## Development

For development, the application uses nodemon for auto-reloading:
```bash
npm run dev
```

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request

## License

This project is licensed under the MIT License.
