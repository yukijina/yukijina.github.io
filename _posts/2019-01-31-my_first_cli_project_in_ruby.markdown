---
layout: post
title:      "My First CLI Project in Ruby"
date:       2019-02-01 03:16:02 +0000
permalink:  my_first_cli_project_in_ruby
---

I am writing about my first CLI - Command Line Interface -  project in Ruby.

To build the application, we need to create a gem, environment/executable/class files from scratch. We need to know how each file collaborates well in order to make CLI work beautifully.

I was so excited but at the same time, I felt a bit scared if I can make it work.
But it turned out it was so much fun to build the program and actually it was even addictive.

## Whole Foods Market Recipe Collection
I used a website from the Whole Foods Market Recipe Collection. They have a bunch of recipes on their website.<br>

Whole Foods website that I used for this project.<br>
[http://www.wholefoodsmarket.com/recipe-collections](http://www.wholefoodsmarket.com/recipe-collections)


<h2>Process making a CLI</h2>
Let's go through how to start a CLI project.
<br>
<p>To get started, we need to install a bundler in our computer.<br>
Bundler can install gems and tracks its version. It is not only managing Ruby gems dependencies but also we can create our own Bundler.</p>

<p>To check if you have a bundle, run the following code in the terminal. <p>
<code>bundle -v</code>

<p>If it is already installed, let's create own bundle gem.</p>
<code>bundle gem wholefoods_recipe</code>

<p>I named it as <code>wholefoods_recipe</code> based on my project but we can assign any name.</p>

<p>Now bin and lib directory, gemfile, gitignore, README.md, and other files were already created. This is pretty cool!! </p>

<h3>.gemspec file</h3>
We have to update <code>spec.summery</code>,<code>spec.description</code> and <code>spec.homepage</code>. I also added <code>gem 'pry'</code> and <code>gem 'nokogiri'</code> at this point. Run <code>bundle</code> in the terminal if everything works okay.
<br>

<h3>Class and CLI files</h3>
I also liked to create some files at the beginning. I definitely needed files for:
<br>

<ul>
<li>cli.rb - CLI controller, interact with users</li>
<li>scraper.rb - scrape data from website</li>
<li>category.rb - class file, assign attribute</li>
</ul>

<p>These are minimum files I created at first but I created more class files to define methods from different pages later.</p>

<h3>Executable file</h3>
<code>bin</code> -  This is executable directory.

<p>Inside this bin directory. Let's create a new file which is going to be my main executable file.</p>
 <code>bin/wholefoods_recipe</code>

<p>In this executable file, I have to write the following code on top of the page because the file does not have an extension. I want to set my environment to ruby. It is called "shebang"</p>
<code>#!/usr/bin/env ruby</code>

<p>Underneath of this code, I wrote lib directory path, that is my environment file.</p>
<code>require_relative "../lib/wholefoods_recipe"</code>

<p>Note: <code>lib</code> is not located in the same directory so we need to use two dots <code>../lib</code> . If it is in the same directory, we can use just one dot.</p>

<h3>Environment file</h3>
<code>lib/wholefoods_recipe</code>

This is my environment file and I wrote all the file paths in this file :
<p>i.e<br>
<code>require_relative "./wholefoods_recipe/cli"</code><br>
<code>require_relative "./wholefoods_recipe/category"</code><br>
<code>require_relative "./wholefoods_recipe/scraper"</code></p>

<h3>My Class files</h3>
I ended up creating cli, scraper and other three class files - total 5 files.
<br>

<h4>&#10033; scraper.rb</h4>
I scraped data such as text and URL from the web pages using Nokogiri. Nokogiri is an open source library to parse XML/HTML in Ruby. It was very fun when I finally obtain the data from the website.
<br>

<h4>&#10033; category.rb</h4>
This is a class file. Title and URL are scraped from the first page of the website - in scraper.rb. Those data was passed through argument - category.
<br>

<h4>&#10033; recipes.rb</h4>
This is also a class file. Recipe name and URL were scraped from the second page of the website - recipe collection.
<br>

<h4>&#10033; recipe.rb</h4>
This class file is for an individual recipe. I scraped name, description, and ingredients from the third page of the website - recipe.

<p>So there are three levels - category - recipes(recipe collection) - recipe(individual recipe).</p>
<p>These three files - category.rb, recipes.rb, recipe.rb  - have almost the same formats but each property is different because the arguments were scraped from the different website pages. The object is instantiated in scraper.rb.</p>
<br>

<h4>&#10033; cli.rb</h4>
This is the file to interact with users and to work all together.

<p>CLI is not just one way to give information to users but also provide another information based on what we received from users or what users want to know.</p>

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


<p>Type the number you like!<br>
I type 119 this time and we can see the recipe list of "119. Surprising Sandwiches" below.<br>

Pick the recipe you are curious about and type the number.
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
<p>At the beginning of this project, each file didn't collaborate well but my mentor gave me a hint that "we can pass the object (user's input) to argument and scrape another data using that object. That object was URL for the second page. Oh wow! Now I can scrape what the user exactly wants because we pass user's input to the argument. Beautiful.</p>

<p>I also found that some web pages do not have the exact same HTML every page. Each page looks exactly the same but some pages have different HTML tag or class name, which brake the code if I did not scrape correctly. It was interesting but challenging.</p>

<p>I learned a lot through this project but at the same time, I really enjoyed it! Learning is fun. Coding makes me awake and even lift my mood up &#9786;</p>
