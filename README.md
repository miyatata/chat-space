# README
## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|text|null: false|

### Association
- has_many :posts
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
|text|text||
|image|string||
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user