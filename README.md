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
###2. Update a task’s status
UPDATE tasks SET status = 'completed' WHERE id = 1;
###3. Delete a task
DELETE FROM tasks WHERE id = 7;
###4. Show tasks with Sorting and Limit (Pagination)
SELECT * FROM tasks ORDER BY created_at DESC LIMIT 3;
###5. Aggregator Functions
-- Count total tasks per user
SELECT user_id, COUNT(*) AS total_tasks
FROM tasks
GROUP BY user_id;

-- Find latest task creation date per user
SELECT user_id, MAX(created_at) AS latest_task
FROM tasks
GROUP BY user_id;
###6. Joins
-- Inner Join
SELECT users.name, tasks.title, tasks.status
FROM users
INNER JOIN tasks ON users.id = tasks.user_id;

-- Left Join
SELECT users.name, tasks.title, tasks.status
FROM users
LEFT JOIN tasks ON users.id = tasks.user_id;

-- Right Join
SELECT users.name, tasks.title, tasks.status
FROM users
RIGHT JOIN tasks ON users.id = tasks.user_id;


