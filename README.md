# yeoman-blueprints

Extends Yeoman's NamedBase to allow to your generator to use overridable templates.
By using these extended methods yeoman will automatically check for locally created template under first ./blueprints and then ./node_modules before falling back to the global templates in the generator.

```
npm install -g yeoman-blueprints
```

Methods

### blueprints.copyTpl
```js
// 'controller' - points to generator you want to use in this case located under generators/controller/
// 'js'         - the file type to be created
// values       - an object of values to be made available to template
this.copyTpl('controller', 'js', values);
```

### blueprints.copy
```js
// 'controller' - points to generator you want to use in this case located under generators/controller/
// 'js'         - the file type to be created
this.copyTpl('controller', 'js');
```

Example:
```js
var blueprint = require('yeoman-blueprints');

module.exports = blueprints.NamedBase.extend({
  init: init,
  prompting: prompt,
  writing: writing
});

/**
 * @name init
 */
function init() {
  this.destPath = './client/app/views/';
}

/**
 * @name writing
 */
function writing() {
  var values = {appName: this.config.get('appName') }

  this.copyTpl('controller', 'js', values);
}
```
