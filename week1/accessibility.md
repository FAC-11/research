What is a "Modal"?
A "Modal" is a dialog box, when opened it stops the user from interacting with the rest of the page and it restricts keyboard focus to the dialog box.

What makes an accessible "Modal"?

An accessible "Modal" allows the following keyboard interactions:
Tab:
Moves focus to the next focusable element inside the dialog.
If focus is on the last element, moves focus to the first focusable element inside the dialog.
Shift + Tab:
Moves focus to the previous focusable element inside the dialog.
If focus is on the first element, moves focus to the last focusable element inside the dialog.
Escape: Closes the dialog.

HTML Attributes for accessible modals:

* The modal dialog box has a role attribute of dialog.
* The aria-labelledby property refers to the visible dialog title.
*  The label is specified with aria-label.
