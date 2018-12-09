---
layout: post
title:      "Set a counter in Ruby Loops"
date:       2018-12-09 03:03:33 +0000
permalink:  set_a_counter_in_ruby_loops
---

Loops are used to execute the same block of code a specific number of times. If we want to output "I love Ruby!" message certain times, we can use loops and set a counter to count how many times it is looping over.

My question was "should I write a counter before or after `puts` message? "

Well.. it depends or doen't matter. <br>
But it made me confused.

At the end of challenge, I found both ways worked so I kept going.
But now it is time to figure out how it works and what is the difference. So I won't be frustrated next time.

Let's see simple while loops below.
We set a counter (valuable `i`) equal to 0 and increment by 1. If `i` hits 5, it executes.

<h4>Case 1.  Increment `i` after `puts` </h4>
```
i = 0
while i < 5
  puts i
  i += 1
end
```
`result --> 0,1,2,3,4`

First result is `0`. `i` is still equal to 0 because we wrote `i += 1` after `puts i`.
1 is added at the next line. And it continues.

When `i = 4`, it outputs `4`. Right after `puts` line, `i` becomes equal to `5` and the loop ends. At the next round, `i` is not less than 5 anymore so it executes without outputting 5.

<h4>Case 2. Increment `j` before `puts`</h4>
```
j = 0
while j < 5
  j += 1
  puts j
end
```

`result --> 1,2,3,4,5`

First output is `1`, not 0.  `j` is incremented just before `puts` message. 
When `j = 4`, it increments by 1, outputs `5` and executes.

<br>
<br>
Return value changes by writing counter before or after `puts`.

In the case 2, I thought it would not output `5` . Because it is supposed to be less than 5!?  I was confused when it outputs `5` . But that's right, if I look the code carefully, it makes sense. It does not mean greater than 5 but simply `puts` is wrote after the counter is incremented.

By the way, if we don't output counter, we may not realize the difference. 
Let's say we want to output message `I love Ruby!` in both case1 and case 2. Both outputs message 5 times and we have the same results like:


```
result  -->
I love Ruby!
I love Ruby!
I love Ruby!
I love Ruby!
I love Ruby!
```

Both ways work the same. I was unconsciously doing that so I found the difference between case 1 and case 2, aha moment came to me!

In the following codes, I only changed arithmetical operator from less than (`<`) to less than or equal to (`<=`).

<h4>Case 3.  Increment `i` after `puts` (same as case 1, but `i <= 5`)</h4>
```
i = 0
while i <= 5
  puts i
  i += 1
end
```

`result --> 0,1,2,3,4,5`


<h4>Case 4. Increment `j` before `puts` (same as case 2, but `j <= 5`)</h4>
```
j = 0
while j <= 5
  j += 1
  puts j
end
```

`result --> 1,2,3,4,5,6`

I had another belief that it only outputs 5 times either we use `< 5` or `<=5`. But if we understand case 1 and case 2, we know that is not true.
<br>
<br>
It was fun to test codes. 
When I finally understand the difference, it makes me happy :)
