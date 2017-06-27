## How to write BEM with CSS
### Why would you use BEM?    
In larger projects it becomes difficult to keep track of all of the CSS classes and what they are referring to.  
Without a system in place, it becomes harder for other people to read your code, and if becomes harder for you to change it if necessary.    
BEM - Block, Element, Modifier - is a methodology for naming your css classes that will make your code more explicit and descriptive.  
### How do you use it?    
First, let's divide it into 3:    
* Block: A parent category with meaning on its own. Eg: navbar, header, form  
   __Syntax: .navbar {}__  
   ( Our house, in the middle of our street )      
* Element: A part of a block, with no semantic meaning by itself. Eg: menu item, list item  
  __Syntax: `.navbar__menu-item {}`__  
   ( The building block of our house )      
* Modifier: A way to target the element or the block in order to change its style/behaviour. Ex: orange, big;        
  __Syntax: .navbar--orange{}__  
  ( One of the bricks in our house is painted red )
