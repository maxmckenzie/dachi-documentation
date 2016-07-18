### Checkout Your Project
Create a folder containing your project files (typically using git) and ensure that your web server is correctly serving
this folder. You will have to make sure your project is being served from the correct URL, or you will have to update
the configuration files with the required URLs.

### Install Everything
Once your project is ready you should run `composer install`. This will connect to our repository and download Dachi and
will then download all of Dachi's dependancies.
```none
wiz@universe myproject> composer install
[...]
wiz@universe myproject> _
```

### Initialize
Now your project will contain all of the required files with everything structured as required. From here you should 
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
Your configuration should be correct if you are using an existing project. If it is not, you should correct it then run
the `dachi:config` or `dachi:all` command line tool. This will regenerate your Configuration cache and allow your
changes to take effect. Configuration is detailed fully in the Configuration section. Once you have finished editing
your Configuration. You should run the `dachi:config` or `dachi:all` command line tool. If you are using windows, you
should replace `/` with `\`.
```none
wiz@universe myproject> vendor/bin/dachi dachi:config
Generating configuration file...
Done!
wiz@universe myproject> _
```
`vendor/bin/dachi dachi:config`