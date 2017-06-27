Mobile First vs. Responsive
“Responsive” is used to describe the possibility of websites adapting to various output devices.
The layout, fonts, image sizes etc. change and or scale according to the size of the browser. This principle enables good readability and usability on desktops, tablets and smartphones.

The term “mobile first”, being very descriptive, already gives us a good hint of what to expect: primarily focusing on development for mobile devices. The common responsive approach works with the desktop browser as the basis, and offers alternative, scaled down versions for other device/browser sizes. That works via CSS media queries, which check the browser size and adjust the layout and styling according to that.

Conceptually starting with displaying a website on mobile devices, rather than on a desktop, leads to a quite different approach on how to deal with content. Mobile first means content first.

Both approaches prioritise one set of users over the other
To avoid that a developer could load one of two styles at the load time depending upon CSS media query or allow a user to choose between styles

Responsive guidelines

1. Do not rely on a particular viewport width (A meta viewport tag gives the browser instructions on how to control the page's dimensions and scaling)
In particular, : avoid fixed width elements, unless they are small

2. Use CSS media queries to apply different styling for different environments, such as small or big screens, mobile or desktop devices. *You can use meta-viewport tags to emulate a different viewport, but it may cause accessibility problems

# use of minimum-scale and maximum-scale which affect the users ability to zoom

Mobile guidelines

1. Mobile first implies prioritising the presentation of the content. Rule #1: avoid clutter
2. The screen size is not the only limitation of the mobile environment. For example, a lot of JS display libraries will slow down the site even if they are not visible
