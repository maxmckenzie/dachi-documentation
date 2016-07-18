Dachi requires a minimum PHP version of 5.5 due to some of its dependancies. We strongly advise you do NOT run old
versions of PHP, Dachi may not keep backwards compatability for PHP versions in future versions. This is the only core
requirement for Dachi to function in the most basic sense.

Typically to use all of the features available to you with Dachi, you would require:

#### Core Requirements
**node.js**: Required for bower and grunt to function.
```none
https://nodejs.org/download/
```

**Composer**: Handles back-end package management.
```none
https://getcomposer.org/doc/00-intro.md
```

**Bower**: Handles front-end package management. Bower is installed using the `npm` tool.
```none
npm install -g bower
```

**Grunt**: Handles automation of tasks and asset management. Grunt is installed using the `npm` tool.
```none
npm install -g grunt
```

#### Additional Requirements
**A Database**: Doctrine DBAL supports many different database engines. We typically use MySQL internally.

**AWS DynamoDB**: For cross-server session support we use DyanmoDB from AWS. This isn't required in a single server
setup.

**AWS S3**: For storage of files using the 'Files' helper we use S3 from AWS. Local file storage can be uses, but only
in a single server setup.

**Mandrill**: For email sending using the 'EMail' helper we use Mandrill's API. Local email sending is currently not
supported.