## usersテーブル

| Column            | Type    | Options                        |
|-------------------|---------|--------------------------------|
| nickname          | string  | null: false                    |
| email             | string  | null: false, unique: true      |
| encrypted_password| string  | null: false                    |
| last_name         | string  | null: false                    |
| first_name        | string  | null: false                    |
| last_name_kana    | string  | null: false                    |
| first_name_kana   | string  | null: false                    |
| birthday          | date    | null: false                    |


### Association
 has_many :items
 has_many :buyers

## itemsテーブル

| Column                  | Type   | Options                         |
|:------------------------|:-------|:--------------------------------|
| user              | references    | foreign_key: true, null: false      |
| name                    | string | null: false                        |
| description             | text   | null: false                        |
| category_id             | integer   | null: false                       |
| condition_id            | integer   | null: false                        |
| price                   | integer   | null: false                        |
| shipping_fee_burden_id | integer   | null: false                        |
| prefecture_id           | integer   | null: false                        |
| days_until_shipping_id | integer   | null: false                        |

### Association
 belongs_to :user
 has_one :buyer

## buyersテーブル
| Column           | Type   | Options                       |
|:-----------------|:-------|:------------------------------|
| user          | references    | foreign_key: true null: false    |
| item          | references    | foreign_key: true null: false    |

### Association
 belongs_to :user
 belongs_to :item
 has_one :address

## addresses テーブル

| Column    | Type | Options                                         |
|----------------|----------|------------------------------------------------------|
| post_number    | string   | null: false                                          |
| prefecture_id  | integer  | null: false                                           |
| city           | string   | null: false                                          |
| address        | string   | null: false                                          |
| building       | string   |                                                      |
| phone_number   | string   | null: false                                          |
| buyer | references | foreign_key: true null: false                           |

### Association
  belongs_to :buyer