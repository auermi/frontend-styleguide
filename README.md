# Front-End Styleguide
A styleguide for writing better frontend code

## General Rules

### Indentation
All indentations will be two spaces, not tabs

### Double Quotes vs. Single Quotes
Always use single quotes (‘) for CSS and JavaScript. In HTML, use double quotes (“)

### Dashes vs. Underscores
For naming files, classes, or ids, separate words with dashes (-).

An exception to this rule applies only to partials. Partials should always be prepended with an underscore (_header.scss, _component.scss). 
Trump partials are an exception here as they are prepended with two underscores (__index.scss, __blog.scss)

### Lowercase vs. Uppercase
Use lowercase across the board. Javascript is an obvious exception and should use the camelcase naming convention.

## CSS Standards

### Preprocessor
We use SASS, so styles will be written in .scss files and then complied and minified into one master CSS file.

### IDs vs. Classes
HTML elements should be styled with classes, not IDs

### Nesting
Always nest. That way if someone needs to target the parent class that didn’t have previous styles they don’t have to restructure your code.
```css
body {
  header {
  }
}
```

### Multiple Selectors
Add a line break and comma after each selector
```css
ol,
ul {
}
```

### Formatting property definitions
There should be one space between properties and their values. Also keep one space between class/element/id names
```css
body {
  background-color: #fff;
}
article .post {
  font-size: 2.25em;
}
``` 

### Brevity vs. More Classes
Be terse with your styles but also don’t be super specific with your styles.

### Media Queries
Media Queries should be desktop first. Try to restrict yourself to three media queries at most. Use max-width, not min-width.
Use Chris Coyier’s media query mixin as seen below.
```css
@mixin bp($point) {
  @if $point == large {
    @media (max-width: $large-bp) { @content; }
  }
  @else if $point == medium {
    @media (max-width: $medium-bp) { @content; }
  }
  @else if $point == small {
    @media (max-width: $small-bp)  { @content; }
  }
}
```

### Colors

If transparency is needed, use rgba(). Else, use the hexadecimal format.

### Sizing Units
Use percentages for widths as much as possible. Only set static widths whenever necessary. 
Use EMs for font-size, line-height, height, and any height-based style.
Never change the root font-size. (16px)

### Important Flags
Never use the !important flag under any circumstances. This just creates larger problems for future changes. Take the time to go back and rewrite your components to be more modular to allow for appropriate styling without having to override them this way.

### Vendor Prefixes
Don’t use vendor prefixes in your stylesheets. Use mixins to combine all needed vendor prefixes like this one:
```css
@mixin transform($transform-property) {
  transform: $transform-property;
  -webkit-transform: $transform-property;
  -moz-transform: $transform-property;
  -ms-transform: $transform-property;
}
```

### File Structure
File structure will enforce a very modular format which will keep your styles easy to control and organize.

There are 7 folders or categories in which we will organize our stylesheets.
- **Settings.** These are variables we will use across any files. Includes colors, breakpoint values, and other variables.
- **Tools.** These include all Mixins and functions. Also includes reused classes like clear-fixes or classes that only javascript would need.
- **Vendor.** Includes any 3rd-party libraries you are using.
- **Base.** The stylesheets that style base elements, i.e. h1s, ps, etc.
- **Layout.** Stylesheets handling structural pieces such as wrappers, headers, and footers go here. Page specific structure styles should go here too.
- **Components.** Style components here. Things like cards and posts would fall under this category.
- **Trumps.** Use these as sparingly as possible. Make your components leaner and more flexible rather than leaning on these. The trump files should be organized into files named by the page they trump. Trump files should be prepended by two underscores.
```
/settings
  _breakpoints
  _colors
/tools
  _clearfix
  _hide
  _mixins
/vendor
  _bourbon
  _jqueryui
/base
  _base
/layout
  _wrapper
  _header
  _footer
  _blog
/components
  _card
  _post
/trumps
  __blog
  __index
```

## HTML Standards

### HTML5 Elements
Try to use HTML5 elements such as nav, article, figure, aside, section over vanilla block elements like p or div

### Classes vs. IDs
Classes are used for styling elements, and IDs are for use with JavaScript.

### Attribute Ordering
For consistency, HTML attributes should be written in the following order:

### Attributes
Element attributes should be ordered in the following way:
```
src, for, type, href, id, name, class, data-*, title, alt, aria-*, role
```

# Credits
These standards are largely based on those from [Studio Science](https://github.com/studioscience/frontend-standard), [Benjamin De Cock](https://github.com/bendc/frontend-guidelines), and the [ITCSS pattern](http://itcss.io).
