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

# eval

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Alias for [`eval`][mdn-eval] global.



<section class="usage">

## Usage

```javascript
import evil from 'https://cdn.jsdelivr.net/gh/stdlib-js/utils-eval@deno/mod.js';
```

#### evil( str )

Alias for [`eval`][mdn-eval] global.

```javascript
var v = evil( '5*4*3*2*1' );
// returns 120
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   A reference to [`eval`][mdn-eval] **is** treated differently by the compiler. For example, when evaluating code containing block-scoped declarations (e.g., `let`, `const`, `function`, `class`), the compiler may throw an `error` complaining that block-scoped declarations are **not** yet supported outside of `strict mode`. One possible workaround is to include `"use strict";` in the evaluated code, as done in the example below.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
import evil from 'https://cdn.jsdelivr.net/gh/stdlib-js/utils-eval@deno/mod.js';

var ctors;
var fcn;
var i;

function compile( ctor ) {
    var name;
    var str;

    name = ctor.match( /^(\w*)Array$/ )[ 1 ];
    name += 'DataArray';

    str = '';
    str += '(function create(){';
    str += '"use strict";';
    str += 'class '+name+' extends '+ctor+'{';
    str += 'constructor(x){';
    str += 'super(x);';
    str += '}';
    str += '}';
    str += 'return '+name+';';
    str += '})();';
    return str;
}

ctors = [
    'Int8Array',
    'Uint8Array',
    'Uint8ClampedArray',
    'Int16Array',
    'Uint16Array',
    'Int32Array',
    'Uint32Array',
    'Float32Array',
    'Float64Array',
    'Array'
];

for ( i = 0; i < ctors.length; i++ ) {
    fcn = evil( compile( ctors[i] ) );
    console.log( fcn.toString() );
}
```

</section>

<!-- /.examples -->



<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

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

[npm-image]: http://img.shields.io/npm/v/@stdlib/utils-eval.svg
[npm-url]: https://npmjs.org/package/@stdlib/utils-eval

[test-image]: https://github.com/stdlib-js/utils-eval/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/utils-eval/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/utils-eval/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/utils-eval?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/utils-eval.svg
[dependencies-url]: https://david-dm.org/stdlib-js/utils-eval/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[cli-section]: https://github.com/stdlib-js/utils-eval#cli
[cli-url]: https://github.com/stdlib-js/utils-eval/tree/cli
[@stdlib/utils-eval]: https://github.com/stdlib-js/utils-eval/tree/main

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/utils-eval/tree/deno
[umd-url]: https://github.com/stdlib-js/utils-eval/tree/umd
[esm-url]: https://github.com/stdlib-js/utils-eval/tree/esm
[branches-url]: https://github.com/stdlib-js/utils-eval/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/utils-eval/main/LICENSE

[mdn-eval]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/eval

</section>

<!-- /.links -->
