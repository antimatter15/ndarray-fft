ndarray-fft
===========
A fast Fourier transform implementation for [ndarrays](https://github.com/mikolalysenko/ndarray).  You can use this to do image processing operations on big, higher dimensional typed arrays in JavaScript.

**WORK IN PROGRESS**

## Example

```javascript
var ndarray = require("ndarray")
var ops = require("ndarray-ops")
var fft = require("ndarray-fft")

var x = ops.random(ndarray.zeros([256, 256]))
  , y = ops.random(ndarray.zeros([256, 256]))

//Forward transform x/y
fft(1, x, y)

//Invert transform
fft(-1, x, y)
```

### `require("ndarray-fft")(dir, x, y)`
Executes a fast Fourier transform on the complex valued array x/y.  

* `dir` - Either +/- 1.  Determines whether to use a forward or inverse FFT
* `x` the real part of the typed array
* `y` the imaginary part of the typed array.

**Note** This code is fastest when the components of the shapes arrays are all powers of two.  For non-power of two shapes, Bluestein's fft is used which is somewhat slower.  Also note that this code clobbers [scratch](https://github.com/mikolalysenko/scratch) memory.

# Credits
(c) 2013 Mikola Lysenko.  MIT License.

Radix 2 FFT based on code by Paul Bourke.