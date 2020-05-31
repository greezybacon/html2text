# HTML to text renderer for PHP

PHP library to render HTML5 to monospaced text. The concept was created to
create text versions of HTML emails. If your software sends HTML email, it
is friendly to also send a plain text version of the document. The plain
text document is generally used by email clients to create the preview text.

## API

`render_html_to_text`

```php
$text = render_html_to_text($html, [$width=76, [$stylesheet=false]]);
```

### Parameters

* `$html` - the HTML document to be rendered. Should be a string.

* `$width` - the width of the rendered document. This is import for word wrapping of block elements and tables.

* `$stylesheet` - custom styles to be implemented in the rendering. These styles will take preference over the built in stylesheet. Currently, only tags and classes are considered. The specificity of a rule is not considered, so in other words, the first rule to match is the one which will be applied to the element.

  Example: `['p' => ['margin-bottom' => '1em']]`

## Stylesheet Interpretation

Stylesheets are currently intepreted as matching elements based on simple classes or tag names. Currently, these style properties are supported:

* `border`
* `margin`
* `padding`
* `text-align`
* `text-decoration`
* `text-transformation`
* `white-space`

Styles are interpreted in a way to try to convert measurements to the same of a monospaced character. The best way to convey measurements in custom stylesheets is with the `em` unit. Since `em` represents the width of character, then the values are used without conversion.
