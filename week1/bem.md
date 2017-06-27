## How to write BEM with CSS
### Why would you use BEM?    
In larger projects it becomes difficult to keep track of all of the CSS classes and what they are referring to.  
Without a system in place, it becomes harder for other people to read your code, and if becomes harder for you to change it if necessary.    
BEM - *Block, Element, Modifier* - is a methodology for naming your css classes that will make your code more explicit and descriptive.  
### How do you use it?    
First, let's divide it into 3:    
* __Block__: A parent category with meaning on its own. Eg: navbar, header, form  
  __Syntax__: choose a succinct descriptor.  
  *CSS* `.navbar {};`  
  *HTML* <nav class="navbar">
   ( Our house, in the middle of our street )      
* __Element__: A part of a block, with no semantic meaning by itself. Eg: menu item, list item  
  __Syntax__: use two underscores.  
  *CSS* `.navbar__menuitem {};`  
  *HTML* <nav class="navbar__menuitem">
   ( The building blocks )      
* __Modifier__: A way to target the element or the block in order to change its style/behaviour. Eg: orange, big       
  __Syntax__: use two hyphens.  
  *CSS* `.navbar--orange {};`  
  *HTML* `<nav class="navbar--orange">`  
  ( One of the bricks, painted red )
