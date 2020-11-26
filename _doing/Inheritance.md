Inheritance

Usually there's two way to inherit in OOP languages, since there's no interface, only Implementation inheritance is available in Javascript.

Each constructor of a type has a prototype property that point to a prototype object, and each instance of the type has a property named  _ _ proto_ _ that point to the same prototype object. the prototype object can be instance of another type, so it can reach another type's prototype object through _ _ proto _ _; that's how a prototype chaining works. PS: the default prototype's constructor property points to the constructor itself.

- Use instanceof can check whether is an instance is used a constructor [ref](:

  ```javascript
  if(target.__proto__ === origin.prototype) {
  			return true
  		}
  		target = target.__proto__ 
  ```

