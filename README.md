

## PHPreact - A React inspired (WordPress) HTML rendering library

I’m fed up with outputing HTML in PHP. Especially keeping in mind that outputting safe HTML can be a challenge when outputting user input. This was the basis for this idea.

Before I begin I wish to state I did no prior research before starting on this proof of concept, therefore it is very likely there are similar, easier and/or safer alternatives out there. Please keep an open mind.

The idea to have a way of rendering HTML in a way that is similar to the way React accomplishes this after the JSX has been transpiled which looks like this:

```js
React.render(
	React.createElement(
		"a",
		{
			href: "https://wordpress.org",
			ref: "nofollow",
		},
		"This is a link to WordPress"
	),
	document.getElementById( "app" )
);
```

Resulting in the following output:

```html
<a href="https://wordpress.org" ref="nofollow">
	This is a link to WordPress
<a>
```

Of course React is meant for running in browser applications, where PHP is meant to output HTML once and be done with it. But there could be some upsides to this approach, especially if you conside that the link or the anchor contents could be user input.

To safely output the above HTML in WordPress you would write the following code (or something in the same fashion) assuming you work with filterable/user-defined attributes and/or content:

```php
echo '<a href="', esc_url( 'https://wordpress.org' ), '" rel="', esc_attr( "nofollow" ), '">',
	esc_html( 'This is a link to WordPress' ),
	'</a>';
```

My idea is to create a project that will make outputting HTML in PHP look like this:

```php
PHPreact::render(
	PHPreact::el(
		'a',
		[
			'href' => 'https://wordpress.org',
			'rel'  => [ 'nofollow' ],
		],
		'This is a link to WordPress'
	)
);
```

1. It is more readable.
2. It knows `href` is supposed to be an URL and escape it accordingly.
3. The same goes for `ref` being an attribute.
4. It can optionally receive arrays for some attributes making them easier to manage.

And no worries, we will get to (reusable) components and nesting. First off: Nesting.

### Nesting

### Components


> Written with [StackEdit](https://stackedit.io/).
