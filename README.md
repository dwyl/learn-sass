# Learn Sass
Learn how to use Sass the CSS extension language

## What?

[Sass](http://sass-lang.com) (Stylistically Awesome Stylesheets) is a CSS
extension language or preprocessor. It's the bulkier version of it's thinner sibling
[Less](http://lesscss.org/). It has versions that are compatible with Node
and Ruby, it is also included within
[Bootstrap v4](https://getbootstrap.com/docs/4.0/getting-started/introduction/).

## History
Sass originated from another preprocessor called [Haml](http://haml.info/) which
was written by Ruby developers. For that reason, Sass stylesheets used a
Ruby-like syntax with no braces, semi-colons and a strict indentation.

Then in May 2010 Sass introduced a new syntax called SCSS for _Sassy CSS_. This
syntax is a hybrid of the old Sass and CSS syntax:

```css
// Variable
$primary-color: hotpink;

// Mixin
@mixin border-radius($radius) {
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  border-radius: $radius;
}

.my-element {
  color: $primary-color;
  width: 100%;
  overflow: hidden;
}

.my-other-element {
  @include border-radius(5px);
}
```

You can now use either syntax in your projects. SCSS is more widespread and
may be preferred due to its fully compatibility with CSS.

- What languages can I use Sass with?
- How big is it?

- What's a CSS preprocessor?
A layer between the stylesheets you create and the `.css` files that are seen in
the browser.

- Parts of Sass
 - Variables
 - Mixins (reusable blocks of styles)

- What language do I write Sass in?
You can write Sass in either Sass or SCSS (_Sassy CSS_). Sass was the original
language with which Sass was created. It's based on Ruby and not so closely
linked to css. But in 2010 SCSS was introduced to encourage more people to learn
Sass. SCSS is a superset of CSS3; any valid CSS3 file is a valid SCSS file as well.

### Pros

- Values that are used frequently in your project but aren't standard CSS e.g. colours, fonts.
- Easier to maintain
- More efficient
- Faster
- Adheres to DRY (Don't Repeat Yourself) principle

### Cons

- Needless complication
- Bloat
