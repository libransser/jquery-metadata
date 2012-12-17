# jQuery.Metadata Plugin

Plugin originally created by [John Resig](https://github.com/jquery/jquery-metadata)

## Why this fork?

The modifications made in this fork were made in order to use it in conjunction
with the [jQuery.Validation](https://github.com/jzaefferer/jquery-validation)
plugin (versions 1.10.0 and below), allowing to store the validation rules as
data-* attributes.

For example:

	<input type="text" name="email" data-required="true" data-email="true" data-messages="{ required:'Your email is required', email:'Enter a valid email'}" />

For jQuery.Validation 1.10.0, a more straightforward way of defining messages
was introduced:

	<input type="text" name="email" data-required="true" data-email="true" data-msg-required="Your email is required" data-msg-email="Enter a valid email" />

But with the previous version of jQuery.Metadata, this caused an error. So this
particular fork made some changes to allow it.

For jQuery.Validation 1.11.0, jQuery.Metadata support will be dropped as
jQuery.Validation will include support for data-* natively.

## Changelog

Changes from version 2.0:
 + Added the support for HTML5 data-* attributes made by Craga89 on https://github.com/Craga89/jquery-metadata
 + Corrected behaviour when using HTML5 data-* attributes for the jQuery.Validation plugin, as trying to use the values stored in data-* as plain strings wasn't straight-forward. The values first get evaluated as usual (working for booleans, hashes, arrays, etc.), if that fails it is evaluated as plain string.
 + Default type changed to 'html5'

## Examples

For examples on the other 4 types of metadata storage refer to the in-code
comments or refer to the original repo https://github.com/jquery/jquery-metadata

In the case of the HTML data-* attributes, their use is as follows:

	<p id='one' class='some_class' data-item_id='1' data-item_label='Label'>This is a p</p>

This particular version of the jQuery.Metadata plugin already sets the use of HTML5
data-* attributes by default, so to get the values in them you just use:

	$('#one').metadata().item_id == 1; $('#one').metadata().item_label == 'Label'
