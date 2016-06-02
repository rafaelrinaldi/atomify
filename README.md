[basscss]: http://www.basscss.com
[css-modules]: https://github.com/css-modules/css-modules
[brent]: https://twitter.com/jxnblk

# atomify ![draft](https://img.shields.io/badge/status-draft-blue.svg?style=flat-square)

> Automatically atomify your CSS

![This might be a silly idea but I'm giving it a shot anyway](http://messages.hellobits.com/warning.svg?message=This%20might%20be%20a%20silly%20idea%20but%20I'm%20giving%20it%20a%20shot%20anyway)

## Why

In my opinion, [Brent Jackson][brent] nailed it with [Basscss][basscss]. It's
a very practical response to CSS modularization, with no bullshit.

The idea of isolating patterns into specific classes and composing them as you
wish is simple but really powerful. If you have a solid design foundation, you
can literally start iterating without having to make CSS changes whatsoever.

Of course you can achieve that by explaining this concept to both developers and
designers and sticking to it. This tool is just an attempt to automate that so
you can apply this concept to code bases that already exist.

## How it works

Given the following input:

```css
.container {
  width: 100%;
  padding: 3rem;
}

.full-width {
  width: 100%;
}
```

This tool would output:

```css
._15QFk {
  width: 100% !important;
}

.container {
  padding: 3rem;
}

.full-width {
}
```

* `_15QFk` it's just an unique id
* We could even have pluggable algorithms to generate the class names (like [CSS Modules][css-modules] does), so `_15QFk` could be something like `w100`
* `!important` could be optional but enforces the concept of immutable styles

## Usage

```sh
$ atomify --help

Usage: atomify input.css > output.css

Options:
  -v    --version           Display current software version
  -h    --help              Display software help and usage details
        --not-so-important  Do not append `!important` at the end of every rule
```

## TBA

* Is a build tool a good way to approach this?
* How debugging would work?
* How to generate a proper report for the compiled file?
* How to sync dev vs. prod markup?
* How to handle media queries?

## Contribute

Feel free to open an issue to give suggestions!
