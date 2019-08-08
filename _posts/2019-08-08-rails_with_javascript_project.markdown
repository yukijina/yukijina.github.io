---
layout: post
title:      "Rails with JavaScript Project"
date:       2019-08-08 04:14:45 +0000
permalink:  rails_with_javascript_project
---


<p>My last project was creating a web application with Ruby on Rails. Now we have to add some functions with JavaScript  - Rails with JavaScript project. Rails application builds an API that utilizes JSON.</p>

<p>The most fun things about this project was how front-end (JavaScript) and back-end (Rails) work together. It is a collaboration between Rails and JavaScript. I can finally create a web application as a "full-stack" developer. It excites me a lot!</p>

<p>In this project, we had to create a Rails back-end API, that is interact with JavaScript front-end. We use rails gem ActiveModel::Serializer (AMS). By using AMS, We can easily create JSON responses. In this serialization, we make a Ruby object as a sting and can consume anywhere.</p>

<p>Why JSON? JSON stands for JavaScript Object Notation, which is a light weight human readable key-value pairs (hash). This is super easy to get access to and more efficient compared to XML documents.</p>

<p>My web application is for organizing a job search. Once a user logs in, he/she can create a position or choose from an existing position. Users can list it to their own checklists. In the checklist, you can add progress such as resume sent, interview done, completed and some notes.</p>

<p>Serialization and getting data available in JavaScript was interesting part for me. I want to make notes here for how to do it.</p>

## 1. Add rails gem ActiveModel::Serializer to Gemfile
<p>We have to add the serializer gem in Gemfile.</p>
`gem "active_model_serializers"`

<p>In terminal:</p>
`bundle install`


## 2. Generate serializer directly and files
<p>Then we create a serializer file. We can generate in the terminal like:</p>
`rails g serializer company`

<p>We add table name after `rails g serializer - your table name`.
Then Rails creates a directly `app/serializers`(if you does not have one) and a file `app/serializers/company_serializer.rb`.</p>

## 3. Add attributes and association
<p>As you open the serializer file, `attributes :id` is already assigned as a default. We can add attributes we want to serialize.</p>

<p>In my project, I want to use positions and users data that are associated with companies through JSON. To make this data available, I have to add an association `has_many :positions` in `app/serializer/company_serializer.rb` :</p>


```
class CompanySerializer < ActiveModel::Serializer
  attributes :id, :name, :url, :description
  has_many :positions
  has_many :users
end
```

<p>We can generate another serializer file as same as company, such as: <br>
`app/serializers/position_serializer.rb.`  <br>
and add attribute (`:title`, `:description` `:salary`, `:full_time...`) an association `belons_to :company`  to the file.</p>

```
class PositionSerializer < ActiveModel::Serializer
  attributes :id, :title, :description, :salary, :full_time, :created_at, :updated_at, :company_id
  belongs_to :company
end
```

<p>This looks pretty much the same code as model. But when we have joint table, we don't need to use  `has_many XXX through XXX`. Instead, we can simply write `has_many XXX` (without through) and AMS takes care of the rest of things with model. </p>

<p>We generate the serizlier for other tables as same as the above.</p>

## 4. In controller,  make json response available
<p>In `index` method of `app/controllers/companies_controller.rb`, I need to add:</p>

```
respond_to do |format|
  format.html  { render :index }
  format.json  {render json: @companies }
end
```

<p>The first line - `format.html  { render :index }` - tells if HTML is requested (default), render `index`. If the clients wants JSON response ,respond as JSON. `@companies`. It makes all company's attributes available as JSON.</p>

<p>We can add this not only in index but also in other methods.</p>

<p>Check JSON data trough API endpoint like `http: localhost:3000/companies.json`<br>
Now we can see key/value pairs JSON on browser. It is your own internal API. That is pretty cool.</p>

## 5. Access JSON through JavaScript
<p>Ruby part is done now. Now it's time to fetch JSON with JavaScript.<br>
In JavaScript file, we need to get the data:</p>

```
function listeningCompaniesLoad() {
   fetch("/companies.json")
   .then(resp => resp.json())
   .then(jsonData =>
    jsonData.forEach((companyData) => {
      do something with data.... I will create a instance of the class and prototype, and append it to the div in the body.
    })
  )
}
```

<p>Fetch accesses HTTP pipeline such as requests and responses.</p>


## 6. Create a class and render HTML through JavaScript.
<p>Create a class and constructor, and assign JSON to property of the instance of the class.<br>
By creating Object-Oriented-Programming in JavaScript, we can easily add function and render the desired HTML through JavaScript. </p>

```
class Company {
  constructor(data) {
    this.id = data.id;
    this.name = data.name;
    this.description = data.description;
		...
  };
  indexHTML() {
    return `
      <div class="card-body">
		    <h2 class="card-title">${this.name}</h2>
        <p class="card-text js-description-${this.id}">${this.description.substring(0, 20)}...</p>
        <button class="js-read-more btn btn-info btn-sm" data-id="${this.id}"> Read More </button>
        <button class="js-positions btn btn-info btn-sm" data-id="${this.id}">Check Positions</button>
         ...
      </div>
		`
  }
	```

<p>Once we create a class, we can add functions for an instance of a class and use or call the functions several times in another functions in JavaScript. That is super efficient and convenient. We can even add another trigger such as click button id in the HTML you just created and use this click event later.</p>

## Conclusion
<p>At the beginning, I thought it was much easier to render HTML through Ruby using the embedded ruby (file.html.erb). However by creating OOP in JavaScript, I learned there was another way to render HTML. We can create reusable functions, which we can call, use or add to another functions. It provides a dynamic movement in a browser. A web page is updated without refreshing the page  - Ajax call. Through this project, I feel great to know about how nicely both front and back-end work together. </p>
