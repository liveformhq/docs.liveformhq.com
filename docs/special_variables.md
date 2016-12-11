There are a few special variables which can be used with LiveForm. Here is a complete list of them and their purpose.

### 1. _noredirect
If you pass this the with the form submission, the response will not return a redirect.

```bash
curl -X POST \
  --data "name=Khaja Muzaffaruddin" \
  --data "bio=Awesome dude" \
  https://liveformhq.com/form/27fb4351-d2f7-45d3-96ac-8dae0eda2d26?_noredirect
```

```text
HTTP/1.1 200 OK
...
```
