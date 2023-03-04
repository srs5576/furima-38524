## userテーブル

| Column            | Type    | Options                        |
|-------------------|---------|--------------------------------|
| id                | int     | auto_increment, primary_key    |
| nickname          | string  | null: false                    |
| email             | string  | null: false, unique: true      |
| password_digest   | string  | null: false                    |
| last_name         | string  | null: false                    |
| first_name        | string  | null: false                    |
| last_name_kana    | string  | null: false                    |
| first_name_kana   | string  | null: false                    |
| birthday          | date    | null: false                    |


## itemsテーブル

| column                  | type   | options                         |
|:------------------------|:-------|:--------------------------------|
| id                      | int    | auto_increment, primary key     |
| seller_id               | int    | foreign_key: true, not null      |
| name                    | string | not null                        |
| image                   | string |                                 |
| description             | text   | not null                        |
| category_id             | int    | not null                        |
| condition_id            | int    | not null                        |
| price                   | int    | not null                        |
| shipping_fee_burden_id  | int    | not null                        |
| prefecture_id           | int    | not null                        |
| days_until_shipping_id  | int    | not null                        |

### Association
- belongs_to :user
- belongs_to :category
- belongs_to :condition
- belongs_to :shipping_fee_burden
- belongs_to :prefecture
- belongs_to :days_until_shipping

## buyerテーブル
| column           | type   | options                       |
|:-----------------|:-------|:------------------------------|
| user_id          | int    | not null                      |
| item_id          | int    | not null                      |
| prefecture_id    | int    |                               |
| Image            | string |                               |

## address テーブル

| column       | type   | options  |
|:-------------|:-------|:---------|
| user_id      | int    | not null |
| post_number  | string |          |
| city         | string |          |
| address      | string |          |
| phone_number | string |          |

