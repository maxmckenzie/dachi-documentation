Dachi ships with a Command Line Tool for managing the day-to-day Dachi related tasks. This tool is used for
pre-generating relevant files for Dachi to operate correctly. It is highly recommended you become familiar with the
available options. The examples shown are using *nix paths, if you are using windows, you should replace `/` with
`\` (i.e. `vendor\bin\dachi`).

#### `dachi:create` Create A Project
After installation, Dachi will do nothing. If you are not using an existing project, you must first create a project.
```none
wiz@universe myproject> vendor/bin/dachi dachi:create
Copying project files...
Done!
wiz@universe myproject> _
```

#### `dachi:all` Refresh Everything
Although most of the commands can be run separately, it is often best to ensure all cache files and internal
requirements are correct. This command will run all the relevant Dachi commands and will also attempt to update bower
components and generate the latest assets using Grunt.
```none
wiz@universe myproject> vendor/bin/dachi dachi:all
[...]
--------------------------------------------------[ DONE! DONE!
wiz@universe myproject> _
```

#### `dachi:route` Generate Routes
Before Dachi can route requests, the routing information cache will need to be generated. This will generate a
`cache/dachi.routes.json` file that will be used internally for routing requests. You must run this command every time
the routing table is changed.
```none
wiz@universe myproject> vendor/bin/dachi dachi:route
Loading controller classes...
[...]
Done!
wiz@universe myproject> _
```

#### `dachi:config` Generate Configuration
Dachi provides many JSON files for configuration. To speed up requests when deployed, these files must be concatenated
into a single quick-to-load file. This will generate a `cache/dachi.config.json` file that is used internally for
configuration. This command must be run again if the configuration files are changed.
```none
wiz@universe myproject> vendor/bin/dachi dachi:config
Generating configuration file...
Done!
wiz@universe myproject> _
```

#### `dachi:modules` Generate Module Information
Dachi use a system to provide features, such as shortcuts, to modules. Shortcuts allow you to use `SampleModule:Model`
instead of `SampleClient\SampleProject\SampleModule\Model` in your database requests and templates. This command will
also run the `__setup()` function on any controller if it has it defined. This system may be used in future for
providing other features to Modules. This will generate a `cache/dachi.modules.json` file that is used internally for
setting up modules. This command must be run again if a module is added/removed or renamed.
```none
wiz@universe myproject> vendor/bin/dachi dachi:modules
Loading controller classes...
[...]
Done!
wiz@universe myproject> _
```

#### `dachi:document` Generate Documentation
Dachi is completely documented using [ApiGen](http://www.apigen.org/). This tool will generate documentation in a
`documentation` folder. This documentation will include documention for your project, and the framework. It is advised
all projects also use the ApiGen format. The tool can be passed the `--internal` argument, this will then generate
documentation useful for debugging the Dachi core.
```none
wiz@universe myproject> vendor/bin/dachi dachi:document
Generating public documentation in 'documentation/public'...
[...]
Done!
wiz@universe myproject> _
```