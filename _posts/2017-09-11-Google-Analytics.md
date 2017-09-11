---
layout: post
title: Adding Google Analytics to a Jekyll blow
---

I needed to add google analytics to my Jekyll portfolio page so I could see if anyone was viewing it.  I have used google analytics on other website so I am familiar with the process,  but it is slightly different using a Jekyll page as it has the _config.yml file.  Upon opening the file and looking at all the settings, this file has many empty fields to be filled in with various account and user information from around the web.  But if you scroll down to the SCRIPTs section of the file you should notice this block of code.

# Scripts
  google_analytics: "your tracking ID here"
  disqus_shortname:
  katex: true # Enable if using math markup

All you will need to do is log into or create a google analytics account.  Once created you should see an admin option either on the left tool bar or at the top header of the page.  Select this and you should see an accounts summary.. select the accounts option and create a new account.  You will need to name it and set the website name and address for our purposes just youse your github pages address in my case it would be Quellick.github.io.  Set your time zone then you can complete the process, you shouldn't need to adjust any other settings.  It's just that simple!  Now you too can marvel at all of the information provided by google analytics and wonder what it's all for!
