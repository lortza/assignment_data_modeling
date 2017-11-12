# assignment_data_modeling
Mmmmm.... dataaaaa....

Anne Richardson

## Basic

### 1) Online Learning Platform

#### Goals

- display a page of all course titles
- each course page should have links to each course lesson
- lessons have tags which link to that tag category so that users can see other related lessons
- tags can have many lessons and lessons can have many tags

#### Tables

Courses
- id: integer
- title: string
- description: text

Lessons
- id: integer
- course_id: references (foreign_key)
- title: string
- body: text

Tags
- id: integer
- name: string

Tags_Lessons
- id: integer
- lesson_id: references (foreign_key)
- tag_id: references (foreign_key)

### 2) User Profile Page

#### Goals

- collect repeatable demographic information in supporting tables
- be flexible in the names of available genders
- display a user's state and country via joins to city
- display a fixed list of cities (though this is not accurate enough for mailings, it will suffice for a "choose the city nearest to you" situation)

#### Tables

Users
- id: integer
- username: string
- email: string
- age: integer
- gender_id: references (foreign_key)
- city_id: references (foreign_key)

Cities
- id: integer
- state_id: references (foreign_key)

States
- id: integer
- name: string
- abbreviation: string
- country_id: references (foreign_key)

Countries
- id: integer
- name: string
- abbreviation: string

Genders
- id: integer
- name: string


## Intermediate

### Hacker News-like Site

#### Goals

- users must sign in
- users can post submissions
- users can comment on submissions

#### Tables

Users
- id: integer
- username: string
- email: string

ContentTypes (ex: post, comment)
- id: integer
- name: string ?

Posts
- id: integer
- user_id: references (foreign_key)
- content_type_id: references (foreign_key)

Comments
- id: integer
- user_id: references (foreign_key)
- parent_id: references (foreign_key)
- content_type_id: references (foreign_key)

Comment_Hierarchies -- WIP, idk...
- id: integer
- ancestor_id: references (foreign_key)
- descendant_id: references (foreign_key)

## Advanced

### E-commerce

#### Goals
- allow users to place orders
- allow users to delete account while we maintain record of purchases

#### Tables
Customers
- has_many addresses
- has_many orders
- id: integer
- name: string
- email: string
- password: etc...
- deactivated: boolean

Vendors
- has_many addresses
- has_many orders
- has_many products
- id: integer
- name: string
- description: text
- deactivated: boolean

Products (going to ignore size and color variants for now)
- belongs_to_many order_items
- id: integer
- name: string
- sku: string
- price: float?
- promo_price: float?
- qty_in_stock: integer

Orders
- has_many order_items
- id: integer
- customer_id: references (foreign_key)
- vendor_id: references (foreign_key)
- subtotal: float?
- total: float?
- purchased_on: date
- canceled: boolean

OrderItems
- belongs_to order
- id: integer
- product_id: references (foreign_key)
- qty: integer
- order_id: references (foreign_key)

CustomerAddresses
- belongs_to user
- belongs_to type
- id: integer
- type_id: references (foreign_key)
- user_id: references (foreign_key)
- street_1: string
- street_2: string
- city_id: references (foreign_key)
- zip: string

VendorAddresses
- belongs_to vendor
- belongs_to type
- id: integer
- type_id: references (foreign_key)
- vendor_id: references (foreign_key)
- street_1: string
- street_2: string
- city_id: references (foreign_key)
- zip: string

AddressType (Billing, Shipping, etc)
- id: integer
- name: string

Cities
- belongs_to state
- id: integer
- name: string
- state_id: references (foreign_key)

States
- belongs_to country
- id: integer
- name: string
- abbreviation: string
- country_id: references (foreign_key)

Countries
- id: integer
- name: string


### Analytics

#### Goals
- track user click information

#### Tables
Users
- id: integer
- name: string
- email: string
- (etc)

Products
- id: integer
- name: string
- (etc)

UserProductClicks
- id: integer
- user_id: references (foreign key)
- product_id: references (foreign key)
- url_clicked: string
- link_text: string
- timestamp: datetime

