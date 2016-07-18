Presenting content to a user requires, in most situations, the combination of both logic, and data. It is never a good
idea to weave this presentation in amoungst other code. Views allow us to store this presentation in a seperate file and
compile the finished result at the last moment. There are multiple methods of implimenting Views, ranging from a simple
file include to a full blown templating engines. For Dachi, we selected the Twig templating engine. This choice was
heavily influence by the ability to render Twig templates on the front-end using JavaScript. Twig performs well and
has a strong following.

Dachi Templates are always stored in the `views` subfolder, inside the Module folder. The filename must end with
`.twig`, however, when refering to templates from controllers you should omit the `.twig`.

### Twig
Dachi handles all of the Twig setup and initialization, as a developer the only things you need to be aware of are:

For front-end rendering of Twig templates using Radon UI (this is an optional feature), a JavaScript version of Twig
will be used for rendering. This has certain implications: if you need to extend twig, you will need to do it on both
sides; certain features will behave differently (dates and times perform very strangely in some cases); when rendering
over Radon UI, ALL set request data will be sent to the client via AJAX, you should be aware that this can cause large
security issues if you define more than is necessary.
```html
// You avoid most problems with dates and times using our "_short" filters.
// (this format is the expected format for HTML5 form elements)

{{ item.created|date_short }}  =>  2015-05-21
{{ item.created|time_short }}  =>  17:43
```

Twig supports namespacing for templating. Dachi supports this out-of-the-box and automatically generates namespaces for
each module. This allows you to use shorthand paths such as "@Module/template".

When following Twig documentation, alot of things may be slightly different due to the way we handle our implementation.
This should not typically interfere with day-to-day development.

### Show Me The View
A view is a simply a combination of HTML and the Twig templating language. This allows us to define data in our
controller and inject it into our template. Here we place a page title, defined in our controller, into our header tag.
```html
<!-- PHP: Request::setData("page_title", "Our Homepage"); -->
<h1 class="page-header">
	{{ page_title }}
</h1>
```
A more advanced, real-world, usage would be looping through a list of data returned from a database. First we'd need to 
select our data from our database using the `Database::getRepository(x)->findAll()` and loop through it to create our
data to render.
```
$entries = array();
foreach(Database::getRepository("Sample:ModelTest")->findAll() as $entry) {
	$entries[] = array("id" => $entry->getId(), "message" => $entry->getMessage);
}
Request::setData("entries", $entries);
Template::display("@Sample/test");
```
Now we can use this from our template, along with the page header code above, to create a template that loops through
the list and outputs every entry.
```
<h1 class="page-header">
	{{ page_title }}
</h1>
{% for entry in entries %}
	<div class="entry">
		<b>{{ entry.id }}:</b> {{ entry.message }}
	</div>
{% endfor %}
```

### Things To Note
Please refer to the [Twig Designer Documentation](http://twig.sensiolabs.org/doc/templates.html) for more specific
details on how Twig works and what features you can use in your templates.