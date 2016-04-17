Break
===

> Sweet responsive breakpoints

## Why?
+ Built for synchronizing grids and breakpoints
+ Extends content within media queries
+ Includes `break-adapter` mixin for creating break plugins

## Getting Started
+ Install with Bower
+ Import dependencies

```
$ bower install --save taffy-break
```

```scss
@import '../bower_components/fizz-sass/scss/main';
@import '../bower_components/taffy-break/scss/main';
```

## Variables
+ `$break-amount` sets the amount of breaks; set to `12` by default
+ `$break-max` sets the max break width; set to `80em` by default

#### Using Variables
Set the variables before importing dependencies to override defaults.

```scss
$break-amount: 6;
$break-max: 40em;

@import '../bower_components/fizz-sass/scss/main';
@import '../bower_components/taffy-break/scss/main';
```

## Breaks
+ Generates media queries that represent columns set with `$break-amount` that span across the width of `$break-max`

#### Using breaks
The `break` mixin accepts one argument that defines which break to use.

In this example the code inside this break will activate after the browser width exceeds the 2nd break.

```scss
.break {
  @include break(2) {
    // ...
  }
}
```

## Includes
+ Injects content into the break include loop

#### Defining includes
The content should use the `$break-include` global variable to create variations between each break.

This is a simple example that outputs different code for breaks `1` and `2`.

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

#### Defining advanced includes
A more advanced example optionally requires the use of adapters.

When defining an include that is meant to be accessed via adapter the placeholders must follow these conventions.
+ The prefix is used to name your include. It must match the name you use in your adapter.
+ The interfix is used to reference which break your content is for. It must be unique to each include and remain the same for each placeholder within the include
+ The suffix is optional and represents a variant of a placeholder. It should be unique to each placeholder and re-occur within each include

In this example there are multiple placeholders that are associated with each break that can be easily called using an adapter.

```scss
@include break-include {
  @if $break-include == 1 {
    %foobar-one-baz {
      // ...
    }
    %foobar-one-qux {
      // ...
    }
  }
  @else if $break-include == 2 {
    %foobar-two-baz {
      // ...
    }
    %foobar-two-qux {
      // ...
    }
  }
}
```

## Adapters
+ Shorthand for extending placeholders generated from includes

#### Defining adapters
To define an adapter wrap a mixin around a `break-adapter` mixin. The first argument is the prefix of the placeholder that gets extended. The second argument is a list of breaks or break/variant pairs.

```scss
@mixin foobar($breaks) {
  @include break-adapter('foobar', $breaks);
}
```

#### Using adapters
Now you can use your adapter to extend certain blocks of code based on breaks.

```scss
.foobar {
  @include foobar((one baz) (two qux));
}
```

If your break and break variants go by the same name you don't need to define it twice. The following lines are equivalent.

```scss
@include item((6 6) (8 8));
@include item(6 8);
```
