Scrupulous
=======

Scrupulous.js is super simple, client side, inline form validation using HTML5 attributes. Add all the standard HTML5 form attributes and call the plugin and it will automatically add inline validation with full styleable elements and class names. 

Scrupulous.js is built around [Bootstrap](http://getbootstrap.com/), using the same class name and HTML structure for simple implementation. Not using Bootstrap? No problem, just update the class names in the CSS file and with minor changes it should still work fine. 

#Setup
* scrupulous.css: you will need to include the scrupulous.css which adds some additional styling to the form elements. 
* jQuery: Scrupulous should work with most newer versions of jQuery, Have not tested how far back it is supported
* scrupulous.js: Runs a jQuery plugin. 
* Call the $.scrupulous() plugin on the form(s) you would like to validate. 

		$(function(){
			$('.validate-form').scrupulous();	
		});

##HTML
Then just add standard HTML5 attributes to your form and Scrupulous takes care of the rest. 

	<form class="validate-form" method="post" action="/">
		<div class="form-group">
			<label for="email">Email</label>
			<input type="email" class="form-control" id="email" name="email" title="Please Enter a Valid Email Address" required>
    </div>
  </form>

Note that the title of the field becomes the error message, mimmicking the default browser HTML5 validation messaging.

##HTML with Errors

If an error is detected the resulting HTML is generated dynamically.

	<div class="form-group has-error">
		<label for="name">Name</label>
		<input type="text" class="form-control invalid" id="name" name="name" title="Please Enter a Name" required>
    	<label class="error-message" for="name">Please Enter a Name</label>
    </div>

##Valid HTML

When the form validates the following HTML is generated dynamically 

	<div class="form-group has-success">
		<label for="name">Name</label>
		<input type="text" class="form-control valid" id="name" name="name" title="Please Enter a Name" required>
	</div>

#Legacy Browser Support
Currently if the browser does not support element.checkValidity Scrupulous will silently fail. You should be using solid server side validation as a backup. It may be possible to use it in conjunction with a HTML5 form validation polyfill. Let us know if you hve any luck. 

#Modernizr.load Example
Scrupulous may also be loaded with Modernizr.load as well. 

	Modernizr.load({
	    test: Modernizr.input.required,
	    yep: 'js/scrupulous.js',
	    complete: function() {
	      $('#my-form').scrupulous();
	    }
	  });
