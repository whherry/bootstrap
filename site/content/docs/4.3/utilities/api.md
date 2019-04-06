---
layout: docs
title: Utilities API
description: The utility API is a Sass based tool to generate utility classes.
group: utilities
aliases: "/docs/4.3/utilities/"
toc: true
---

## Bootstrap utilities

The bootstrap utilities are generated with the utility API which can be used to change or extend Bootstraps utility classes. Before reading on, you will need to know what sass maps work, information about it can be found in the [official docs] (https://sass-lang.com/documentation/file.SASS_REFERENCE.html#maps).

The `$utilities` map contains all utilities and is later merged with your custom `$utilities` map if present.
The utility variables accept the following options:

- `property`: Obviously just the name of the property. This can be a string or an array of strings (needed for eg. horizontal paddings or margins).
- `responsive` _(optional)_: Boolean indicating if responsive classes need to be generated. `false` by default.
- `class` _(optional)_: Variable to change the class name if you don't want it to be the same as the property.
- `values`: This can be a list of values or a map if you don't want the class name to be the same as the value. If null is used as map key, it isn't rendered.
- `print` _(optional)_: Boolean indicating if print classes need to be generated. `false` by default.
  

## Adding utilities to the utility API

All utility variables are added to the `$utilities` variable. If you want to add your custom utilities, you can add
them like this:

```scss
$utilities: (
  "opacity": (
    property: opacity,
    values: (
      0: 0,
      25: .25,
      50: .5,
      100: 1,
    )
  )
 );
```

Output:
```css
.opacity-0 {
  opacity: 0;
}
.opacity-25 {
  opacity: .25;
}
.opacity-75 {
  opacity: .75;
}
.opacity-100 {
  opacity: 100;
}
```

## Changing utilities

Overriding excising utilities is possible by using the same key. For example if you want more responsive overflow
utility classes you can do this:

```scss
$utilities: (
  "overflow": (
    responsive: true,
    property: overflow,
    values: visible hidden scroll auto,
  ),
);
```

## Removing utilities

Utilities can also be removed, for example if you want to remove the `float` utilities:

```scss
$utilities: (
  "float": null,
);
```
