---
layout: post
title:      "Thought about sort in JavaScript"
date:       2019-11-11 05:19:38 +0000
permalink:  thought_about_sort_in_javascript
---

I recently practice a coding challenge and algorithm. Sorting arrays and strings are a bit different. Once you understand the logic, it is not difficult but I thought it was good to organize my thoughts about how sort() works so I want to leave a note here.


## Array:
### *sort array of numbers
`const numberArray = [-1, 14, 2, -3, 9]`

`numberArray.sort((a, b) => a - b)` 
`#result =>  [-3, -1, 2, 9, 14]`

The opposite order:<br>
`numberArray.sort((a, b) => b - a )`
`#result => [14, 9, 2, -1, -3]`
 
That is also same as:<br>
```numberArray.sort(function(a, b) {
return a - b
})```
 
### *sort array of strings
Array of strings are just as same as numbers above.

`const stringArray = ["coffee", "apple", "pineapple"]`

`stringArray.sort((a, b) => a - b)`
`#result => ["apple", "coffee", "pineapple"]`
 
### *sort array of strings (unique characters)
But there is an exception. We need `localeCompare()` for unique characters. Without this function, it can't be sorted.

`const specialStringArray = ['réservé', 'premier', 'cliché', 'communiqué', 'café', 'adieu']`
 
`specialStringArray.sort((a, b) => a.localeCompare(b))`
`#result => [ 'adieu', 'café', 'cliché', 'communiqué', 'premier', 'réservé']`
 
## String
How about a string? Remember, `sort()` is function for Array. So we need to convert a string to an array and get it back to a string agin after sorted.

### *sort strings
`const string = "pomegranate"`<br>
`string.split("").sort().join("")`
`#result => “aaeeegmnoprt”`

The other order:<br>
`string.split("").sort().reverse().join("")`
`#result => “trponmgeeeaa”`
 
 
### *sort numbers
We need one more step for the number. Let’s change it to a string first. The rest is the same as the above.

`const number = 4356612`

`const newNumber = number.toString().split("").sort().join("")`
`parseInt(newNumber)`
`#result => 1234566`
 
Or one line:<br>
`parseInt(number.toString().split("").sort().join(""))`
`#result => 1234566`
 


Sort is a basic function in JavaScript. However it is a bit tricky to understand how it works for numbers and strings. The function itself is for Array so that we can use it for a string by changing a string to an array - `split("")`.




