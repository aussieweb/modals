# Modals
Simple modal dialogue windows. [View the demo](http://cferdinandi.github.io/modals/).

**In This Documentation**

1. [Getting Started](#getting-started)
2. [Options & Settings](#options-and-settings)
3. [Browser Compatibility](#browser-compatibility)
4. [License](#license)
5. [Changelog](#changelog)
6. [Older Docs](#older-docs)



## Getting Started

### 1. Include Modals on your site.

```html
<link rel="stylesheet" href="css/modals-css.css">
<script src="js/modals.js"></script>
<script src="buoy.js"></script>
```

Modals is [built with Sass](http://sass-lang.com/) for easy customization. If you don't use Sass, that's ok. The `css` folder contains compiled vanilla CSS.

The `_config.scss` and `_mixins.scss` files are the same ones used in [Kraken](http://cferdinandi.github.io/kraken/), so you can drop the `_modals.css` file right into Kraken without making any updates. Or, adjust the variables to suit your own project.

Modals also requires [Buoy](http://cferdinandi.github.io/buoy/), a vanilla JS micro-library that contains simple helper functions used by Modals.

### 2. Add the markup to your HTML.

```html
<a data-modal data-target="#modal" href="#">Modal Toggle</a>

<div class="modal" data-modal-window id="modal">
	<a class="close" data-modal-close>x</a>
	<h3>Modal</h3>
	<p>Modal content</p>
	<button data-modal-close>Close</button>
</div>
```

Be sure to assign each modal a unique ID. Add the `.modal-medium` or `.modal-small` class to change the modal size.

```html
<div class="modal modal-small" data-modal-window id="modal">
	...
</div>
```

Adding a `[data-modal-close]` data attribute to any button or link turns it into a modal dismiss link. The `.modal-close` class adds special styling to close links (if you wanted to use an X for close, for example). Clicking anywhere outside the modal or pressing the escape key will close the modal, too.

### 3. Assign a backup URL.

Always specify a functioning link as a backup for modals.

Modals uses modern JavaScript API's that aren't supported by older browsers, including IE 8 and lower. On modern browsers, Modals will prevent the backup URL from redirecting people away from the current page.

```html
<a class="modal-toggle" data-target="#modal" href="http://backup-url.com">Modal Toggle</a>
```

*If you need to support older browsers, you can still [download the jQuery version of modals on GitHub](https://github.com/cferdinandi/modals/tree/archive-v1).*

### 4. Initialize Modals.

```html
<script>
	modals.init();
</script>
```

In the footer of your page, after the content, initialize Modals. And that's it, you're done. Nice work!



## Options and Settings

Modals includes smart defaults and works right out of the box. But if you want to customize things, it also has a robust API that provides multiple ways for you to adjust the default options and settings.

### Global Settings

You can pass options and callbacks into Modals through the `init()` function:

```javascript
modals.init({
	modalActiveClass: 'active', // Class applied to active modal windows
	modalBGClass: 'modal-bg', // Class applied to the modal background overlay
	offset: 50, // How far from the top of the viewport to offset modal windows in pixels
	callbackBeforeOpen: function () {}, // Functions to run before opening a modal
	callbackAfterOpen: function () {}, // Functions to run after opening a modal
	callbackBeforeClose: function () {}, // Functions to run before closing a modal
	callbackAfterClose: function () {} // Functions to run after closing a modal
});
```

### Use Modals events in your own scripts

You can also call Modals events in your own scripts:

```javascript
// Open a specific modal window
modals.openModal(
	toggle, // Node that launches the modal. ex. document.querySelector('#toggle')
	modalID, // The ID of the modal to launch. ex '#modal'
	options, // Classes and callbacks. Same options as those passed into the init() function.
	event // Optional, if a DOM event was triggered.
);

// Close all modal windows
modals.closeModals(
	options, // Classes and callbacks. Same options as those passed into the init() function.
	event // Optional, if a DOM event was triggered.
);
```

**Example 1**

```javascript
modals.openModal( null, '#modal' );
```

**Example 2**

```javascript
modals.closeModals();
```



## Brower Compatability

Modals works in all modern browsers, and IE 9 and above.

Modals is built with modern JavaScript APIs, and uses progressive enhancement. If the JavaScript file fails to load, or if your site is viewed on older and less capable browsers, all content will be displayed by default.



## License
Modals is licensed under the [MIT License](http://gomakethings.com/mit/).



## Changelog
* v4.0 - February 24, 2014
	* Better public/private method namespacing.
	* Require `init()` call to run.
	* New API exposes additional methods for use in your own scripts.
	* Better documentation.
* v3.4 - February 16, 2014
	* [Added method to stop YouTube, Vimeo, and HTML5 videos from playing when modal is closed.](https://github.com/cferdinandi/modals/issues/5)
* v3.3 - February 10, 2014
	* [Fix `event.preventDefault()` bug that was blocking radio button and checkbox behavior.](https://github.com/cferdinandi/modals/issues/6)
* v3.2 - Feburary 5, 2014
	* [Fixed `setAttribute` bug in FireFox.](https://github.com/cferdinandi/kraken/issues/34)
* v3.1 - February 4, 2014
	* Reverted to `Array.prototype.foreach` loops.
* v3.0 - January 28, 2014
	* Switched to a data attribute for the toggle selector (separates scripts from styles).
	* Added namespacing to IIFE.
	* Updated looping method.
* v2.4 - December 3, 2013
	* Added Sass support.
* v2.3 - August 27, 2013
	* Added missing semicolon to variables.
	* Activated strict mode.
* v2.2 - August 26,2013
	* Converted to an IIFE pattern.
	* Added Buoy vanilla JS micro-library.
* v2.1 - August 18, 2013
	* Added touchevent to close modals.
* v2.0 - August 12, 2013
	* Converted to vanilla JavaScript.
	* Removed jQuery dependency.
* v1.1 - June 7, 2013
	* Switched to MIT license.
* v1.1 - March 27, 2013
	* Touchscreen bug fix.
* v1.0 - March 25, 2013
	* Initial release.



## Older Docs

* [Version 3](http://cferdinandi.github.io/modals/archive/v3/)
* [Version 1](https://github.com/cferdinandi/modals/tree/archive-v1)