Now you have your data stored, and your presentation prepared. We still need a way of defining how the user will access
this, and the logic associated with it. This is where controllers come in to play. Controllers allow us to simply
define the actions of a application. Dachi doesn't provide any controllers other than a small controller for Radon UI to
function. Controllers are written by you developers!

Controllers are stored in your Module folder and always have a filename prefixed with 'Controller' (i.e.
ControllerManage.php, ControllerUpdate.php).

### Show Me The Controller
As with all Dachi module code, you first need to declare your namepsace and declare any Dachi features you may require:
```php
namespace OurProject\OurModule;
use Dachi\Request;
```

Next we open a class that extends Controller, with a name prefixed by "Controller" that will be used to refer to your
controller throughout the codebase, this class will then contain function definitions for each URL you wish to handle
and can also contain private functions as any other PHP class can.
```
class ControllerView extends Controller {
```

#### Defining a URL route
For routing, Dachi requires a comment to be placed before the function. This comment should contain a `@route-url` tag
describing the URL that can be used to access it. Other tags are available, and it is possible to use wildcard urls (see
the Routing documentation).
```php
	/**
	 * @route-url /view
	 */
```

#### Executing our logic
Now we create a standard public function, there is no restriction on the name of the function although it's advised to
use descriptive names. Be aware that PHP places some restrictions on certain function names.
```php
	public function page_view() {
```
Anything inside our function will now be executed whenever a user hits the `/view` endpoint. We are now free to use any
of the functionality provided by Dachi and PHP. Here we retrieve the latest news entry and display it to our user.
```php
		$entry = Database::getRepository("Sample:ModelNews")->getLatest();
		Request::setData("latest_news", array(
			"time" => $entry->getTime(),
			"message" => $entry->getMessage()
		));
		Template::display("@Sample/news");
```
A Controller can have as many functions as required and all routes are pre-calculated and cached providing little
overhead. It is advised to split Controllers if they are becoming too large, as there is also no limit to the amount of
Controllers a Module may provide.
```php
	}
```

### Things To Note
Controllers can become fairly complex as more and more logic is added. It is advised you try to make all your code as
clear as possible. Avoid short and undescriptive variable and function names, avoid complex one-line peices of code and
try to comment un-obvious code. Make the next developers life easier, and hope the previous developer did the same!
```
}
```