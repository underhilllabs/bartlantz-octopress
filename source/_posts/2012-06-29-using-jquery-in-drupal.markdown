---
layout: post
title: "Using jQuery in Drupal"
date: 2012-06-29 18:52
comments: true
categories: [Drupal, JQuery, Webdev]
---
Drupal 7 includes jQuery 1.4.4 by default.  So getting started using jQuery in your module or theme is really simple.  The easiest way to include a javascript file is to include it in a .info file with a line like "scripts[]= myfile.js".

## How to include your js file in a module or theme

### Add this to the .info file

```yaml
scripts[] = js/myjavascript.js
```

this will include the javascript file on every page that includes your module or theme.

### Include it in your Theme's template.php

Themes have more granular control of where javascript file is included in template.php

```php
drupal_add_js(drupal_get_path('theme','kepler6_omega') . 'js/myjavascript.js');
```

### Use drupal_add_js in your module

Include js in yarr.module
```php
function yarr_form_alter(&amp;$form, &amp;$form_state, $form_id) {
  drupal_add_js(drupal_get_path('module,'yarr') . 'js/myjavascript.js');
  ...
}
```

### Use drupal_add_library to add libraries included in Drupal

example add jQueryUI Accordion library
```php
drupal_add_library('system','ui.accordion');
```

While jQuery core is included by default, jQuery UI is not, so you need to include that with drupal_add_library if you need it, as above.)


## Drupal Behaviors
### Drupal behaviors are used instead of $(document).ready();

$(document).ready() is used to wait until the entire DOM is loaded before adding
your javascript functionality to the DOM. 

Drupal adds its own way to add your javascript to the DOM

### Drupal attach behaviors

attach your functionality to the Drupal objects behavior array




```javascript
(function($) {

Drupal.behaviors.yarr = {
  attach: function(context, settings) {
    $('h1 &gt; a').each(function(i) {
      var h1text = $(this).text();
      $(this).text("Yarrr, matey! " + h1text);
    });
    $('h1:not(:has(a))').each(function(i) {
      var h1text = $(this).text();
      $(this).text("Yarr, " + h1text);
    });
  }
};

})(jQuery)
```

## Notes on the code example
* The outside wrapper is required if you wish to use the short jquery "$" syntax.
* $('h1 &gt; a') selects all of the H1 headers (and the inner anchor) that have immediate anchor children
* $('h1:not(:has(a))') selects all H1 headers that do not have anchors embedded
  in them.
* .each, iterates over each element in the selector.

Inside the function the "this" object refers to the current DOM element. If you want
the jQuery object use the $(this) syntax.


## Further Reading
 <a href="http://drupal.org/node/171213">Drupal Documentation on Javascript and jQuery</a>

 <a href="http://jquery.org">jQuery Documentation</a>

 <a href="http://api.jquery.org">jQuery API Documentation</a>


