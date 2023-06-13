# Public Endpoints :
- POST /api/v1/register
- GET /api/v1/posts (to see all posts).
- GET /api/v1/posts/{id} (to see the specific post)
- GET /api/v1/posts/{id}/comments (to see the specific post's comments)
- POST /api/v1/logout (to logout)
  
# Private Endpoints
- POST /api/v1/posts (create a new post)
- PATCH /api/v1/posts (edit a post)
- DELETE /api/v1/posts/{id} (delete a post)
- POST /api/v1/posts/{id}/comments (create a comment)
- PATCH /api/v1/comments/{id} (update a comment)
- DELETE /api/v1/comments/{id} (delete a comment)
- GET /api/v1/profile/ (get profile)
- PATCH /api/v1/profile (edit profile)
- PATCH /api/v1/reset-password (reset password)

  <b> ----  Specially For Admin ---- </b>
- GET /api/v1/users (get all users)
- PUT /api/v1/users (update user or create)
- PATCH /api/v1/users/{id} (update user)
- GET /api/v1/users/{id}/posts (get a single user's all posts)
- DELETE /api/v1/users/{id} (delete a user)

