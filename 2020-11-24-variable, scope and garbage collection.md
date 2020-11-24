variable, scope and garbage collection



- the difference of let name1 = 'string' , let name2 = new String('string') is that name1 doesn't have any property;

- arguments passed by coping the value;

- typeof: string, number, boolean, undefined, function, object;

- [instanceof](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/instanceof)

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

  