# CSS Layouts

A collection of the six most used websites layout.

An abstraction layer for your grid system.
Call it a SASS/LESS/CSS interface if you want.

## Why?

There is an hell of grid systems and unfortunate presentational classnames out there.
Eg.

* `.row`
* `.span4`
* `.grid-size1of2`
* `.grid-they-call-me-one-third-column-but-i-am-a-block-level-element-on-mobile`
* `.one-two-three-mambo`

At some point I realized that we use six main layouts over and over:

* Two colums layout: left/right sidebar + main content
* Two colums layout: same width (50/50)
* Three colums layout: left and right sidebar + main content
* Three colums layout same width: (1/3)
* Four colums layout same width: (1/4)

and only a few developers use preprocessors to produce semantic stuff and create layouts.

## Solution

I created a SCSS/CSS interface which basically consist of a set of six empty rules describing the six most used layouts.

For each rule you can define a static `column` size and the style for the `row` container, or use the mixins of your grid system of choice.

Once you have created your layouts, you can (almost) forget about the grid system and use a few classnames to fast-prototype and build layouts.

## Installation

* Download: [zip](https://github.com/giuseppeg/css-layouts/zipball/master)
* Git: `git clone https://github.com/giuseppeg/css-layouts`

## Usage

If you are using SASS this is the way to go:

### Settings

Edit `_layouts.settings.scss` if you want to change the layouts class names.

### Layouts definition

Open up `_layouts.scss` and add the css for the layouts inside the empty rules.

## Example

A two columns layout: left/right sidebar + main content

### SCSS
```scss
// mobile-first

#{$l-container} {
    margin-right: 2.5%;
    margin-left: 2.5%;
}

// desktop devices

@media (min-width: 480px) {
    #{$l-container} {
        @include grid-row;
        margin-right: auto;
        margin-left: auto;
    }

    #{$l-twoColumns} {
        // sidebar
        & > #{$l-side} { @include grid-column(3); }

        // main content
        & > #{$l-content} { @include grid-column($grid-columns - 3); }
    }
}
```

### HTML

```html
<div class="container side-content">
    <div class="side">side content</div>
    <div class="content">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras quis nunc vitae lacus dapibus congue. Nulla nec vestibulum nisi. Proin id mollis risus. Ut eu faucibus quam.</div>
</div>
```

See the [tests](test/) for more examples.

## Author

[@giuseppegurgone](http://twitter.com/giuseppegurgone)

## License (MIT)

Copyright (c) 2013 Giuseppe Gurgone

This work is licensed for reuse under the MIT license.
See the included [LICENSE] (LICENSE) file for details.