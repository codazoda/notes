# MySQL Tables

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
| articleId  | int(10) unsigned | NO   |     |                |
| userId     | int(10) unsigned | NO   |     |                |
| text       | longtext         | NO   |     |                |
| submitDate | timestamp        | NO   |     |                |

## users

| Field      | Type             | Null | Key | Extra          |
|------------|------------------|------|-----|----------------|
| userId     | int(10) unsigned | NO   | PRI | auto_increment |
| firstName  | varchar(64)      | NO   |     |                |
| lastName   | varchar(64)      | NO   |     |                |
| createDate | timestamp        | NO   |     |                |