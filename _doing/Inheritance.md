Inheritance

Usually there's two way to inherit in OOP languages, since there's no interface, only Implementation inheritance is available in Javascript.

protype chaining

Each constructor of a type has a prototype property that point to a prototype object, and each instance of the type has a property named  _ _ proto_ _ that point to the same prototype object. the prototype object can be instance of another type, so it can reach another type's prototype object through _ _ proto _ _; that's how a prototype chaining works. PS: the default prototype's constructor property points to the constructor itself.

- Use _instanceof_ can check whether is an instance is created with a constructor [ref](https://yeecai.github.io/blog/variable,-scope-and-memory/):

  ```javascript
  if(target.__proto__ === origin.prototype) {
  			return true
  		}
  		target = target.__proto__ 
  ```

- the problem of prototype chaining is that everything on prototype is static (shared with all instances), so that property better place on constructor; so you can't pass arguments to the super() function;

+constructor stealing:

Supertype.call(this) in Subtype(), use apply or call the parent's contructor function in child's contructor.

pro: copied all the property's in parent's constructor;

con: missed the methods on the parent's prototype object.

=> combination inheritance:

combine the both above to get everything in  as well everything on prototype:

```javascript
subtype.prototype = new SuperType() // prototype chaining
function Subtype(name, age) {
    SuperType.call(this, name) // stealing constructor
}
```



Prototypal inheritance: 

create a new object by shallowly copy another object, without use known constructor.

```javascript
function prototypal(origin) {
	function F(){};
	F.prototype = origin;
	return new F();
}

// same with Object.create() without the second argument
```

let's handroll an Object.create()

``` javascript
function create(origin, properties) {
    function F() {};
    F.prototype = origin;
    let o = new F();
    if (typeof properties === 'object') {
        Object.defineProperties(o, properties)
    }
    return o;
}
```

=>Parasitic inheritance(not good with code reuse)

Use Object.create with additional methods:

```javascript
function parasitic(origin) {
    let o = create(origin)
    o.extraFn = () {};
    return o;
}
```

Parasitic combination inheritance:

 problem of combination inheritance is it will call the parent's constructor twice: 

So we can get the protoype of the parent directly to skip calling SuperType() once

``` javascript
fucntion parasiticCombin(SubType, SuperType) {
    let prototype = create(SuperType.prototye);
    prototype.constructor = SubType;
    SubType.prototype = prototype;
}

function Subtype(name, age) {
    SuperType.call(this, name) // stealing constructor
}
```

combination inheritance means create a new instance(copy) of the parent as it's own prototype to inherit everything on it while calling the parent's constructor to copy it's own property

parasitic inheritance means use prototype to refer(parasite) an existed instance while add extra method;

so Parasitic combination inheritance is to refer(parasite) to the parent's prototype instead of create a new instance of the parent;

the major difference is whether create an new instance as subType's prototype

Class:

- no hoisting compared to function

- when use class expression, the class identifier not accessible outside the class expression

  