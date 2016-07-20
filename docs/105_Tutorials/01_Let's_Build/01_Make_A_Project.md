Make sure to check the [requirements section](/Requirements) of the docs before trying to setup a new Dachi project.

As mentioned there be sure to have [node.js](https://nodejs.org/download) and [composer](https://getcomposer.org/doc/00-intro.md#globally) installed. In case you're having troubles installing composer on mac follow along this [youtube-tutorial](https://www.youtube.com/watch?v=BnIZVHmROkk).

### composer.json

Create a file `composer.json` with:

```javascript
{
  "minimum-stability": "dev",
  "prefer-stable": true,
  "repositories": [
    {"type": "composer", "url": "http://packages.services.ld-cdn.com/"}
  ],
  "autoload": {
    "psr-4": {
      "SampleClient\\SampleProject\\": "src/"
    }
  },
  "require": { "ld-packages/dachi": "^2.0" }
}
```
Replace `SampleClient\\SampleProject\\` with your a client/organization-name and project-name.

Run `composer install`.

### Install Dachi

Once everything is downloaded, you are ready to create your Dachi project. (If you are using windows, you should replace `/` with `\` for your path.)

Run `vendor/bin/dachi dachi:create`
