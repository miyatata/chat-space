# README
## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|groupname|text|null: false|
|nickname|text|null: false, foreign_key: true|

### Association
- has_many :groups_users
- has_many :users, through: :groups_users

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|text|null: false, funique: true|
|email|string|null: false, unique: true|
|password|string|null: false|

### Association
- has_many :posts
- has_many :groups_users
- has_many :groups, through: :groups_users

## postsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|image|string||

### Association
- belongs_to :users
- has_many :groups_users
- has_many :groups, through: :groups_users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user