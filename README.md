# Ember CLI HTMLBars

[![Build Status](https://travis-ci.org/rondale-sc/ember-cli-htmlbars.svg?branch=master)](https://travis-ci.org/rondale-sc/ember-cli-htmlbars)

### Handlebars 2.0 Support

Handlebars 2.0 support has been removed. If you are using ember-cli-htmlbars with a 1.9.x project please continue
to use ember-cli-htmlbars@0.6.x.

### Using as a Broccoli Plugin

```javascript
var HtmlbarsCompiler = require('ember-cli-htmlbars');

var templateTree = new HtmlbarsCompiler('app/templates', {
  isHTMLBars: true,

  // provide the templateCompiler that is paired with your Ember version
  templateCompiler: require('./bower_components/ember/ember-template-compiler')
});
```

### Registering a Plugin

```javascript
var SomeTransform = require('./some-path/transform');

module.exports = {
  name: 'my-addon-name',

  included: function() {
    // we have to wrap these in an object so the ember-cli
    // registry doesn't try to call `new` on them (new is actually
    // called within htmlbars when compiling a given template).
    this.app.registry.add('htmlbars-ast-plugin', {
      name: 'some-transform',
      plugin: SomeTransform
    });
  }
};
```
