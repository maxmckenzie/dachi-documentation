Radon-UI is a javascript framework that we typically use with Dachi.

Radon-UI basically provides a framework for us to structure our JS simpler
```./src/radon.js```

There is some mandatory styling for the loading bar:
```
./src/pace-style.css
```

jQuery-Bind-First is a required lib so we make sure the framework the is the first thing called when .bind()ing.
```
./src/jquery.bind-first.js
```


### Using Ajax with Radon-UI

By using `class="ajax"` on any element (form/link/...), Radon-UI tells Dachi that the request is an ajax request by adding the parameter:
```
?radon-ui-ajax=true
```

Dachi now serves data objects, with a list of templates, instead of rendered html.

i.e:
`http://example.com/dashboard/?radon-ui-ajax=true`
```
Example response:
{
  "data": {
    "siteName": "Example",
    "timezone": "Europe/London",
    "domain": "example.com",
    "baseURL": "/dashboard",
    "assetsURL": "https://amazonaws.com/123123",
    "URI": [
      ""
    ]
  },
  "response": {
    "status": "assumed",
    "message": "Assuming successful."
  },
  "render_actions": [
    {
      "type": "display_tpl",
      "template": "@DashboardPage/dashboard",
      "target_id": "page_content"
    }
  ],
  "filament": {
    "environment": "development",
    "log": [],
    "time": 1469017355,
    "request_id": "2ff3a4ea3d26239881086bdffc51693f",
    "session_id": "7ff0epjqjdfkj40sutr8ao0cl1",
    "request": "{\"uri\":[\"\"],\"render_path\":\"\",\"data\":[],\"ajax\":true}"
  }
}
```
