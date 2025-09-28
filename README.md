# Task Manager Database

## Database Name
`task_manager`

## Tables Created

### 1. users
- `id` (Primary Key, Auto Increment)
- `name` (User full name)
- `email` (Unique email address)
- `created_at` (Timestamp of record creation)

### 2. tasks
- `id` (Primary Key, Auto Increment)
- `user_id` (Foreign Key referencing users.id)
- `title` (Task title)
- `description` (Task details)
- `status` (pending, completed, in progress, etc.)
- `created_at` (Timestamp of record creation)

## Relationship
- One-to-Many (1:N) relationship between **users** and **tasks**.  
  - One user can have many tasks.  
  - Implemented using `FOREIGN KEY (user_id) REFERENCES users(id)`.

## Data Inserted
- 3 users: Shafin, Rahim, Karim  
- Multiple tasks for each user (at least 2+ per user)

## SQL Queries Used

### 1. Select all tasks
```sql
SELECT * FROM tasks;


