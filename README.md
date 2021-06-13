<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# isWriteOnlyProperty

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] [![dependencies][dependencies-image]][dependencies-url]

> Test if an object's own property is [write-only][@stdlib/utils/define-write-only-accessor].

<section class="installation">

## Installation

```bash
npm install @stdlib/assert-is-write-only-property
```

</section>

<section class="usage">

## Usage

```javascript
var isWriteOnlyProperty = require( '@stdlib/assert-is-write-only-property' );
```

#### isWriteOnlyProperty( value, property )

Returns a `boolean` indicating if a `value` has a [write-only][@stdlib/utils/define-write-only-accessor] `property`.

<!-- eslint-disable no-restricted-syntax -->

```javascript
var defineProperty = require( '@stdlib/utils-define-property' );

var obj = {
    'foo': 'bar'
};

defineProperty( obj, 'beep', {
    'configurable': false,
    'enumerable': false,
    'writable': false,
    'value': 'boop'
});

defineProperty( obj, 'accessor', {
    'configurable': false,
    'enumerable': true,
    'set': function setter( v ) {
        obj.foo = v;
    }
});

var bool = isWriteOnlyProperty( obj, 'foo' );
// returns false

bool = isWriteOnlyProperty( obj, 'beep' );
// returns false

bool = isWriteOnlyProperty( obj, 'accessor' );
// returns true
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Value arguments other than `null` or `undefined` are coerced to `objects`.

    ```javascript
    var bool = isWriteOnlyProperty( 'beep', 'length' );
    // returns false
    ```

-   Property arguments are coerced to `strings`.

    ```javascript
    var defineProperty = require( '@stdlib/utils-define-property' );

    var obj = {};

    function setter( v ) {
        obj.null = v;
    }

    defineProperty( obj, 'null', {
        'configurable': false,
        'enumerable': true,
        'set': setter
    });

    var bool = isWriteOnlyProperty( obj, null );
    // returns true
    ```

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint-disable object-curly-newline -->

<!-- eslint no-undef: "error" -->

```javascript
var isWriteOnlyProperty = require( '@stdlib/assert-is-write-only-property' );

var bool = isWriteOnlyProperty( 'a', 'length' );
// returns false

bool = isWriteOnlyProperty( { 'a': 'b' }, 'a' );
// returns false

bool = isWriteOnlyProperty( [ 'a' ], 0 );
// returns false

bool = isWriteOnlyProperty( { 'null': false }, null );
// returns false

bool = isWriteOnlyProperty( { '[object Object]': false }, {} );
// returns false

bool = isWriteOnlyProperty( {}, 'toString' );
// returns false

bool = isWriteOnlyProperty( {}, 'hasOwnProperty' );
// returns false

bool = isWriteOnlyProperty( null, 'a' );
// returns false

bool = isWriteOnlyProperty( void 0, 'a' );
// returns false
```

</section>

<!-- /.examples -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2021. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/assert-is-write-only-property.svg
[npm-url]: https://npmjs.org/package/@stdlib/assert-is-write-only-property

[test-image]: https://github.com/stdlib-js/assert-is-write-only-property/actions/workflows/test.yml/badge.svg
[test-url]: https://github.com/stdlib-js/assert-is-write-only-property/actions/workflows/test.yml

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/assert-is-write-only-property/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/assert-is-write-only-property?branch=main

[dependencies-image]: https://img.shields.io/david/stdlib-js/assert-is-write-only-property
[dependencies-url]: https://david-dm.org/stdlib-js/assert-is-write-only-property/main

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/assert-is-write-only-property/main/LICENSE

[@stdlib/utils/define-write-only-accessor]: https://github.com/stdlib-js/utils-define-write-only-accessor

</section>

<!-- /.links -->
