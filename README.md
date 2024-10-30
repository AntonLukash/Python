markdown
# USOF

![Node.js](https://img.shields.io/badge/Node.js-%3E%3D14.0.0-green) ![MySQL](https://img.shields.io/badge/MySQL-Database-blue) ![License](https://img.shields.io/badge/License-ISC-blue)

> **USOF** is a forum platform inspired by Stack Overflow, designed for programmers and enthusiasts. It allows users to create accounts, post questions, comment, and like content. Administrators can manage content and users via an integrated AdminJS panel.

## Table of Contents
- [Features](#features)
- [Installation and Setup](#installation-and-setup)
- [API Documentation](#api-documentation)
- [Admin Panel](#admin-panel)
- [Usage Examples](#usage-examples)
- [License](#license)

---

## Features

### User Features
- **Authentication**: Register and log in with unique usernames and emails.
- **Post Publishing**: Create, view, and manage personal posts.
- **Post Saving**: Save posts for later viewing and access all saved posts.
- **Comments**: Comment on posts.
- **Likes & Ratings**: Like or dislike posts and comments.
- **Filtering & Sorting**: Filter posts by category and sort by date or rating.

### Admin Features (via AdminJS Panel)
- **User Management**: View, edit, delete, and assign roles.
- **Post Management**: Edit and delete posts, set status (active/inactive).
- **Category Management**: Create, edit, and delete categories.

---

## Installation and Setup

### Prerequisites
- [Node.js](https://nodejs.org) version 14.0.0 or higher
- [MySQL](https://www.mysql.com/) database
- [npm](https://www.npmjs.com/)

### Installation

1. **Clone the repository:**
   git clone https://github.com/
   
2. **Install all dependencies:**
   npm install
   
3. **Set up the MySQL database:**
   - Run the SQL script from file `db.sql` to create tables and insert test data.

4. **Start the server:**

   npm start
   
Access the API at [http://localhost:3000](http://localhost:3000).

---

## API Documentation

### 1. Authentication
- `POST /api/auth/register` — Register a new user
- `POST /api/auth/login` — Log in and receive an access token

### 2. Users
- `GET /api/users` — Get all users (admin only)
- `GET /api/users/:userId` — Get specific user information
- `PATCH /api/users/avatar` — Update user avatar
- `DELETE /api/users/:userId` — Delete a user (admin only)

### 3. Posts
- `GET /api/posts` — Get all posts with filtering and sorting
- `GET /api/posts/:postId` — Get specific post by ID
- `POST /api/posts` — Create a new post
- `PATCH /api/posts/:postId` — Update a post (author or admin)
- `DELETE /api/posts/:postId` — Delete a post (author or admin)

### 4. Saved Posts
- `POST /api/posts/:postId/save` — Save a post
- `GET /api/posts/saved` — Get all saved posts of the user
- `DELETE /api/posts/:postId/save` — Remove a post from saved posts

### 5. Comments
- `GET /api/posts/:postId/comments` — Get comments on a post
- `POST /api/posts/:postId/comments` — Add a comment to a post
- `DELETE /api/comments/:commentId` — Delete a comment (author or admin)

### 6. Likes
- `POST /api/posts/:postId/like` — Add a like/dislike to a post
- `DELETE /api/posts/:postId/like` — Remove a like/dislike from a post

---

## Admin Panel

AdminJS provides a graphical interface for managing data. Access it at `/admin` with an admin role.

---

## Usage Examples

### Create a New User
http
POST /api/auth/register
Content-Type: application/json

{
  "login": "user1",
  "password": "password123",
  "fullName": "User One",
  "email": "user1@example.com"
}
### Create a New Post
http
POST /api/posts
Authorization: Bearer <token>
Content-Type: application/json

{
  "title": "New Post",
  "content": "This is the content of the post",
  "categories": [1, 2]
}
### Get Saved Posts of User
http
GET /api/posts/saved
Authorization: Bearer <token>

---

## License

This project is licensed under the ISC License. MIT © Anton
