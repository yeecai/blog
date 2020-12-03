nodeType1 === document

It has only item(0) = html 

document.body 

HTML document only got one 

document.implementation.hasFeature

document.domainname same domain name can makes inner iframe object access js object



nodeType2 === Element

nodeType 1 anything else 

element attribute vs object properties:

- 5 element attributes map document properties id align class , 2 types style(getAttribute() return css code text while div.style return object), event handler; onclick attribute return code string while onclick property return the function; so better use just use getAttribute() for value of custom attribute, and use object property
- but adding properties doesn't create attribute
- removeAttribute can be useful when serializing a Dom element
- attributes return all atributes collection

get/set/removeAttribute() 

createElement() creates a new element then can be added to document with appendChild insertBefore

element.getElementsByTagName will return all descendents

nodeType 3 === #text

- nodeValue === the text content
- no children
- parentNode === an element

nodeType8 === '#comment'

- [ ] to read

nodeType 10 11



mutation observers

