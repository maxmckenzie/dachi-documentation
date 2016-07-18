Repositories act as a middle ground between Models and Controllers. They allow you to specify a set of functions that
can be used to manipulate the data. This is typically used for building functions that can select specific data based
upon a specific criteria. Repository functions allow for further removal from the data structure, for example you could
create a function called `getAvailableVehicles`, this would then be clear and obvious to a developer that this function
returns a list of vehicles that are available. This remains true if you then decide to completely change the data
structure behind Vehicles, while retaining the same interface.

Dachi Repositories are stored in the Module folder and always have a name prefixed with 'Repository' (i.e.
RepositoryClient.php, RepositoryVehicle.php). Repositories are a concept introduced by Doctrine and are tightly
integrated with Doctrine.

### Tell Your Model
Before you can use a repository, you will need to update your Model file to contain the repository class. Doctrine will
then always return your repository, instead of the default, when `Database::getRepository` is called. This is as simple
as updating your `@Entity` tag to have the `repositoryClass` argument.
```php
/**
 * @Entity(repositoryClass="RepositorySample")
 * @Table(name="[...]")
 */
class ModelX extends Model {
```

### Show Me The Repository
As with all Dachi module code, you first need to declare your namepsace and declare any Dachi features you may require,
and in the case of Repositories, we also need to declare that we are using the Doctrine EntityRepository feature.
```php
namespace OurProject\OurModule;
use Dachi\Database;
use Doctrine\ORM\EntityRepository;
```

Next we open a class, with a name prefixed by "Repository" that will be used to refer to your repository throughout the
codebase, this class will then contain function definitions for each feature you want to provide.
```
class RepositorySample extends EntityRepository {
```

#### Executing our logic
Exactly the same as you do with a Controller, we create a standard public function, there is no restriction on the name
of the function although it's advised to use descriptive names. Be aware that PHP places some restrictions on certain
function names.
```php
	public function getAvailableVehicles() {
```
Anything inside our function will now be executed whenever a this function is called from a controller. We are now free
to use any of the functionality provided by Dachi and PHP. Here we retrieve a list of available vehicles.
```php
		$vehicles = $this->findBy(array(
			"available" => true
		));
		return $vehicles;
```
Usually a Repository function would have more complex logic, and could accept arguments to retreive data based upon. A
Repository can have as many functions as required.
```php
	}
```

### Things To Note
Repository can seem a strange concept at first glance but when used to their full potential they can be a powerful
asset. It is strongly advised to become familiar with them as this will allow easier access to your data across Modules
and provide a consistant data access API.
```
}
```