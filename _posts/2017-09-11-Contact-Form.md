---
layout: post
title: Setting Up The Contact Form
---

I needed to add a contact form to my portfolio site so that potential employers as well as anyone interested could contact me.  I was refered to the [Get Simple Form](https://getsimpleform.com) site to get my API issued, I just provided my e-mail address and they provided a code block (sample) shown bellow.

{% highlight javascript %}
<form action="https://getsimpleform.com/messages?form_api_token=<your_api_token_here>" method="post">

  <!-- the redirect_to is optional, the form will redirect to the referrer on submission -->
  <input type='hidden' name='redirect_to' value='<the complete return url e.g. http://fooey.com/thank-you.html>' />

  <!-- all your input fields here.... -->
  <input type='text' name='test' />

  <input type='submit' value='Test form' />
</form>
{% endhighlight %}

All I had to do at this point was update my contact.md file with the proper API key after the form_api_token=<>  as well as plug in the proper web address for my GitPages site.  Now after reloading the page anyone should be able to send me an e-mail once the site is hosted online.
