


# Accessibilty in Navigation and Modals

## Nav Bar Accessibility
_Why do we need accessibile nav bars?_
* For user agents without CSS and JS
* For users with sight problems
* For users with difficulty seeing low contrast
* To enable users without a mouse to access the navigation options with only key presses

_What do we need to do to make our nav bars accessible?_
* Use defined accessibility features such as tabindex
* Name the nav bar options appropriately
* Make sure the colour contrast is sufficient. Check your colour contrast ration [here](http://webaim.org/resources/contrastchecker/)
* For modern menus eg. burger the user should have the ability to select option without a click press

## Modal Accessibility
 _What is a "Modal"?_

A "Modal" is a dialog box, when opened it stops the user from interacting with the rest of the page and it restricts keyboard focus to the dialog box.

_What makes an accessible "Modal"?_

An accessible "Modal" allows the following keyboard interactions:
Tab:
Moves focus to the next focusable element inside the dialog.
If focus is on the last element, moves focus to the first focusable element inside the dialog.  
Shift + Tab:
Moves focus to the previous focusable element inside the dialog.
If focus is on the first element, moves focus to the last focusable element inside the dialog.
Escape: Closes the dialog.

_HTML Attributes for accessible modals:_

* The modal dialog box has a role attribute of dialog.
* The aria-labelledby property refers to the visible dialog title.
*  The label is specified with aria-label.
