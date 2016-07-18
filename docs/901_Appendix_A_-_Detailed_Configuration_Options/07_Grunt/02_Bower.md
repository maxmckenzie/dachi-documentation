#### `grunt.bower.json` Bower Configuration File
##### `mainFiles` Main Files for Libraries *- object*
This should contain an object, with a key for each bower component that you wish to specify a main file for. This is
used for concatenating components that don't specify their main file.
```json
	"mainFiles": {
		"xxxxx" : "lib/xxxx.js"
	},
```
##### `exclude` Libraries to Exclude *- array[string]*
This should contain an array of components to exclude from concatenation. The primary use case for this is allowing
inclusion of components with LESS files, as these files are better handled manually with the LESS Grunt action.
```json
	"exclude": ["xxxxx"]
```