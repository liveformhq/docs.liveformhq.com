There are a few special variables which can be used with LiveForm. Here is a complete list of them and their purpose.

### 1. _noredirect
If you pass this the with the form submission, the response will not return a redirect.

```bash
curl -X POST \
  --data "name=Khaja Muzaffaruddin" \
  --data "bio=Awesome dude" \
  https://liveformhq.com/form/27fb4351-d2f7-45d3-96ac-8dae0eda2d26?_noredirect
```

The `_noredirect` parameter can be appended the url as a query string like above. Or it can be set using a hidden input field.

The resposne to this will be

```text
HTTP/1.1 200 OK
...
```

### 2. _redirect
Passing an input parameter with this name will redirect the user to its value. For instance in the example below, once the user submits
the form, he will be redirected to `https://awesome.com/thank-you#thanks`

```bash
curl -X POST \
  --data "Zainab" \
  --data "bio=Awesome dude" \
  --data "_redirect=https://awesome.com/thank-you#thanks" \
  https://liveformhq.com/form/27fb4351-d2f7-45d3-96ac-8dae0eda2d26?_noredirect
```

This can be used to redirect the user to a thank you page. If you don't have a dedicated thank you page, you can still append a "#thank-you" fragment to the form's url
and show a thank you message via javascript if it is present.

Please note that this should be a full url and not a relative url. e.g. passing "/thanks" in _redirect will not work.

### 3. g-recaptcha-response
This holds the recaptcha response for your form, if you are using google's recaptcha. We use this data to verify if a message is spam.

### 4. _utf8
You can add an input field with a name `_utf8` and set it to a unicode character like the ✓ mark. The purpose of this is explained here: http://stackoverflow.com/a/3348524/24105
