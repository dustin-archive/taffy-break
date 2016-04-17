Break
===

> Sweet responsive breakpoints

## Why?
+ Built for synchronizing grids and breakpoints
+ Easily extend content across at-rules

## Getting Started
+ Install with Bower
+ Import dependencies

```
$ bower install --save taffy-break
```

```scss
@import '../bower_components/taffy-break/scss/main';
```

## Variables
+ `$break-amount` sets the amount of breaks
+ `$break-max` sets the max break width

#### Using Variables
The default `$break-amount` is set to `12` and the default `$break-max` is set to `80em`. To override these defaults set the variables before importing the dependencies.

```scss
$break-amount: 6;
$break-max: 40em;

@import '../bower_components/taffy-break/scss/main';
```

## Breaks
+ Generates media queries that represent breaks or columns
+ Calculated with `$break-amount` and `$break-max` variables
+ Accepts one argument that defines which break to use

#### Using breaks
In this example the code inside this break will activate after the browser width exceeds the 2nd break.

```scss
.break {
  @include break(2) {
    // ...
  }
}
```
