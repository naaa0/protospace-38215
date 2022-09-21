# テーブル設計

## usersテーブル

| Column              | Type       | Options                   |
| ------------------- | ---------- | ------------------------- |
| email               | string     | null: false, ユニーク制約   |
| encrypted_password  | string     | null: false               |
| name                | string     | null: false,              |
| profile             | text       | null: false,              |
| occupation          | text       | null: false,              |
| position            | text       | null: false,              |

### Association
- has_many :prototypes
- has_many :comments


## prototypesテーブル

| Column      | Type       | Options                           |
| ----------- | ---------- | --------------------------------- |
| title       | string     | null: false, unique: true         |
| catch_copy  | text       | null: false                       |
| concept     | text       | null: false,                      |
| user        | references | null: false, foreign_key: true    |


### Association
- belongs_to :users
- has_many   :comments


## commentsテーブル

| Column      | Type       | Options                           |
| ----------- | ---------- | --------------------------------- |
| content     | string     | null: false, unique: true         |
| prototype   | references | null: false, foreign_key: true    |
| user        | references | null: false, foreign_key: true    |


### Association
- belongs_to :users
- belongs_to :prototypes


