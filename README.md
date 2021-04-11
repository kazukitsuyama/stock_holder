# テーブル設計

## users テーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| name               | string | null: false               |
| email              | string | null: false  unique: true |
| encrypted_password | string | null: false               |

### Association
- has_many :stocks
- has_many :areas

## stocks テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| stock_name         | string     | null: false                    |
| text               | text       | null: false                    |
| category           | integer    | null: false                    |
| use_place          | integer    | null: false                    |
| order_place        | integer    | null: false                    |
| cost               | integer    | null: false                    |
| user               | references | null: false, foreign_key: true |
| area               | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- belongs_to :area

## areas テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| area_name          | string     | null: false                    | 
| user               | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- has_many   :stocks