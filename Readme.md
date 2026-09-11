# SuperTube

SuperTube is a backend API for a modern video-sharing platform. It provides secure user authentication, video management, social interactions, comments, subscriptions, and media handling through a modular Node.js and Express architecture.

## Features

- User registration and login authentication
- JWT-based authentication with access and refresh tokens
- Secure password hashing with bcrypt
- User profiles, avatar/cover image management, and watch history tracking
- Video upload, management, thumbnail handling, and publication status toggling
- Cloudinary media integration for file uploads and automated asset cleanup
- Like functionality for videos, comments, and tweets
- Video comments management with pagination
- Channel subscribe/unsubscribe functionality and subscriber tracking
- Playlist creation and video organization
- User tweets / community posts management
- Channel dashboard analytics (total views, subscribers, video stats, total likes)
- Centralized error handling and standard API responses

## Tech Stack

- Node.js
- Express.js
- MongoDB & Mongoose
- JSON Web Token (JWT)
- bcrypt
- Cloudinary
- Multer
- dotenv

## Project Structure

```
src/
├── controllers/    # API request handlers and business logic
├── db/             # Database connection setup
├── middlewares/    # Auth verification and file upload middlewares
├── models/         # Mongoose schemas and data models
├── routes/         # Express route definitions
├── utils/          # Helper utilities (ApiError, ApiResponse, Cloudinary, etc.)
├── app.js          # Express app configuration & global middleware
├── constants.js    # Application constants (e.g. DB_NAME)
└── index.js        # Server entry point
```

## Installation

```bash
git clone https://github.com/000aksh000/SuperTube.git
cd SuperTube
npm install
```

Copy `.env.sample` to `.env` and fill in your configuration:

```bash
cp .env.sample .env
```

## Environment Variables

Configure the following environment variables in `.env`:

- `PORT` - Port number for server (default: `8000`)
- `MONGODB_URI` - MongoDB connection string
- `CORS_ORIGIN` - Allowed CORS origin (`*` or specific client domain)
- `ACCESS_TOKEN_SECRET` - Secret key for signing access tokens
- `ACCESS_TOKEN_EXPIRY` - Access token expiration duration (e.g. `1d`)
- `REFRESH_TOKEN_SECRET` - Secret key for signing refresh tokens
- `REFRESH_TOKEN_EXPIRY` - Refresh token expiration duration (e.g. `10d`)
- `CLOUDINARY_CLOUD_NAME` - Cloudinary cloud name
- `CLOUDINARY_API_KEY` - Cloudinary API key
- `CLOUDINARY_API_SECRET` - Cloudinary API secret

## Running Locally

To start the development server with auto-reloading:

```bash
npm run dev
```

## API Routes

- `/api/v1/healthcheck` - Server status & health check
- `/api/v1/users` - User registration, authentication, avatar/cover management, profile & watch history
- `/api/v1/videos` - Video uploads, paginated search, video fetching, thumbnail updates & publish toggles
- `/api/v1/comments` - Video comment creation, updates, deletion, & paginated fetching
- `/api/v1/likes` - Video, comment, and tweet likes toggling & fetching liked videos
- `/api/v1/subscriptions` - Channel subscription toggles, subscriber lists & subscribed channel listings
- `/api/v1/playlist` - Playlist creation, updates, deletion & video management
- `/api/v1/tweets` - User community tweets CRUD
- `/api/v1/dashboard` - Creator channel analytics, view counts, subscriber stats & channel video list

## Security

- Password hashing using bcrypt prior to database storage
- JWT authentication with secure HTTP-only cookies and bearer tokens
- Protected routes guarded by `verifyJWT` middleware
- Environment-isolated secrets and API keys
- Structured input validation and global error handling

## License

ISC License
