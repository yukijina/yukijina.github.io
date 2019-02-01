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
Let's go through how to start CLI project.
<br>
<p>To get started, we need bundler installed in our computer.<br>
Bundler can install gems and tracks its version. Bundle is not only managing Rubygems dependencies but also we can create our own Bundler.</p>

<p>To check bundle, run the following code in the terminal. <p>
<code>bundle -v</code>

<p>If it is already installed,  let's create own bundle gem.</p>
<code>bundle gem wholefoods_recipe</code>

<p>I named it as <code>wholefoods_recipe</code> according to my project but you can assign any name here.</p>

<p>Now bin and lib directory, gemfile, gitignore, README.md and other files were already created. This is pretty cool!! </p>

<h3>.gemspec file</h3>
We need to update <code>spec.summery</code>,<code>spec.description</code> and <code>spec.homepage</code>. I also added <code>gem 'pry'</code> and <code>gem 'nokogiri'</code> at this point. Run <code>bundle</code> in the terminal if everything works okay.
<br>

<h3>class and cli files</h3>
I also like to create some files at the beginning. I definitely needed files for:
<br>

<ul>
<li>cli.rb - CLI controller, interact with users</li>
<li>scraper.rb - scrape data from website</li>
<li>category.rb - class file, assign attribute</li>
</ul>

<p>These are minimum files I created at first but I created more class files to define methods from different pages later.</p>

<h3>Executable file</h3>
<code>bin</code> -  This is executable directory.

<p>Inside this bin directory, I created new file which is my main executable file.</p>
 <code>bin/wholefoods_recipe</code>

<p>In this executable file, I need to write the following code on top of the page because the file does not have extension. We need computer to read correctly - this is ruby file. It is called "shebang"</p>
<code>#!/usr/bin/env ruby</code>

<p>Underneath of this code, I wrote lib directory path, that is our environment file.</p>
<code>require_relative "../lib/wholefoods_recipe"</code>

<p>Note: <code>lib</code> is not located in the same directory so we need to use two dots <code>../lib</code> . If it is in the same directory, we can use just one dot.</p>

<h3>Environment file</h3>
<code>lib/wholefoods_recipe</code>

This is my environment file and I wrote all the file paths in this folder :
<p>i.e<br>
<code>require_relative "./wholefoods_recipe/cli"</code><br>
<code>require_relative "./wholefoods_recipe/category"</code><br>
<code>require_relative "./wholefoods_recipe/scraper"</code></p>

<h3>My Class files</h3>
I ended up creating cli, scraper and other three class files - total 5 files.
<br>

<h4>scraper.rb</h4>
In scraper.rb, I scraped text and url from website using Nokogiri. Nokogiri is an open source library to parser XML/HTML in Ruby. It was very very fun part for me when I finally get the data from website. I like it.
<br>

<h4>category.rb</h4>
This is a class file to initialize with arguments scraped in scraper.rb. I assigned attribute and stored information in class variable. I grabbed title and url from the first page of the website - recipe category.
<br>

<h4>recipes.rb</h4>
This is also a class file. Recipe name and url were pulled from the second page of the website - recipe collection.
<br>

<h4>recipe.rb</h4>
This class file is for individual recipe. I scraped name, description and ingredients from the third page of the website - recipe.

<p>So there are three levels - category - recipes(recipe collection) - recipe(individual recipe).</p>
<p>These three files - category.rb, recipes.rb, recipe.rb  - have almost the same format but each attribute value is different because the arguments were scraped from the different website pages. The object (argument) is instantiated in scraper.rb.</p>
<br>

<h4>cli.rb</h4>
This is the file to interact with users and to work all together.

<p>CLI is not just one way to give information to users but also provide another information based on what we received from users or what users want to know. When I understood this flow, I felt amazing.</p>

<h2>Final look</h2>
Let's look at my final interface together!<br>
Run <code>./bin/wholefoods_recipe</code></p>

<img src="../img/myimg/cli1.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli1.png) -->


<p>Let's type "list" to see recipe categories.<br>
List is like this: </p>
<img src="../img/myimg/cli2.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli2.png) -->

<p>There are 119 categories!</p>
<img src="../img/myimg/cli3.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli3.png) -->


<p>Interested in one of these categories?? <br>
Type the number you like!</p>
<p>I type 119 this time. Now we can see the recipe list of "119. Surprising Sandwiches" below.</p>
<p> Pick the recipe you are curious about and type the number.</p>
<img src="../img/myimg/cli4.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli4.png) -->

<p>Tada! We can see recipe name, description and ingredients. Isn't it cool!?</p>
<img src="../img/myimg/cli5.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli5.png) -->

<p>If you want to see another recipe, you can type "y" and go back to the previous list.</p>
<img src="../img/myimg/cli6.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli6.png) -->

<p>If not, it exits.</p>
<img src="../img/myimg/cli7.png">
<!-- ![cli project image](http://yukijina.github.io/img/myimg/cli7.png) -->

<br>
<h2>Conclusion</h2>
<p>At the beginning of this project, it didn't collaborate well but my mentor gave me a hint that "we can pass the object (user's input) to argument and scrape another data using that object. That object was url for the second page. Oh wow! Now I can scrape what a user exactly wants because we pass user's input to argument.It flows beautifully.</p>

<p>I also found that some websites do not have the exact same HTML every page.Each page looks exactly same but some pages have different HTML tag or class name, which brake the code if I did not scrape correctly. It was interesting and challenging.</p>

<p>I learned a lot through this project but at the same time, I really enjoyed it! Learning is so much fun if I understand. Coding makes me awake and even lift my mood up.</p>
