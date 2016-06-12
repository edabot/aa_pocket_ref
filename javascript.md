###Webpack
packaging node files for browser

```
webpack ./root.js bundle.js
```

root.js is the main.js file that is requiring all of the support files. bundle.js is what is made from that and is what is included in the html

Or we can set up a wedbpack.config.js file with this
```
module.exports = {
    entry: "./entry.js",
    output: {
        path: __dirname,
        filename: "bundle.js"
    },
    module: {
        loaders: [
            { test: /\.css$/, loader: "style!css" }
        ]
    }
};
```
entry is the root JS file, filename is the output name. then we can just use
```
webpack
```
to compile. If we want a progress bar, we do this:
```
webpack --progress --colors
```
If we want it to recompile with every saved change, we do this
```
webpack --progress --colors --watch
```

###Prototypal Inheritance

```
function Animal (name) {
  this.name = name;
};

Animal.prototype.sayHello = function () {
  console.log("Hello, my name is " + this.name);
};

function Dog (name, coatColor) {
  // call super-constructor function on **the current `Dog` instance**.
  Animal.call(this, name);

  // `Dog`-specific initialization
  this.coatColor = coatColor;
}

function Surrogate () {};
Surrogate.prototype = Animal.prototype;
Dog.prototype = new Surrogate();

Dog.prototype.bark = function () {
  console.log("Bark!");
};
```
