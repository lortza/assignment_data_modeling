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
- course_id: integer
- title: string
- body: text

Tags
- id: integer
- name: string

Tags_Lessons
- id: integer
- lesson_id: integer
- tag_id: integer

## Intermediate

- TBD


## Advanced

- TBD