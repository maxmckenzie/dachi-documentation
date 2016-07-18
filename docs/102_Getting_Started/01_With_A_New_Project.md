### Create Your Composer File
To create a new Dachi project, after ensuring you have all the requirements installed, you simply need to create a new
folder, and create a file called `composer.json`. This file should contian the text provided here. You should replace
`SampleClient\\SampleProject\\` with the correct namespace for your project, this can be anything you want but it's
recommended to follow the `Client\Project` format. This file is used to inform composer of our namespace, that we want
to use the private LemonDigits repository where Dachi and it's updates are served from and that we will be requiring
Dachi.
```javascript
{
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
    	{"type": "composer", "url": "http://packages.services.ld-cdn.com/"}
    ],
    "autoload": {
        "psr-4": {
            "SampleClient\\SampleProject\\": "src/"
        }
    },
    "require": { "ld-packages/dachi": "^2.0" }
}
```

### Install Everything
After creating this file you need to execute `composer install`. This will connect to our repository and download Dachi
and will then download all of Dachi's dependancies. Once this has finished, you can use the command line tool to
generate a new project, with the included sample code. If you are using windows, you should replace `/` with `\`.
```none
wiz@universe myproject> vendor/bin/dachi dachi:create
Copying project files...
Done!
wiz@universe myproject> _
```
`vendor/bin/dachi dachi:create`

### Initialize
Now your project will contain all of the required files with everything structured as required. There will also be an
example Module in the **/src/** folder, and an example Test in the **/tests/** folder. From here you should first
initalize everything by refreshing all the required pre-generated files and generating assets. If you are using
windows, you should replace `/` with `\`.
```none
wiz@universe myproject> vendor/bin/dachi dachi:all
[...]
--------------------------------------------------[ DONE! DONE!
wiz@universe myproject> _
```
`vendor/bin/dachi dachi:all`

### Configure
You should now configure your Dachi installation to your taste. Configuration is detailed fully in the Configuration
section. Once you have finished editing your Configuration. You should run the `dachi:config` or `dachi:all` command
line tool. This will regenerate your Configuration cache and allow your changes to take effect. If you are using
windows, you should replace `/` with `\`.
```none
wiz@universe myproject> vendor/bin/dachi dachi:config
Generating configuration file...
Done!
wiz@universe myproject> _
```
`vendor/bin/dachi dachi:config`