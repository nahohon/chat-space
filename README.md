# DB設計

## users table

|Column|Type|Options|
|------|----|-------|
|id|integer|primary_key: true|
|name|string|null: false|
|email|string|null: false|unique: true|
|timestamps|  |null: false|

### Association

  - has_many :groups, through: group_users <br>
  - has_many :messages <br>
  - has_many :groups_users



## messages table
|Column|Type|Options|
|------|----|-------|
|id|integer|primary_key: true|
|body|text|   |
|image|string|  |
|group_id|references| foreign_key: true|
|user_id|references| foreign_key: true|
|timestamps|  |null: false|

### Association

   - belongs_to :user <br>
   - belongs_to :group



## groups table
|Column|Type|Options|
|------|----|-------|
|id|integer|primary_key: true|
|name|string|null: false|
|timestamps|   |null: false|

### Association

   - has_many :messages <br>
   - has_many :users, through: :groups_users <br>
   - has_many :groups_users
   
   
   
## groups_users
|Column|Type|Options|
|------|----|-------|
|id|integer|primary_key: true|
|user_id|references|foreign_key: true|
|group_id|references|foreign_key: true|

### Association
   - belongs_to :user <br>
   - belongs_to :group
