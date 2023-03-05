## usersテーブル

| Column            | Type    | Options                        |
|-------------------|---------|--------------------------------|
| id                | int     | auto_increment, primary_key    |
| nickname          | string  | null: false                    |
| email             | string  | null: false, unique: true      |
| encrypted_password| string  | null: false                    |
| last_name         | string  | null: false                    |
| first_name        | string  | null: false                    |
| last_name_kana    | string  | null: false                    |
| first_name_kana   | string  | null: false                    |
| birthday          | date    | null: false                    |


### Association
 has_many :items, dependent: :destroy
 has_many :buyers
 has_many :purchases, through: :buyers, source: :item
 has_one :address

## itemsテーブル

| column                  | type   | options                         |
|:------------------------|:-------|:--------------------------------|
| seller               | int    | foreign_key: true, not null      |
| name                    | string | not null                        |
| description             | text   | not null                        |
| category             | int    | not null                        |
| condition            | int    | not null                        |
| price                   | int    | not null                        |
| shipping_fee_burden  | int    | not null                        |
| prefecture           | int    | not null                        |
| days_until_shipping  | int    | not null                        |

### Association
 belongs_to :user
 belongs_to :category
 belongs_to :condition
 has_one :shipping_fee_burden
 has_one :prefecture
 has_one :days_until_shipping
 has_one :buyer

## buyersテーブル
| column           | type   | options                       |
|:-----------------|:-------|:------------------------------|
| user_id          | int    | not null                      |
| item_id          | int    | not null                      |

### Association
 belongs_to :user
 belongs_to :item
 has_one :address, through: :user

## address テーブル

| Column Name    | Data Type | Constraints                                         |
|----------------|----------|------------------------------------------------------|
| post_number    | string   | NOT NULL                                             |
| prefecture     | integer  | NOT NULL                                             |
| city           | string   | NOT NULL                                             |
| address        | string   | NOT NULL                                             |
| building       | string   |                                                      |
| phone_number   | string   | NOT NULL                                             |
| purchase_history | foreign key | NOT NULL, with foreign key constraints          |

### Association
  belongs_to :user
  belongs_to :buyer