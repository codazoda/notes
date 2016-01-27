# MySQL Table Structure

## articles

| Field      | Type             | Null | Key | Extra          |
|------------|------------------|------|-----|----------------|
| articleId  | int(10) unsigned | NO   | PRI | auto_increment |
| headline   | varchar(256)     | NO   |     |                |
| summary    | tinytext         | NO   |     |                |
| text       | longtext         | NO   |     |                |
| postDate   | timestamp        | NO   |     |                |

## comments

| Field      | Type             | Null | Key | Extra          |
|------------|------------------|------|-----|----------------|
| commentId  | int(10) unsigned | NO   | PRI | auto_increment |
| articleId  | varchar(256)     | NO   |     |                |
| name       | varchar(32)      | NO   |     |                |
| text       | longtext         | NO   |     |                |
| submitDate | timestamp        | NO   |     |                |