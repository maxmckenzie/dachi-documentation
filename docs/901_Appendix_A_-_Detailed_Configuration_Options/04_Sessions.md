#### `sessions.json` Sessions Configuration File
##### `name` Session Identifier *- string*
This should contain a short string to identify your project. This will be used to ensure that any other projects running
on the same webserver or domain will not conflict.
```json
	"name"   : "our_fancy_project",
```
##### `domain` Domain *- string*
This should contain the domain name that sessions should be attached to. This can be set to `false` and will default to
use the same domain name as PHP, this is sufficiant for most cases, however setting this can increase security.
```json
	"domain" : "our-fancy-project.com",
```
##### `secure` Force HTTPS Security *- boolean*
If this is set to `true` then a valid session will only be allowed via https. If this is set to `false` then a valid
session will be allowed via both http and https.
```json
	"secure" : false,
```
##### `mode` Session Storage Mode *- string*
This configuration variable is currently un-used. In future, this will be used for enabling remote session storage for
multi-server load-balancing support.
```json
	"mode"   : "default"
```