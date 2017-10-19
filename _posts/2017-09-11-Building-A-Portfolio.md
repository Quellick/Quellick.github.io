---
layout: post
title: Setting Up A Portfolio w/ Jekyll
---
Hello,

So today I needed to set up a new blogging site as my portfolio website.  I am going to use Jekyll for the site template.   Jekyll allows you to create static websites and blogs using Markdown, Liquid, HTML, and CSS.  Since I already had a GitHub pages site I decided to just use their resources for hosting my new site.

https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/

First off, I was given a choice of two available themes of which I forked one repo into my GitHub.  I personally use GitHub Desktop as it makes cloning and forking branches a lot easier with its visual layout.  However, if you need the git commands to clone the repo as well as change the remote URL to your repository, they are.

$ git clone https://github.com/{username}/{portfolio-xxxx}.git

$ git clone https://github.com/{username}/{portfolio-xxxx}.git

Once all that was done I had a bare-bones template in my view and needed to start customizing it.  Within the _config.yml file there are many settings that need to be updated as they apply to you.  The actual site address for your portfolio (if you have a custom domain explained later in the post), username info for various social media, e-mails, site titles and descriptions, etc.  While it is not all required information I would fill in as much as possible, you can always go back and remove what you don't want to show on the page once you're familiar with the layout.  Once completed you should be able to reload the page and see a much more custom version of the theme you selected,  your name and accounts as well as social media icons linking to your username should now be visible.  Now.. about that custom domain.

We need to set up a custom domain for my portfolio site.  I was using <a href="https://pages.github.com/">Github Pages</a> to host my current site but wanted a more personal address for my portfolio.  There are quite a few options out there to purchase a domain name from, I chose <a href="https://www.namecheap.com/">Namecheap</a> to purchase mine from as I had experience with them in the past.  The process is fairly simple really, it may vary from company to company,  but you just type in the name you would like to use for your domain.  In my case I chose a character name I have used throughout my computing and video gaming career,  <a href="https://www.Quellick.com/">Quellick</a>.  It was available (meaning nobody else had purchased that specific name), so I purchased it for a year.  You can choose to purchase for a longer period of time but I find having to renew your domains once a year is a good time to audit them and make sure they are something you still need/want.

Once you have the domain name itself the rest is fairly simple for me as <a href="https://pages.github.com/">Github Pages</a> has a very simple process to set up redirects.  I just needed to go to my GitHub account,  select the repo I was using for my portfolio page, and then go into the settings for that repo.  Once in the options page, you just need to scroll down until you see the GitHub Pages section.  Within that section you should see a Custom Domain option,  just fill that in with the domain you purchased.

At this point, everything should be working right?  That's what I thought to.. but turns out I had to do some configuration with <a href="https://www.namecheap.com/">Namecheap</a> first.  Your DNS provider, in my case its the same as my domain name provider (most domain name registers offer some sort of free DNS providing as well). Using <a href="https://www.namecheap.com/">Namecheap's</a> dashboard it was easy to find the settings for my domain.  They show all the host records associated with a specific domain.  In this case, I needed to adjust the settings for my CNAME Record.  Namecheap had the site set up to visit their landing page rather than my portfolio.  So I updated the file with the correct Value.. in this case, my GitHub pages site address Quellick.github.io.  And now.. everything works.   If I type in quellick.com it now redirects me to www.quellick.com and it displays my portfolio page being hosted on GitHub pages but with my snazzy new personal domain name.  Now, what if someone wants to contact me?

I needed to add a contact form to my portfolio site so that potential employers, as well as anyone interested, could contact me.  I was referred to the [Get Simple Form](https://getsimpleform.com) site to get my API issued, I just provided my e-mail address and they provided a code block (sample) shown below.

{% highlight javascript %}
<form action="https://getsimpleform.com/messages?form_api_token=<your_api_token_here>" method="post">

  <!-- the redirect_to is optional, the form will redirect to the referrer on submission -->
  <input type='hidden' name='redirect_to' value='<the complete return url e.g. http://fooey.com/thank-you.html>' />

  <!-- all your input fields here.... -->
  <input type='text' name='test' />

  <input type='submit' value='Test form' />
</form>
{% endhighlight %}

All I had to do at this point was update my contact.md file with the proper API key after the form_api_token=<>  as well as plug in the proper web address for my GitPages site.  Now after reloading the page anyone should be able to send me an e-mail since the sight is already hosted.
