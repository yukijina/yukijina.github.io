---
layout: post
title:      "Boostrap 4 Grid sytem"
date:       2019-03-09 20:46:01 +0000
permalink:  boostrap_4_grid_sytem
---


Bootstrap grid sysmte makes it much easier to create a responsive website. I found there were some keys to remember when we make colums nicely.


When we make columun using `.col` , each column has default horizontal padding (px-3 =>padding both right and left). Defaul it only horizontal, not vertical. We can easily change this by using `.px- ` and `py- ` and even can reset by using `p-0`.  Through my experiments, when we make space between columns, it is easier to adjust padding but not margin. Probably it is fine to change vertical margin but if you change horizontal margin, column does not fit in a row anymore.

Here is my experiment:

<img src="../img/myimg/bootstrap-grid.png" alt="grid image">
