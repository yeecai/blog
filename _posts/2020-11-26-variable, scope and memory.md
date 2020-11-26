variable, scope and memory



- the difference of let name1 = 'string' , let name2 = new String('string') is that name1 doesn't have any property;

- arguments passed by coping the value;

- typeof: string, number, boolean, undefined, function, object;

- [instanceof](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/instanceof) return false for primitive value;

  ```javascript
  // let's handroll a instanceof
  const myInstanceof = (target, origin) => {
      // typeof null === 'object'
      if(typeof target !== 'object' || target === null) return false
  	while(target) {
  		if(target.__proto__ === origin.prototype) {
  			return true
  		}
  		target = target.__proto__ 				
  	}
  	return false
  }
  ```

  ``` javascript
  Object.create(null) instanceof Object // false
  ```

var, let , const 

- "Duplicate `var` declarations are simply ignored; duplicate `let` declarations throw a `SyntaxError`."

- *const* only forbid reassignment of reference value, the properties' value is not protected;
- **Object.freeze**() is an option to protect the properties; However, **Object**. **freeze**() is not **recursive**. You can still modify nested **object** properties

#### memory

- v8 use hidden class(share the same class) for two object instance, but if one altered by creating new property or delete property, the class for each instance is not longer shared, so better put property in constructor;

- const and let has better performance regarding this since block scope terminates sooner than the function scope, so the referenced space could be collected sooner;

- referencing-counting has a major issue as circular reference, and if the circular operation happens frequently, memory leaks;

- mark&sweep mark the unreferred object and sweep then;

- BOM and DOM implemented as COM in C++, so might cause circular reference:

  ```javascript
  let element = document.getElementById("some_element");
  let myObject = new Object();
  myObject.element = element;
  element.someObject = myObject;
  ```

  memory leaks:

  	- circular reference with DOM;
  	- closure with extremely large object;
  	- global reference;
  	- setIntervel timers caused closure

  suggestion:

  	- use object pool;
  	- avoid creating object in frequently called function: because GC happen by the rate of object churn(creating lots object then destruct the reference)