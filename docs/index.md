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

### API

If you go to the form's API page, you'll see a simple jQuery code snippet which shows you how to
access your messages via the API. To access the form submissions you need to pass a url with a valid form id
a valid form api_key and an optional `page` parameter. Pagination can be performed using the `page` parameter

To see how you can use the API to build an html page app checkout our blog post on
[ Creating an Imgur clone using Github Pages and Liveform.](http://blog.liveformhq.com/2016/11/27/creating-an-imgur-clone-using-github-pages-and-liveform/)

```javascript
$.get("https://api.liveformhq.com/v1/forms/369c5f72-7940-4d20-b3c7-8a963fc49a15/messages", {
    api_key: "11d43d92-d928-4a8b-b55c-50f98227c794",
    page: 1, // if you don't pass a page param, the first page is returned
    page_size: 25 // the default page_size is 25, you can pass a value between 1 and 100 as the page_size
  },
  function(messages) {
    console.log(messages)
  })
```

Here is a sample response from the API
```javascript
{
    "messages": [{
        "id": "56c22cba-530e-4f76-9444-ed9fd14688a0",
        "data": {
            "title": "Aeroplane Rawcode",
            "upload": "https://s3.amazonaws.com/liveform/files/50c662eb-7646-4176-839c-ddea9ea61486/aeroplane.jpg"
        },
        "form_id": "369c5f72-7940-4d20-b3c7-8a963fc49a15",
        "request_ip": "183.83.175.192",
        "spam": false,
        "archived_at": null,
        "created_at": "2016-11-27T19:54:44.993Z",
        "updated_at": "2016-11-27T19:54:45.191Z"
    }, {
        "id": "dbb365db-b929-4a8f-970b-fbfbf83a58f5",
        ...
    }, { ... }, ...],
    "meta": {
        "current_page": 2,
        "next_page": 3,
        "prev_page": 1,
        "total_pages": 5,
        "total_count": 120,
        "next_link": "https://api.liveformhq.com/v1/forms/369c5f72-7940-4d20-b3c7-8a963fc49a15/messages?page=3",
        "prev_link": "https://api.liveformhq.com/v1/forms/369c5f72-7940-4d20-b3c7-8a963fc49a15/messages?page=1"
    }
}

```

![Liveform API Code](/images/liveform-api.png)

