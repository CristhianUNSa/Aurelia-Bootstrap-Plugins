# Aurelia-Bootstrap-Tagsinput

### Introduction
An Aurelia Custom Element for the 3rd party addon [Bootstrap Tags Input](https://bootstrap-tagsinput.github.io/bootstrap-tagsinput/examples/)

### Usage
A quick example of the code in action. Note that the value is available under the `model.bind`.
```html
<aba-tags-input element.bind="tag" model.bind="post.categories"></aba-tags-input>
```

### Available Attributes/Options
Every single options that are part of `Bootstrap Tags Input` are available as bindable or as regular attributes. For the complete list, please visit the official site [Bootstrap Tags Input - Options](http://bootstrap-tagsinput.github.io/bootstrap-tagsinput/examples/#options).
There is 2 ways to call options (with a `bind` attribute or as a regular attribute).

Example

_regular attribute (View)_
```html
<aba-tags-input item-value="id" item-text="label"></aba-tags-input>
```

_bind attribute (View + ViewModel)_
```html
<aba-tags-input confirm-keys.bind="tagConfirmKeys"></aba-tags-input>
```
```javascript
export class Example {
    tagConfirmKeys = [13, 44];
}
```

### Available Methods/Functions
Again every single methods which comes with `Bootstrap Tags Input` are available. For the complete list, please visit the official site [Bootstrap Tags Input - Functions](http://bootstrap-tagsinput.github.io/bootstrap-tagsinput/examples/#methods). 

To have access to the methods/functions, you will need to expose the element itself through `element.bind` to expose the methods _(also note that doing so will also give you access to `events`, `options` and `methods`)_. 

Example

_View (exposing the element)_
```html
<aba-tags-input element.bind="tag" model.bind="post.categories"></aba-tags-input>
```

_ViewModel (calling the method)_
```javascript
export class Example {
  tagChanged() {
    this.tag.methods.add('tag1');
  }
}
```

### Available Events
Every events of `Bootstrap Tags Input` are, as no surprises, available as well. For the complete list, please visit the official site [Bootstrap Tags Input - Events](http://bootstrap-tagsinput.github.io/bootstrap-tagsinput/examples/#events). 

To have access to the `events`, you will need to expose the element itself through `element.bind` to expose the methods _(also note that doing so will also give you access to `events`, `options` and `methods`)_. 

**Note**
The events are called with the syntax of `onEvent` which differs from the original syntax. Example, for the `beforeItemAdd`, we would use the `onBeforeItemAdd` event.

Example

_View (exposing the element)_
```html
<aba-tags-input element.bind="tag" model.bind="post.categories"></aba-tags-input>
```

_ViewModel (calling the onEvent trigger)_
```javascript
export class Example {
  tagChanged() {
    this.tag.events.onBeforeItemAdd = (e) => console.log('onBeforeItemAdd');
    this.tag.events.onBeforeItemRemove = (e) => console.log('onBeforeItemRemove');
    this.tag.events.onItemAdded = (e) => console.log('onItemAdded');
    this.tag.events.onItemAddedOnInit = (e) => console.log('onItemAddedOnInit');
    this.tag.events.onItemRemoved = (e) => console.log('onItemRemoved');
  }
}
```

## Installation
You can run the examples or build your own by doing the following.

### Aurelia-CLI / Webpack
```bash
npm install --save aurelia-bootstrap-tagsinput
```
#### Aurelia-CLI
For `CLI` you will need to add (`aurelia-bootstrap-tagsinput`) to your `aurelia.json` file. The exported class is `aba-tags-input`.
```javascript
{
  "name": "aba-tags-input",
  "path": "../node_modules/aurelia-bootstrap-tagsinput/dist/amd",
  "main": "index",
  "resources": ["**/*.{css,html}"]
}
```

#### Aurelia (main)
Make the plugin available globally in your `main.js` file. Please note the exported class is `aba-tags-input` (`aba` stands for `Aurelia-Bootstrap-Addon`)

```javascript
export function configure(aurelia) {
  aurelia.use
    .standardConfiguration()
    .developmentLogging()
    .plugin('aba-tags-input')
    .feature('resources');

  aurelia.start().then(() => aurelia.setRoot());
}
```