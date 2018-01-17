# Learn Sass
Learn how to use Sass the CSS extension language

## What?

[Sass](http://sass-lang.com) (Stylistically Awesome Stylesheets) is a CSS
extension language, the bulkier version of it's thinner sibling
[Less](http://lesscss.org/). It has versions that are compatible with Node
and Ruby, it is also included within
[Bootstrap v4](https://getbootstrap.com/docs/4.0/getting-started/introduction/).

## History
Sass originated from another preprocessor called [Haml](http://haml.info/) which
was written by Ruby developers. For that reason, Sass stylesheets used a
Ruby-like syntax with no braces, semi-colons and a strict indentation.

Then in May 2010 Sass introduced a new syntax called SCSS for _Sassy CSS_. This
syntax is a hybrid of the old Sass and CSS syntax:

```
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

You can now use either syntax in your projects.
