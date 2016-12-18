# Documentation Home

LiveForm allows you to make online forms easily. It allows you to use a form without the annoying
iframes and doesn’t impose any pre-built themes on your forms.

The only thing you need to change, to use simple form, is the `action` attribute on your form and use the `post method` on it.

An example of the form's usage is at [https://liveformhq.com/#contact](https://liveformhq.com/#contact) You can checkout the source, it's very simple.

~~~html
<form role="form" action="https://liveformhq.com/form/00a1265d-af82-44dc-aba7-8ef01018c6c3" method="POST" accept-charset="utf-8">
  <input type="hidden" name="utf8" value="✓">
  <input type="hidden" name="_redirect" value="https://liveformhq.com/thank_you">

  <div class="form-group">
    <label for="name">Name</label>
    <input type="text" class="form-control" name="name" id="name" placeholder="Name">
  </div>

  <div class="form-group">
    <label for="email">Email address</label>
    <input type="email" class="form-control" name="email" id="email" placeholder="Email">
  </div>

  <div class="form-group">
    <label for="message">Message</label>
    <textarea class="form-control" rows="5" name="message" id="message" placeholder="Your message..."></textarea>
  </div>

  <button type="submit" class="btn btn-default">Send Message</button>
</form>
~~~

### Screenshot of the above contact form
![Contact Form](/images/liveform-contact.png)

As you can see, live form integrates easily and seamlessly into your app. Hope you guys find it useful.


### File Uploads

File uploads are very simple using liveform. You can now do file uploads using Liveform.
You just need two things to be able to upload files.

 1. Make sure your form has an attribute `enctype="multipart/form-data"`
 2. Add a file field e.g. `<input type=file name=resume />`

That's it, once you have those, files can be uploaded through your forms.
