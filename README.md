# DB設計

## users table

|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false, unique: true|
|email|string|null: false|unique: true|

### Association

  - has_many :groups, through: group_users
  - has_many :messages
  - has_many :groups_users



## messages table
|Column|Type|Options|
|------|----|-------|
|body|text|   |
|image|string|  |
|group_id|references| foreign_key: true|
|user_id|references| foreign_key: true|

### Association

   - belongs_to :user
   - belongs_to :group



## groups table
|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false, unique: true|

### Association

   - has_many :messages
   - has_many :users, through: :groups_users <br>
   - has_many :groups_users
   
   
   
## groups_users
|Column|Type|Options|
|------|----|-------|
|user_id|references|foreign_key: true|
|group_id|references|foreign_key: true|

### Association
   - belongs_to :user
   - belongs_to :group
