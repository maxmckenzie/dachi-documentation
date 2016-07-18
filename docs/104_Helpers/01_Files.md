#### `helpers.files.json` Files Configuration File
##### `handler` File Storage Handler *- string*
This should contain the file storage handler you wish to use. Valid options: `local` store files locally. `s3` store
files using AWS S3.
```json
	"handler" : "s3"
```