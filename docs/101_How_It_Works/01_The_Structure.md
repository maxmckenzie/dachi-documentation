### Modules
It is good practice to componentize code for a website. Dachi supplies this through the use of Modules. Modules are
simply folders in the **/src/** directory, and the usage of modules is more of a theoretical concept. A Module should
implement a single concept in your project. A Module can communicate with other Modules with ease. Doctine (for models)
and Twig (for templating) both support namespacing, in these cases we automatically namespace to the module name. For
example, let's say we are developing a project to help a small business manage their a list of their suppliers, place
orders with suppliers and manage clients. We would typically attempt to split the project into it's core components, and
then build the controllers under these components. In this case we would have a structure similar to the one shown.
```
|-- Suppliers
|   |- views
|   |  '- [...]
|   |
|   |- ControllerManage.php
|   |- ControllerAudit.php
|   '- [...]
|
|-- Clients
|   |- views
|   |  '- [...]
|   |
|   |- ControllerManage.php
|   |- ControllerNewletter.php
|   '- [...]
|
'-- Orders
    |- views
    |  '- [...]
    |
    |- ControllerManage.php
    '- [...]
```

### Model, View, Controller
Dachi follows the MVC pattern. This pattern enforces a strict seperation between the data, the logic and the
presentation. On top of the MVC pattern, Dachi implements two additional services: Repositories and Helpers.

#### Model
A model represents the data structure and provides simple, named functions for accessing the data. A model should only
represent the data and should not typically perform any additional logic. Additional logic is likely more appropriate
in a Controller, Helper or Repository.
```php
$test = new ModelTest();
$test->setMessage("Hello There!");
Database::persist($test);
Database::flush();
```

#### View
A view is typically the HTML markup that the is rendered to the user, using a templating language to represent data.
The templating language will then be triggered from the Controller to render the final page.
```html
<strong>{{ test.message }}</strong>
```

#### Controller
A controller sits between the Model, the View and the Dachi Framework and acts as an intermediary. The controller is
responsable for the core logic. Controllers contain the routing rules and are responsable for handling incoming
requests.
```php
/**
 * @route-url /test
 */
public function view_test() {
	Template::display("@Test/view.test");
}
```

#### Repository
A repository acts as an extention to a model. Providing small library-like pieces of code to enhance the model. Good
use cases would include functions such as `getLogEntriesByDateRange` and `removeAllPendingEntries`.
```php
Database::getRepository("Test:ModelTest")->removeAllTestEntries();
```

#### Helper
A helper acts as a global library to aid with features not deemed an integeral part of the Dachi Core. Currently the
only available helpers are `Files` and `EMail`. Due to the module nature of Dachi, this can be expanded both by us,
and any developer using the framework (this is infact advised!).
```php
use Dachi\Helpers\Files;
Files::delete("test_file.txt");
```

### Application Flow
"If you can't draw a picture of it, it's too complex."
![Application Flow Diagram](../img/application_flow.png)
```php
/**
 * 1. Accept web request and parse the requested URL
 *
 * 2. Route the web request
 *    a. Cheak the routing cache for the correct handler
 *    b. Load module and controller
 *
 * 3. Execute Controller
 *    a. Load model
 *    b. Perform action, aided by the Framework
 *    c. Render template
 *
 * 4. Send rendered content back to the user
 *
 * 5. Profit.
 */
```

### Directory Structure
Due to the large amount of functionality Dachi provides we require quite a varied selection of files to be placed in
the correct positions. We provide a command-line tool to automate creation of a new project.

#### Before Initialization
**/assets/** Contains all projects assets. Contains subfolders for javascript, lcss, static assets and uploads (if S3
isn't being used)

**/config/** Contains all dachi configuration. Contains subfolders for each environment (local, development, production)

**/src/** Contains all the projects source code. This is where your controllers, models and views are stored. 

**/tests/** Contains all the projects test code. By default this will only contain a dummy test.

**/views/** Contains all the projects global templates.

**.bowerrc** Instructs bower to use our private repositories.

**.gitignore** Instructs git to ignore certain files.

**.htaccess** Instructs apache to route web requests through Dachi.

**cli-config.php** Doctrine uses this file to initalize the command line interface.

**Gruntfile.js** Instructs grunt to use the built-in Dachi grunt pipeline.

**package.json** Contains a list of required packages for Grunt to function.

#### After Initialization
**bower_components** Contains all required bower components for front-end code

**build** Contains the latest built version of all assets

**cache** Contains a cached version of the request table, the configuration objects, database proxies and precompiled
twig templates.

**vendor** Contains all required composer components for back-end code