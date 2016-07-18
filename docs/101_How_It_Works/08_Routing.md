Dachi handles URL routing using the internal `Router` class. This class is responsable for parsing the incoming request
and comparing it to the existing cache of valid URLs. Once a valid URL is found, the Router will load the appropriate
Module and Controller, and then execute the requested function as defined with `@route-url` tags.

All routing is handled via tags in comments on functions in your Controllers. Routing is cached to a file and this file
must be generated and then regenerated if any routing changes occur. This is generated using the command line tool.

It is currently not possible for a function have multiple `@route-url` or `@route-render` tags. The same functionality
can be achieved by creating a second function with your additional tags, and just calling the other function.

### `@route-url`
This tag defines what URL your function can be accessed via. This example shows a function that can be accessed via the
`/sample` endpoint.
```php
/**
 * @route-url /sample
 */
public function view_sample() { }
```

Wildcard URLs are supported and allow you to have dynamic parts of your URL. This example shows a function that can be
access via the `/sample/:id/view` endpoint, where `:id` is any number. i.e: `/sample/3/view/`, `/sample/1337/view`. If
the URL argument (`:id`) doesn't match the pattern provided as the second argument to `Request::getUri`, an
`InvalidRequestURIException` will be thrown. You can nest wildcard URLs (i.e. `/sample/:id/view/:other_id`) but you
cannot have two functions bound to the same wildcard URL (even with different wildcard names).
```php
/**
 * @route-url /sample/:id/view
 */
public function view_sample_sub() {
	$id = Request::getUri("id", "[0-9]+");
}
```

If a valid route cannot be found, a `ValidRouteNotFoundException` will be thrown.

### `@route-render`
This tag is used to define an additional URL to render before rendering the current URL. This additional URL will only
be rendered if the page is directly requested, and not requested via AJAX. This allows you to have a page such as
`@route-url /sample`, which displays a template with a `<radon-block>`. Then you can have a second page such as
`@route-url /sample/:id`, which only renders a specific entry into the `<radon-block>`. Without the `@route-render`, the
Router has no way of knowing that `/sample/:id` should be inside `/sample`.
```php
/**
 * @route-url /sample/:id
 * @route-render /sample
 */
```

Wildcard URLs can be used with `@route-render`, however you must ensure that the wildcard matches perfectly. For
instance: `/sample` and `/sample/:id` is fine. `/other/:id/view` and `/other/:id/view/:thing` is fine. `/bad/:id` and
`/superbad/:id` is not fine, as this would result in /bad/:id being called with an incorrect ID, which may trigger
errors and will give unexpected results.
```php
/**
 * @route-url /clients/:id/documents/:document
 * @route-render /clients/:id
 */