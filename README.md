Break
===

> Sweet responsive breakpoints

## Why?
+ Created for synchronizing grids and breakpoints
+ Automatically extends content, even within media queries
+ Includes a `break-adapter` mixin for creating shorthand break plugins

## Breaks
+ Generates media queries
+ Each break is the width of `$break-max` divided by `$break-amount` plus the width of the previous break
+ Each break width is added to the `$break-map` map

#### Using breaks

This example break will activate when the browser width exceeds the 2nd break.

```scss
.break {
  @include break(2) {
    // ...
  }
}
```

## Includes
+ Creates breaks for the inner code
+ Updates a global variable `$break-include` which is the value of the break currently being processed

#### Using includes
+ Inner code should utilize the `$break-include` global variable to create changes between each break
+ The amount of breaks is controlled by the `$break-amount` variable

```scss
@include break-include {
  // ...
}
```

#### Example

This example outputs different code for each break.

```scss
@include break-include {
  @if $break-include == 1 {
    // ...
  }
  @else if $break-include == 2 {
    // ...
  }
}
```

## Adapters
+ Determines which break to extend from

#### Using adapters

Define an adapter like this.

```scss
@mixin item($breaks) {
  @include break-adapter('item', $breaks);
}
```

Now use your adapter like this.

```scss
.item {
  @include item(2 '6:4' '8:6');
  // ...
}
```
