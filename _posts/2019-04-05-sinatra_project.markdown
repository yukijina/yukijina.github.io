---
layout: post
title:      "Sinatra Project"
date:       2019-04-05 04:11:06 +0000
permalink:  sinatra_project
---


It's time to make a web application!

Sign up, log in, log out - most of the websites have a natural flow to view one page after another.
For example - Facebook , nobody wants other users to edit, delete and create his/her own posts. That is obvious when we visit any web application every day but I was surprised that creating this logic and RESTful route was more complicated than I imagined.

However, as always, when you understand the logic, fun time begins.

## What I learned through the project:
The key is to *make a blueprint *first. I found it was definitely helpful to write down what kind of application I want to create. As Avi always explains in his video lecture, I decided to note the structure and ideas before programming.

1. What kind of tables/database I want to create.
2. A relationship between tables - and how many Models
3. What kind of routes are needed
4. What kind of page the route renders. Or redirects to the other route?

My project is creating a fictional Brewery club application with Sinatra. A brewery is a user. Once a user signs up the club, the user can register their own brands and information.

## My Note:
### Model (class)
- class Brewery     
   - has_many :brands
   - has_secure_password
   - validates

- class Brand          
    - belongs_to :breweries

#### Brewery has many (beer) brands
##### Breweries table
- :name "ABC Brewery"                #string
- :email  "abc@example.com"   #string - unique log-in attribute
- :password "xxxx"                        #password_digest
- :city "Portland, OR"                    #string

#### Brand belongs to brewery
##### Brands table
- :name   "summer magic"        #string
- :style    "IPA"                      #string
- :abv       "5.6%"                   #string
- :brewery_id                    #integer (foreign key)

#### Brewery's responsibility
- Brewer signs up with name, email, password, and city.  #CREATE
- Brewery logs in with email and password
- Brewery can see its own (individual) page   #SHOW
- Brewery can see all Breweries    #INDEX
- Brewery can log out

#### Brands responsibility   
- Brand can show its beer brand          #SHOW
- Brand can create a new brand        #NEW
- Brand can edit its own brand          #EDIT
- Brand can delete its own brand        #DELETE
- Brand can see all the brands    #INDEX
- Brand can't create, edit and delete other brewery's brands

### Controllers
- ApplicationController
- BreweriesController  
- BrandsController     

#### ApplicationController
- main controller
- inherit from Sinatra
- enable session
- include the helper method
- has home route '/'

#### BreweriesController
- inherit from ApplicationController
- has signup, login, logout, show routes

#### BrandsController
- inherit from ApplicationController
- has show, create, edit, delete routes

##### 7 RESTful routes :
There is 7 restful routes pattern to follow when creating an application.

REST(representational Stat Transfer) provides mapping HTTP verbs and CRUD (create, read, update, delete) actions.

![grid sytem](http://yukijina.github.io/img/myimg/route.png)
<!-- <img src="../img/myimg/route.png" alt="RESTful route"> -->


If I follow these routes, everything should be in a good flow.
That is all the notes I wrote before building the application.

I was able to focus on programming based on the blueprint.
I can see the goal clearly and know what I want to do next. It gives me focus and direction. I already know what routes I want to create and what kind of templates I want to render. What I need to think is writing ruby and html/css. I don't need to think again and again for what kind of method or route I am supposed to use next.

The blueprint should not be perfect. We can always add additional functions and change for the better ideas. Creating a note at the beginning is not only to make your mind clear but also it is exciting because you can picture what kind of application you want.

It is like a vision board and it can set a goal.  
