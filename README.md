# DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|username|string|null: false|
|image|string||
|text|text||
### Association
- has_many :tweets
- has_many :comments


## tweetsテーブル
|Column|Type|Options|
|------|----|-------|
|title|text|null: false|
|text|text|null: false|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- has_many :comments
- has_many :tweets_tags
- has_many  :tags,  through:  :tweets_tags


## likesテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false|
|tweet_id|integer|null: false|

### Association
- belongs_to :user
- has_many :comments
- has_many :tweets_tags
- has_many  :tags,  through:  :tweets_tags


## tagsデーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
### Association
- has_many :tweets_tags
- has_many  :tweet,  through:  :tweets_tags

## tweets_tagsテーブル
|Column|Type|Options|
|------|----|-------|
|tweet_id|integer|null: false, foreign_key: true|
|tag_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :tweet
- belongs_to :tag

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :tweet
- belongs_to :user
