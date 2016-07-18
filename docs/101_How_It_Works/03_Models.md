Most applications require a method of storing information in a database. There are countless methods and technologies
for storing data. For Dachi, we decided the best choice would be to integrate a database engine that removes all the
hassle behind these different methods and has heavy usage of database models. A database model is a strictly defined
logical structure of the database which determines how data can be stored, organized and manipulated. This is best
defined in a format that is not dependant on the resulting choice of database engine and other technologies. Doctrine
fulfills our needs perfectly, while providing a wealth of other features.

Dachi Models are always stored in the Module folder, and the model name must be prefixed with 'Model' (i.e.
ModelClient, ModelSupplier).

### Doctrine
Doctrine can use multiple methods of defining a database model, however for Dachi we have settled upon using the PHP
format, as this allows us to further expand models with required logic. Dachi handles all of the Doctine setup and
initialization, as a developer the only things you need to be aware of are:

Correct database credentials must always be provided in the relevant configuration files. If you working with an
existing project, you will likely need to request a copy of the latest database schema. A database schema can be
generated from the model files and typically updates can be done using the command line tool. However on initial setup,
you'll likely need the associated data to get things running.

Doctrine provides a command line interface for interacting with the database, it is wise to become familiar with it.

Doctrine supports namespacing for templating. Dachi supports this out-of-the-box and automatically generates namespaces
for each module. This allows you to use shorthand paths such as "Module/template".

When following Doctrine documentation, alot of things may be slightly different due to the way we handle our
implementation. This should not typically interfere with day-to-day development.

### Show Me The Model
As with all Dachi module code, you first need to declare your namepsace and declare that you intend to use the Dachi
database engine.
```php
namespace OurProject\OurModule;
use Dachi\Database;
```

This is then followed by a comment, which includes the `@Entity` tag. This informs Doctrine that the following class is
a database entity. Alongside the entity tag, we also have the `@Table` tag. This informs Doctrine that our table should
be called "examples". Typically we use plural names in table names where applicable. We favour `clients_documents` over
`client_document`.
```php
/**
 * @Entity
 * @Table(name="examples")
 */
```

Next we open a class that extends Model, with a name prefixed by "Model" that will be used to refer to your entity
throughout the codebase, this class will then contain definitions for the columns and provide functions for getting and
setting the values of the columns.
```
class ModelExample extends Model {
```

#### Defining Identifing Column
For an entity to be useful, typically we have to give it an identifing column. There are cases where you would not
require an identifing column but in most cases you should include one. This is done by defining the `id` column, with
the appropriate tags and the defining a single function for retrieving the ID. `@Id` tells Doctrine that this column is
used for identifing the entity. `@GeneratedValue` tells Doctrine to automatically increase the id for each entity. The
`@Column` tag declares the column type, which for an ID is "integer".

```php
	/**
	 * @Id @Column(type="integer") @GeneratedValue
	 */
	protected $id;

	public function getId() {
		return $this->id;
	}
```

#### Defining Columns
Once we have a model class prepared, we can add our column definitions and functions for getting and setting data. First
we open with another comment, this comment has a `@Column` tag which defines the type of data stored. There are many
types of data, and some of them have additional options (see doctrine docs). After the comment, we declare the column
name (in this case 'message').
```php
	/**
 	* @Column(type="string")
 	*/
	protected $message;
```

This is sufficient to get the column into the database, however it will be empty and inaccessable until we provide
functions to access it. These are fairly simple functions. The getter doesn't take any arguments and just returns the
column value. The setter takes a single argument and the column is set to it. There is no requirement on the naming of
functions, however it is advised they fit the getX/setX format. These functions could have additional code attached to
them, however care should be taken as this may be more appropriate in the controller or repository.
```php
	public function getMessage() {
		return $this->message;
	}

	public function setMessage($message) {
		$this->message = $message;
	}
```

### Things To Note
Typically we place all the column definitions at the top of the class, and all the get/set functions below them. This
makes things a little easier for somebody new jumping into the code. Please refer to the
[Doctrine Mapping Documentation](https://doctrine-orm.readthedocs.org/en/latest/reference/basic-mapping.html) for more
specific details and a full list of available data types.
```
}
```