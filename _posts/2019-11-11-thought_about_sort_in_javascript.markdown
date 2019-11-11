---
layout: post
title:      "Thought about sort in JavaScript"
date:       2019-11-11 05:19:38 +0000
permalink:  thought_about_sort_in_javascript
---

I recently practice a coding challenge and algorithm. So today I am writing about sort function in JavaScript.


## Array:
### sort array of numbers
`const numberArray = [-1, 14, 2, -3, 9]`

`numberArray.sort((a, b) => a - b)       =>  [-3, -1, 2, 9, 14]`

The opposite order:
`numberArray.sort((a, b) => b - a )    => [14, 9, 2, -1, -3]`
 
That is also same as:

```numberArray.sort(function(a, b) {
return a - b
})```
 
### sort array of strings
Array of strings are just as same as numbers above.

`const stringArray = ["coffee", "apple", "pineapple"]`

`stringArray.sort((a, b) => a - b)  => ["apple", "coffee", "pineapple"]`
 
### sort array of strings (unique characters)
But there is an exception. We need `localeCompare()` for unique charactors.

`const specialStringArray = ['réservé', 'premier', 'cliché', 'communiqué', 'café', 'adieu']`
 
`specialStringArray.sort((a, b) => a.localeCompare(b))  =>  [ 'adieu', 'café', 'cliché', 'communiqué', 'premier', 'réservé']`
 
## String
How about a string? Remember, `sort()` is function for Array. So we need to convert a string to an array and get it back to a string agin after sorted.

### sort strings
`const string = "pomegranate"`
`string.split("").sort().join("")   => “aaeeegmnoprt”`

The other order:
`string.split("").sort().reverse().join("") => “trponmgeeeaa”`
 
 
### sort numbers
We need one more step for the number. Let’s change it to a string first. The rest is the same as the above.

`const number = 4356612`

`Const newNumber = number.toString().split("").sort().join("")`
`parseInt(newNumber)`
 
Or one line:
`parseInt(number.toString().split("").sort().join(""))`
 


Sort is a basic function in JavaScript. However it is sometimes confusing how it works especially for numbers and strings.  



