sdsdot
NPM version Build Status Coverage Status

Calculate the dot product of two single-precision floating-point vectors with extended accumulation.

The dot product (or scalar product) is defined as

Installation
npm install @stdlib/blas-base-sdsdot
Alternatively,

To load the package in a website via a script tag without installation and bundlers, use the ES Module available on the esm branch (see README).
If you are using Deno, visit the deno branch (see README for usage intructions).
For use in Observable, or in browser/node environments, use the Universal Module Definition (UMD) build available on the umd branch (see README).
The branches.md file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

Usage
var sdsdot = require( '@stdlib/blas-base-sdsdot' );
sdsdot( N, scalar, x, strideX, y, strideY )
Calculates the dot product of vectors x and y with extended accumulation.

var Float32Array = require( '@stdlib/array-float32' );

var x = new Float32Array( [ 4.0, 2.0, -3.0, 5.0, -1.0 ] );
var y = new Float32Array( [ 2.0, 6.0, -1.0, -4.0, 8.0 ] );

var z = sdsdot( x.length, 0.0, x, 1, y, 1 );
// returns -5.0
The function has the following parameters:

N: number of indexed elements.
scalar: scalar constant added to the dot product.
x: input Float32Array.
strideX: index increment for x.
y: input Float32Array.
strideY: index increment for y.
The N and stride parameters determine which elements in the strided arrays are accessed at runtime. For example, to calculate the dot product of every other value in x and the first N elements of y in reverse order,

var Float32Array = require( '@stdlib/array-float32' );

var x = new Float32Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0 ] );
var y = new Float32Array( [ 1.0, 1.0, 1.0, 1.0, 1.0, 1.0 ] );

var z = sdsdot( 3, 0.0, x, 2, y, -1 );
// returns 9.0
Note that indexing is relative to the first index. To introduce an offset, use typed array views.

var Float32Array = require( '@stdlib/array-float32' );

// Initial arrays...
var x0 = new Float32Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0 ] );
var y0 = new Float32Array( [ 7.0, 8.0, 9.0, 10.0, 11.0, 12.0 ] );

// Create offset views...
var x1 = new Float32Array( x0.buffer, x0.BYTES_PER_ELEMENT*1 ); // start at 2nd element
var y1 = new Float32Array( y0.buffer, y0.BYTES_PER_ELEMENT*3 ); // start at 4th element

var z = sdsdot( 3, 0.0, x1, -2, y1, 1 );
// returns 128.0
sdsdot.ndarray( N, x, strideX, offsetX, y, strideY, offsetY )
Calculates the dot product of vectors x and y with extended accumulation and using alternative indexing semantics.

var Float32Array = require( '@stdlib/array-float32' );

var x = new Float32Array( [ 4.0, 2.0, -3.0, 5.0, -1.0 ] );
var y = new Float32Array( [ 2.0, 6.0, -1.0, -4.0, 8.0 ] );

var z = sdsdot.ndarray( x.length, 0.0, x, 1, 0, y, 1, 0 );
// returns -5.0
The function has the following additional parameters:

offsetX: starting index for x.
offsetY: starting index for y.
While typed array views mandate a view offset based on the underlying buffer, the offset parameters support indexing semantics based on starting indices. For example, to calculate the dot product of every other value in x starting from the second value with the last 3 elements in y in reverse order

var Float32Array = require( '@stdlib/array-float32' );

var x = new Float32Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0 ] );
var y = new Float32Array( [ 7.0, 8.0, 9.0, 10.0, 11.0, 12.0 ] );

var z = sdsdot.ndarray( 3, 0.0, x, 2, 1, y, -1, y.length-1 );
// returns 128.0
Notes
If N <= 0, both functions return scalar.
sdsdot() corresponds to the BLAS level 1 function sdsdot.
Examples
var discreteUniform = require( '@stdlib/random-array-discrete-uniform' );
var sdsdot = require( '@stdlib/blas-base-sdsdot' );

var opts = {
    'dtype': 'float32'
};
var x = discreteUniform( 10, 0, 100, opts );
console.log( x );

var y = discreteUniform( x.length, 0, 10, opts );
console.log( y );

var out = sdsdot( x.length, 0.0, x, 1, y, -1 );
console.log( out );
References
Lawson, Charles L., Richard J. Hanson, Fred T. Krogh, and David Ronald Kincaid. 1979. "Algorithm 539: Basic Linear Algebra Subprograms for Fortran Usage [F1]." ACM Transactions on Mathematical Software 5 (3). New York, NY, USA: Association for Computing Machinery: 324–25. doi:10.1145/355841.355848.
See Also
@stdlib/blas-base/ddot: calculate the dot product of two double-precision floating-point vectors.
@stdlib/blas-base/dsdot: calculate the dot product with extended accumulation and result of two single-precision floating-point vectors.
@stdlib/blas-base/sdot: calculate the dot product of two single-precision floating-point vectors.
Notice
This package is part of stdlib, a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop stdlib, see the main project repository.

Community
Chat
