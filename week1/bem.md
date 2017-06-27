## How to write BEM with CSS
### Why would you use BEM?    
In larger projects it could be difficult to keep track of all the css classes and what they relate to.  
Without this kind of system it becomes harder for other people to read your code and for you to change it if necessary.    
BEM - Block, Element, Modifier - is a methodology for naming your css classes that will make your code more explicit and descriptive.  
### How do you use it?    
First, let's divide it into 3:    
* Block: A parent category with meaning on its own. Ex: navbar, header, form  
   __Syntax: .navbar{}__  
   (Our house)      
* Element: A part of a block, with no meaning on itself. Ex: menu item, list item  
  __Syntax: .navbar__menu-item{}__  
  (The building block of our house)      
* Modifier: A way to target the element or the block in order to change its style/behaviour. Ex: orange, big;        
  __Syntax: .navbar--orange__  
  (Half of our house is red)      
