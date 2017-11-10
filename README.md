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
- country_id: foreign_key

Countries
- id: integer
- name: string
- abbreviation: string

Genders
- id: integer
- name: string


## Intermediate

- TBD


## Advanced

- TBD