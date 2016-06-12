###Webpack
packaging node files for browser

```
webpack ./root.js bundle.js
```

root.js is the main.js file that is requiring all of the support files. bundle.js is what is made from that and is what is included in the html

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
