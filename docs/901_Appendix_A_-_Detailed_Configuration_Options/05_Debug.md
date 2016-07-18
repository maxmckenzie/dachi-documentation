#### `debug.json` Debug Configuration File
**This file should only be modified by experianced developers or with assistance.**
##### `path` Debug Log Path *- string*
This should contain the path where Dachi should store all log files.
```json
	"path"      : "logs",
```
##### `database` Database Engine *- boolean*
Should we be debugging the database engine? Setting this to `true` will 
```json
	"database"  : false,
```
##### `template` Template Engine *- boolean*
Should we be debugging the template engine? Setting this to `true` will cause the generated templates have a
`__toString()` method that you can use to display the generated nodes.
```json
	"template"  : false
```