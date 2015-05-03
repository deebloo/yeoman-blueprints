# yeoman-blueprints

For a working example look at [generator-angular-blueprints](https://github.com/deebloo/generator-angular-blueprint).

Extends Yeoman's NamedBase to allow to your generator to use overridable templates.
By using these extended methods yeoman will automatically check for locally created template under first ./blueprints and then ./node_modules before falling back to the global templates in the generator.

##### GENERATORS MUST BE UNDER A GENERATORS FOLDER 

```
npm install --save yeoman-blueprints
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
  writing: function writing() {
    // Set destination directory
    this.destDirectory = './client/app/views/' + this.name;
             
    // Set the template values
    var values = {appName: this.config.get('appName') }
           
    // Create the template
    this.copyTpl('controller', 'js', values);
  }
});
```
