# Database Design

In this project we will be using Amazon RDS and a PostgreSQL database.

## Tables
- Profile
- Posts
- Comments
- Likes
- Follows

![Database tables](/assets/documentation/database-tables.png "Database Tables")

## Relationships

Profiles have a one-to-many relationship with posts, comments, likes and follows, they also have a one-to-one relationship with AWS Cognito users.

Posts have a one-to-many relationship with comments and likes.

Comments have a many-to-one relationship with posts.

Likes have a many-to-one relationship with both posts and comments.