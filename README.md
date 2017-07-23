# DB設計 #


## messages table ##

| Column     | Type        | Options                      |
|:-----------|:------------|:-----------------------------|
| body       | text        |null: false                   |
| image      | string      |                              |
| group_id   | references  |foreign_key: true, index: true|
| user_id    | references  |foreign_key: true, index: true|

### Association ###

- belongs_to :user

- belongs_to :group


## users table ##

deviseを使用

| Column     | Type        | Options                              |
|:-----------|:------------|:-------------------------------------|
| name       | string      |index: true, null: false, unique: true|

### Association ###

- has_many :massages

- has_many :group_users

- has_many :groups, through: :group_users


## groups table ##

| Column     | Type        | Options                 |
|:-----------|:------------|:------------------------|
| name       | string      |null: false, unique: true|

### Association ###

- has_many :users, through: :group_users

- has_many :group_users

- has_many :messages


## group_users table ##

| Column     | Type        | Options                      |
|:-----------|:------------|:-----------------------------|
| group_id   | references  |foreign_key: true, index: true|
| user_id    | references  |foreign_key: true, index: true|

### Association ###

- belongs_to :user

- belongs_to :group
