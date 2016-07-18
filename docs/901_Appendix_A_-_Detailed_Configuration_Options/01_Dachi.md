#### `dachi.json` The Main Dachi Configuration File
##### `siteName` Site Name *- string*
This should contain the name of your application. This will be used throughout Dachi for many purposes and is
required.
```json
	"siteName"      : "Our Fancy Project",
```
##### `baseURL` Base URL *- string*
This should contain the full path, to Dachi, from the root of your web server. For instance, if Dachi is
installed at `http://mysite.com/ourfolder/dachi/` then this should be set to `/ourfolder/dachi`. This should **never**
have a trailing slash, if Dachi is installed in the root of your webserver then this must be left blank.
```json
	"baseURL"       : "/fancy",
```
##### `assets` Asset Storage Location *- string*
This should contain the full URL (or path if local) of your asset storage location. If you are running locally, this
will usually be `/build`. If you are using the Grunt+S3 deployment system, this will usually be something like
`https://s3-eu-west-1.amazonaws.com/our-fancy-project-assets`. This should **never** have a trailing slash.
```json
	"assets"        : "/build",
```
##### `logo` Logo Location *- string*
This should contain the full URL (or path if local) of your logo. Dachi doesn't require this by default, however it is
advised to be set as any Module may take advantage of it.
test
```json
	"logo"          : "/build/static/images/logo.png",
```
##### `domain` Domain *- string*
This should contain the domain name of your project. This will be used for any auto-generated links that may require a
fixed domain (i.e. OAuth callbacks, links in emails).
```json
	"domain"        : "our-fancy-project.com",
```
##### `timezone` Timezone *- string*
This should be set to the timezone in which you operate. Dachi will attempt to use this timezone when appropriate. This
must be a value from the [list provided by PHP](https://secure.php.net/manual/en/timezones.php)
```
	"timezone"      : "Europe/London"
```