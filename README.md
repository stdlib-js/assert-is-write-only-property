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

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Test if an object's own property is [write-only][@stdlib/utils/define-write-only-accessor].



<section class="usage">

## Usage

```javascript
import isWriteOnlyProperty from 'https://cdn.jsdelivr.net/gh/stdlib-js/assert-is-write-only-property@deno/mod.js';
```

#### isWriteOnlyProperty( value, property )

Returns a `boolean` indicating if a `value` has a [write-only][@stdlib/utils/define-write-only-accessor] `property`.

<!-- eslint-disable no-restricted-syntax -->

```javascript
import defineProperty from 'https://cdn.jsdelivr.net/gh/stdlib-js/utils-define-property@deno/mod.js';

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
    import defineProperty from 'https://cdn.jsdelivr.net/gh/stdlib-js/utils-define-property@deno/mod.js';

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
import isWriteOnlyProperty from 'https://cdn.jsdelivr.net/gh/stdlib-js/assert-is-write-only-property@deno/mod.js';

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

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

* * *

## See Also

-   <span class="package-name">[`@stdlib/assert-is-read-only-property`][@stdlib/assert/is-read-only-property]</span><span class="delimiter">: </span><span class="description">test if an object's own property is read-only.</span>
-   <span class="package-name">[`@stdlib/assert-is-read-write-property`][@stdlib/assert/is-read-write-property]</span><span class="delimiter">: </span><span class="description">test if an object's own property is readable and writable.</span>
-   <span class="package-name">[`@stdlib/assert-is-writable-property`][@stdlib/assert/is-writable-property]</span><span class="delimiter">: </span><span class="description">test if an object's own property is writable.</span>
-   <span class="package-name">[`@stdlib/assert-is-write-only-property-in`][@stdlib/assert/is-write-only-property-in]</span><span class="delimiter">: </span><span class="description">test if an object's own or inherited property is write-only.</span>

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2023. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/assert-is-write-only-property.svg
[npm-url]: https://npmjs.org/package/@stdlib/assert-is-write-only-property

[test-image]: https://github.com/stdlib-js/assert-is-write-only-property/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/assert-is-write-only-property/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/assert-is-write-only-property/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/assert-is-write-only-property?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/assert-is-write-only-property.svg
[dependencies-url]: https://david-dm.org/stdlib-js/assert-is-write-only-property/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/assert-is-write-only-property/tree/deno
[umd-url]: https://github.com/stdlib-js/assert-is-write-only-property/tree/umd
[esm-url]: https://github.com/stdlib-js/assert-is-write-only-property/tree/esm
[branches-url]: https://github.com/stdlib-js/assert-is-write-only-property/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/assert-is-write-only-property/main/LICENSE

[@stdlib/utils/define-write-only-accessor]: https://github.com/stdlib-js/utils-define-write-only-accessor/tree/deno

<!-- <related-links> -->

[@stdlib/assert/is-read-only-property]: https://github.com/stdlib-js/assert-is-read-only-property/tree/deno

[@stdlib/assert/is-read-write-property]: https://github.com/stdlib-js/assert-is-read-write-property/tree/deno

[@stdlib/assert/is-writable-property]: https://github.com/stdlib-js/assert-is-writable-property/tree/deno

[@stdlib/assert/is-write-only-property-in]: https://github.com/stdlib-js/assert-is-write-only-property-in/tree/deno

<!-- </related-links> -->

</section>

<!-- /.links -->
