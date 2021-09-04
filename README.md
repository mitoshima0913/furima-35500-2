# DB 設計

## users table

| Column             | Type                | Options                 |
|--------------------|---------------------|-------------------------|
| nickname           | string              | null: false             |
| email              | string              | null: false             |
| password           | string              | null: false             |
| nickname           | string              | null: false             |
| last_name          | string              | null: false             |
| first_name         | string              | null: false             |
| last_furigana      | string              | null: false             |
| first_furigana     | string              | null: false             |
| birthday           | datetime            | null: false             |

### Association

* has_many :items

## items table

| Column                              | Type       | Options           |
|-------------------------------------|------------|-------------------|
| image                               | reference  | foreign_key: true |
| name                                | string     | null: false       |
| description                         | text       | null: false       |
| category                            | string     | null: false       |
| condition                           | string     | null: false       |
| pay                                 | string     | null: false       |
| district                            | string     | null: false       |
| days                                | integer    | null: false       |
| price                               | integer    | null: false       |
| user                                | references | foreign_key: true |

### Association

- belongs_to :user
- has_one :purchase

## purchasers table

| Column      | Type       | Options           |
|-------------|------------|-------------------|
| item        | references | foreign_key: true |
| user        | references | foreign_key: true |

### Association

- belongs_to :item
- has_one :address

## address table

| Column            | Type       | Options           |
|-------------------|------------|-------------------|
| zip_code          | integer    | null: false       |
| prefecture        | string     | null: false       |
| municipalities    | string     | null: false       |
| street_number     | integer    | null: false       |
| phone_number      | integer    | null: false       |
| purchase          | references | foreign_key: true |

### Association

- belongs_to :purchase