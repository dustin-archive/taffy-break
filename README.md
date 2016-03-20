Break
===

> Sweet responsive breakpoints

## Why?
+ Created for syncing grids and breakpoints
+ Automatically extends input, even within media queries
+ Includes a shorthand mixin

## Breaks
+ Creates media queries based on item widths
+ Each break is the width of `$break-max` divided by `$break-amount` plus the width of the previous break
+ Each break width is added to the `$break-map` map

This example break will activate when the browser width exceeds the 4th break.

```scss
.break {
  @include break(4) {
    // ...
  }
}
```

## Includes


## Adapters
