---
layout: post
title:      "Ruby String Methods - Palindrome"
date:       2018-12-02 17:26:10 -0500
permalink:  ruby_string_methods_-_palindrome
---

Today I worked on Ruby string methods to check if the string is palindrome. I was thinking to write down whole process of coding, but it turned out the blog was going to be very long. I want to write down some string methods I learned and want to keep in my mind. 


What is palindrome?
> "A palindrome is a word, number, phrase, or other sequence of characters which reads the same backward as forward"  - wikipedia


e.g.  abccba, madam

<br>
We pass one argument - string - and then check if the string is palindrome. <br>
My approach is:
1. divide the string to two
2. if the first and the second divided half are the same strings, it is palindrome.

If we pass the string "abccba", it is divided to the first "abc" and the second "cba".
Then reverse the second part "cba" to "abc". If both are matched, it is palindrome.

`string.gsub(/[\s,\!\-]/ ,"").downcase`

#gsub method takes two arguments. <br>
`#gsub(pattern, replacement) --> new_str` <br>
The first is text you want to remove and the second is new text you want to replace.

Let's look closely in the parentheses.
* ` \s,` removes white space and comma
* `\! `   removes exclamation mark
* `\- `   removes hyphen

We put all the above in the array and wrap with forward slash `/  /`. <br>
After the comma is a replacement. In this case,  non-space `""` .

Let's say we pass the string "abc! c B,a". 

`string.gsub(/[\s,\!\-]/ ,"") --> "abccBa"`

Cool! All unnecessary characters and white space were removed.

After #gsub, we have `#downcase`, which replace all the uppercase letters with lowercase letters.
The string outputs "abccba" now.


How to divide strings?<br>
Characters can't be divided so we need to get the number of letters of the string.<br>
`#length` or `#size` return the character length of string. <br><br>
`string.length / 2`

if the string is  "abccba", result is  3. <br>
Let's keep this result in variable name "median".

`median = string.length / 2  -->   3  (median = 3)`

To get the first half of string,  I used #slice. Slice takes two arguments. The first is index and the second is length:

`#slice(index, length)`

`first_half_str = string.slice(0, median)  --> "abc"` <br>
 meaning, slice(index:0, length: 3). we got the characters from 1 to 3.

`second_half_str = string.slice(median, str.length) --> "cba"` <br>
 meaning, slice(index: 3,  length:6). We got the characters from 3 to 6.

<br>
Reverse string<br>
#reverse can reverse the character. Let's revise the second_half_str "cba" to "abc". <br>
`revised_second_half_str = second_half_str.reverse  --> "abc"`

Great! Now we can compare the first half "abc" and the revised second half "abc".
<br>

Ok, I though I was actually done here but when I checked the definition of palindrome in wikipedia above, I realized "madam" is also palindrome. Right... it is same when we read backward.

"abccba" has 6 characters and can be divided by 2 to make it half. I thought palindrome is only even number but it is not.

 "madam" has 5 characters. It means it can' be divided by 2. Well...in this case, if we divide "madam" by 2 (character length 5), it returns 2. It is round down.

We need to add extra steps to make it work. 

`"madam".length / 2 -- > 2`

When we apply the string methods mentioned above, we can get:<br>
`first_half_str = "ma"  ` <br>
`second_half_str = "dam"` <br>
`revised_second_half_str = "mad"`

Even though we know "madam" is palindrome, if we compare these two strings, we get the error. "ma" and "mad" is obviously not the same.

To make things work, let's remove "d" in the revised_second_half_str "mad". 

First, we get the last character <br>
`last_char = revised_second_half_str[-1, 1]`

`#str[start, length]`<br>
It takes two arguments. First -1 means "last character".
Second 1 means "one length." So we take out one last character

Then let's remove the last character using #chomp<br>
`revised_second_half_str.chomp(last_char)`

We can put two methods in one line: <br>
`revised_second_half_str.chomp(revised_second_half_str[-1, 1])  --> "ma"`

Good! So now even if we pass strings with odd length, it will work.


This is just a preparation. <br>
We need to define methods to check if the string is palindrome.<br>
If you are interested in whole process, please check my GitHub repo.

I am sure there are many different or better ways to check palindrome string but as of now, I am happy to understand string methods I learned in this project.

Thanks for reading!! Let's keep learning.

 







