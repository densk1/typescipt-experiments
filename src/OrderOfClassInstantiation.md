# Order of Class Instantiation

A typescript class is compiled to a javascript function. The order of the function is as follows:
1. Constructor field shorthand
2. Property initializers
3. Constructor body.

```ts
class Parent {
  private one: string;

  constructor(one: string = "p1", private two: string = "p2") {
    this.one = one;
  }

  pArrowFunction = () => {};
  pNormalFunction() {}
}
```

Compiles to:

```js
// ES5
var Parent = /** @class */ (function () {
    function Parent(one, two) {
        if (one === void 0) { one = "p1"; }
        if (two === void 0) { two = "p2"; }
        this.two = two;
        this.pArrowFunction = function () { };
        this.one = one;
    }
    Parent.prototype.pNormalFunction = function () { };
    return Parent;
}());

// ES2016
class Parent {
    constructor(one = "p1", two = "p2") {
        this.two = two;
        this.pArrowFunction = () => { };
        this.one = one;
    }
    pNormalFunction() { }
}
```
