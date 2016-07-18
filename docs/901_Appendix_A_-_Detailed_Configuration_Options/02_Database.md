#### `database.json` Database Configuration File
##### `uri` Uniform Resource Identifier *- string*
This should contain the connection URI for your database. This format is described in detail by
[the Doctrine Documentation](http://docs.doctrine-project.org/projects/doctrine-dbal/en/latest/reference/configuration.html#connecting-using-a-url).
We usually use Dachi with mysql which has a format of `mysql://USERNAME:PASSWORD@HOST/DOMAIN?charset=utf8`.
```json
	"uri"      : "mysql://root:root@localhost/our_fancy_project?charset=utf8",
```
##### `cache` Cache *- boolean*
If you are using APC, Xcache, Memcache, Redis or some other form of caching, it is possible to use this cache with our
Database engine. This is provided by Doctrine and you should consult the Doctrine documentation for further information.
Typically this will be left `false`.
```json
	"cache"    : false
```