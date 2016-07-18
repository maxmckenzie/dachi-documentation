Helpers are additional features that are out of the scope of the Dachi Core, but are still a valuable tool for
development. Helpers are optional and are only loaded when they are required. We currently use Helpers to provide two
features for developers:

#### Files
The Files Helper handles storage of files uploaded via your application. It currently supports storing the files locally
and storing the files remotely on Amazon's S3.
```php
use Dachi\Helpers\Files;
Files::delete("test_file.txt");
```

#### EMail
The EMail Helper handles sending emails via the Mandrill API. There is no support for sending EMails using any other
method at the moment.
```php
use Dachi\Helpers\EMail;
EMail::send(array(
	// [...]
));
```

### Creating Your Own Helpers
Helpers are just standard PHP classes that extend the `Helper` class. Due to the way classes are loaded, you are unable
to create Helpers in the `Dachi\Helpers\X` namespace. Helpers must be placed in the **/src/** folder and must have a
name prefixed with `Helper` (i.e. HelperSocialAPI.php, HelperSMS.php), and must exist in the root namepsace for your
project.
```php
namespace OurProject;
use Dachi\Core\Helper;

class HelperSMS extends Helper {
	public function send([...]) {
		// [...]
	}
}
```

If you create a Helper and you'd like it to become part of the default set of Helpers just send us a message. Then we
can change the namespace and get it in the Dachi git repository.