---
layout: post
title:      "My First CLI Project in Ruby"
date:       2019-02-01 03:16:02 +0000
permalink:  my_first_cli_project_in_ruby
---

I am writing about my first CLI - Command Line Interface -  project in Ruby.

To build the program, we need to create a gem, environment directory and multiple files for classes from scratch. All needs to be collaborated each other to make CLI work beautifully.

I was so excited but at the same time I felt a bit scared if I can make it work!
But it turned out it was so much fun to build the program and actually it was even addictive.

## Whole Foods Market Recipe Collection
<p>I used the website from Whole Foods Market Recipe Collection. They have a bunch of recipes on their website.</p>
Here is the site that  I used for this project.<br>
[http://www.wholefoodsmarket.com/recipe-collections](http://www.wholefoodsmarket.com/recipe-collections)


<h2>Process making CLI</h2>
<p>Let's go through how to start CLI project.</p>

<p>To get started, we need bundler installed in our computer.<br>
Bundler can install gems and tracks its version. Bundle is not only managing Rubygems dependencies but also we can create our own Bundler.</p>

<p>To check bundle, run the following code in the terminal. <p>
`bundle -v `

<p>If it is already installed,  let's create own bundle gem.</p>
`bundle gem wholefoods_recipe`

<p>I named it as `wholefoods_recipe` according to my project but you can assign any name here.</p>

<p>Now bin and lib directory, gem, gitnote, READ.md and other files were already created. This is pretty cool!! </p>

<h3>.gemspec file</h3>
We need to update `spec.summery`,`spec.description` and `spec.homepage`. I also added `gem 'pry'` and `gem 'nokogiri'` at this point. Run `bundle` in the terminal if everything works okay.

<h3>class and cli files</h3>
I also like to create some files at the beginning. I definitely needed files for:

* cli.rb - CLI controller, interact with users
* scraper.rb - scrape data from website
* category.rb - class file, assign attribute

These are minimum files I created at first but I created more class files to define methods from different pages later.

<h3>Executable file</h3>
`bin` -  This is executable directory.

<p>Inside this bin directory, I created new file which is my main executable file.</p>
 `bin/wholefoods_recipe`

<p>In this executable file, I need to write the following code on top of the page because the file does not have extension. We need computer to read collectly - this is ruby file.</p>
`#!/usr/bin/env ruby`

<p>Underneath of this code, I wrote lib directory path, that is our environment file.</p>
`require_relative "../lib/wholefoods_recipe"`

<p>Note: `lib` is not located in the same directory so we need to use two dots `../lib` . If it is in the same directory, we can use just one dot.</p>

<h3>Environment file</h3>
`lib/wholefoods_recipe`

<p>This is my environment file and I wrote all the file paths in this folder :</p>

<p>i.e<br>
`require_relative "./wholefoods_recipe/cli"`<br>
`require_relative "./wholefoods_recipe/category"`<br>
`require_relative "./wholefoods_recipe/scraper"`<br></p>

<h3>My Class files</h3>
I ended up creating cli, scraper and other three class files - total 5 files.

<h4>scraper.rb</h4>
In scraper.rb, I scraped text and url from website using Nokogiri. Nokogiri is an open source library to parser XML/HTML in Ruby. It was very very fun part for me when I finally get the data from website. I like it.

<h4>category.rb</h4>
This is a class file to initialize with arguments scraped in scraper.rb. I assigned attribute and stored information in class variable. I grabed title and url from the first page of the website - recipe category.

<h4>recipes.rb</h4>
This is also a class file. Recipe name and url were pulled from the second page of the website - recipe collection.

<h4>recipe.rb</h4>
This class file is for individual recipe. I scraped name, description and ingredients from the third page of the website - recipe.

So there are three levels - category - recipes(recipe collection) - recipe(individual recipe).
These three files - category.rb, recipes.rb, recipe.rb  - have almost the same format but each attribute value is different because the arguments were scraped from the different website pages.  

The object (argument) is instantiated in scraper.rb.

<h4>cli.rb</h4>
This is the file to interact with users and to work all together.

Interesting thing for me is CLI is not just providing information to users but also it can get the input result from users and pass it as argument so that we can instantiate in another files. That was my big "wow" moment. It is not just one way to give information to users but also provide another information based on what we received from users or what users want to know. It interacts with users indeed.

<h2>Final look</h2>
Let's look at my final interface together!<br>
Run `./bin/wholefoods_recipe`
<img src="../img/myimg/cli1.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli1.png) -->


<p>Let's type "list" to see recipe categories.</p>
<p>List is like this: </p>
<img src="../img/myimg/cli2.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli2.png) -->

<p>There are 119 categories!</p>
<img src="../img/myimg/cli3.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli3.png) -->


<p>Interested in one of these categories?? <br>
Type the number you like!</p>
<p>Let's type 119 this time. Now we can see the recipe list of "119. Surprising Sandwiches" below.</p>
<p> Pick the recipe you are curious about and type the number.</p>
<img src="../img/myimg/cli4.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli4.png) -->

Tada! We can see recipe name, description and ingredients. Isn't it cool!?
<img src="../img/myimg/cli5.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli5.png) -->

If you wants to see another recipe, you can type "y" and go back to the previous list.
<img src="../img/myimg/cli6.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli6.png) -->

If not, it exits.
<img src="../img/myimg/cli7.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli7.png) -->

<br>
<h2>Conclusion</h2>
<p>At the beginning of this project, I was only able to scrape the first level - I mean the first web page. I had a problem to understand how to provide another information using the class method and attribute value  I created. It didn't collaborate well but my mentor gave me a hint that "we can pass the object (user's input) to argument and scrape another date using that object. That object was url for the second page. Oh wow! Now I can scrape what a user exactly wants because we pass user's input to argument. At this point, I was able to grab data for the following pages and It continuously flows beautifully.</p>

<p>I also found that websites do not have the exact same HTML every page. Probably many sites usually have? I am not sure at this point but in this website, each page looks exactly same but some pages have different HTML tag or class name, which brake the code if I did not scrape correctly. It was interesting.</p>

<p>I learned a lot through this project but at the same time, I really enjoyed it! I can't believe that I didn't understand how to collaborate each class file a month ago. Learning is so much fun if I understand.  Coding makes me awake and even lift my mood up. I want to thank to my mentors and Flatiron community. They always help me how to figure out! This is not yet the final project, actually it is still the beginning,  but I feel appreciated.</p>
