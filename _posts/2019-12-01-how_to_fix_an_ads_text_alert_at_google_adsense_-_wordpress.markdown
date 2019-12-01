---
layout: post
title:      "How to fix an ads.text alert at Google AdSense - WordPress"
date:       2019-12-01 23:20:45 +0000
permalink:  how_to_fix_an_ads_text_alert_at_google_adsense_-_wordpress
---



If you use Google AdSense to your website or blog, you might notice that there is an alert on your Home at Google AdSense like this:

![alert](http://yukijina.github.io/img/myimg/WP-alert.png)


I actually have not signed up my account for a while and not sure when this alert came up but I need to fix it. Otherwise, the ads won’t display correctly - meaning there is no revenue!

## What is this ads.text file for?
According to the Google,  
>“Authorized Digital Sellers, or ads.txt is an IAB initiative that helps ensure that your digital ad inventory is only sold through sellers (such as AdSense) who you've identified as authorized.” 


It prevents to sell ads to the counterfeit inventory and Google strongly recommends to add the ads.text file to your website, if you use Google AdSense.

## How to fix the problem:
1. Click `Fix now`
2. Click and open the `Create an ads.text file` massage
3. Click `download`. Then the ads.text is downloaded to your computer.
4. Save the ads.text file to the root level of your site like : http://yourwebsite.com/ads.txt

If you create your website/blog by yourself, it could be easier to find where the root directly is. But I use WordPress for my blog and I was not sure which folders I can add the file. Here is the solution:

### How to  fix the problem on WordPress: 
(it is the same procedure as above until no.3)

1. Click `Fix now`
2. Click and open the `Create an ads.text file` massage
3. Click `download`. Then the ads.text is downloaded to your computer.
4. Log in to your WordPress account and click `Plugins` at the right menu bar and click `Add New` 
![menu bar](http://yukijina.github.io/img/myimg/WP-menubar.png)

5. Search `Ads.txt Manager`. Install and activate the plugin
![ads manager image](http://yukijina.github.io/img/myimg/WP-adManager.png)

6. Go back to the ads.text file that you downloaded from Google AdSense and open the file. There is a code like `google.com, pub-XXXXXXXX, DIRECT, fXXXXXXXX`. Copy the code.
7. Go back to your Wordpress. Now the plugin should be activated. Click `Setting` at the bottom of the right menu bar
8. Select `ads.text`, and paste the code in the text file. The code was copied from ads.text file at Google AdSense.
9. Click `Save Changes`
 
 
Now all should be good.


If you go back to Google AdSense Home, the alert might still be there but it would be gone in several hours or the next day!




