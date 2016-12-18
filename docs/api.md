# API

LiveForm has a simple read only JSON api at the moment. Here is how you can use it

Request

```bash
# if you don't pass a page param, the first page is returned
# the default page_size is 25, you can pass a value between 1 and 100 as the page_size

curl -X GET \
    --data page=1 \
    --data page_size=25 \
  'https://api.liveformhq.com/v1/forms/369c5f72-7940-4d20-b3c7-8a963fc49a15/messages?api_key=11d43d92-d928-4a8b-b55c-50f98227c794'
```

Response

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
        "data": {
            "title": "Cats !!",
            "upload": "https://s3.amazonaws.com/liveform/files/ec380243-e97b-4c7f-a38b-ffc6facaba6c/cat1.jpeg"
        },
        "form_id": "369c5f72-7940-4d20-b3c7-8a963fc49a15",
        "request_ip": "183.83.175.192",
        "spam": false,
        "archived_at": null,
        "created_at": "2016-11-27T12:53:59.055Z",
        "updated_at": "2016-11-27T12:53:59.365Z"
    }],
    "meta": {
        "current_page": 1,
        "next_page": null,
        "prev_page": null,
        "total_pages": 1,
        "total_count": 7,
        "next_link": null,
        "prev_link": null
    }
}
```

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


