---
layout: post
title:      "Ruby on Rails Project"
date:       2019-06-07 02:53:32 +0000
permalink:  ruby_on_rails_project
---

I have learned so many things about ruby on rails so far such as MVC model, RESTful routes, CRUD, validation, layout. I did my best to complete each learning section. But at the same time, I felt it was overloading to my brain because I experienced a lot of inputs within a limited time frame. I need outputs to sort out a way to handle this. Building a project is one of the great things to output what I have learned.

As always, it was very helpful for me to create a note about the project before building the web app. I’m brainstorming solo - what kind of Model, View, Routes, table columns are necessary for the project. I spent times to work on it however,  a lot of ideas actually came up while I was coding. I ended up modifying many things - adding and removing table columns, and deleting a join table and creating a new one, etc. I was programming, thinking about the logic, at the same time, doing user experience -  what kind of structure or interaction is good for users.

### About my project:
It is called "Job search organizer" !
Users must sign up/log in. Users can create their own checklists, which include information about companies and positions users added,  and also users can track the process of the job application. A resume was sent? Or Interview was done? Tracking your application sounds convenient.

### Model:
I have four models. Checklist is a join table.

User
![User Model](/img/myimg/rails-user-model.png)

Company
![Company Model](/img/myimg/rails-company-model.png)

Position
![Position Model](/img/myimg/rails-position-model.png)

Checklist
![Checklist Model](/img/myimg/rails-cheklist-model.png)


I added admin attribute to User. Only admin can edit the company and position after they were created.


One of the most challenging parts was associations between tables, and what kind of attributes (table columns) are necessary.

In the real world, there are a lot of options and information. We could add as much as information we like but we do not need to provide all the options, just need to abstract and think about what kind of information users want and we want to keep in the database.

I definitely feel this project was essential for expanding my experiences and increasing my knowledge. I enjoyed Rails magic and understanding and utilizing the magic is fun way to build a web application. 
