Dachi uses Grunt & Bower to manage all the assets, javascript & stylesheets your project uses. This allows easy and
automated management of both Bower components and custom project assets. This pipeline allows you to just worry about
writing your stylesheets and javascript and not worry about how all of it will be served to the end-user.

#### Running the pipeline
The pipeline is super simple to use. Simple run `grunt` from your terminal after installation and everything will
automagically happen and our will pop a `build` folder, this folder will contain all the compiled assets. You can also
run `grunt watch` if you would like your assets folder to be watched for changes and automatically compiled.
```none
wiz@universe myproject> grunt
[...]
Done, without errors.
wiz@universe myproject> _
```

#### JavaScript
By default, javascript files in the `assets/javascript` folder will be concatenated to a `default.js` file (and then
minified by the rest of the pipeline). The ordering of these javascript files is not guaranteed to be consistant. You
can add additional javascript folders if you would like to split your application into sections using the
`grunt.bower.json` configuration file (see Appendix A).
```javascript
function smile() {
	return ":-)";
}
```

#### Stylesheets
Dachi implements LESS for better CSS handling. This provides us with a wealth of additional features over traditional
CSS. So much so that we no longer support standard CSS in our pipeline. By default, the `assets/lcss/styles.less` file
will be compiled to a `default.css` file (and then minified by the rest of the pipeline). This LESS file can include
additional files and therefore has no issues with ordering.
```css
.smile {
	.face(yellow);
	content: ':-)';
}
```

#### Bower
The pipeline will automatically attempt to concatenate all Bower components that have been required. This process depends
upon the components defining the "main files" in the `bower.json` file. However, some modules do not implement this and
you will have to manually set the main files using the `grunt.bower.json` configuration file (see Appendix A).
```none
wiz@universe myproject> bower install bootstrap
[...]
bootstrap#x.x.x bower_components\bootstrap
wiz@universe myproject> _
```

### Grunt Templates
There is built in support for using deploy-time variables in templates. Your template file must end with `.twig-default`
instead of `.twig`. The pipeline will the automatically perform replacements inside this file and generate the template
file. This is used to generate the correct paths for assets and to allow environment specific generation. This is used
extensively in the `view/base.twig-default` file.

#### Deployment
The pipeline will automatically attempt to upload the finished asset package to S3 if the executing environment isn't 
local, and S3 credentials must be specified in the configuration files for this to function.