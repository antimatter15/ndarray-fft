ndarray-fft
===========
A fast Fourier transform implementation for [ndarrays](https://github.com/mikolalysenko/ndarray).  You can use this to do image processing operations on big, higher dimensional typed arrays in JavaScript.

## Example

```javascript
var zeros = require("zeros")
var ops = require("ndarray-ops")
var fft = require("ndarray-fft")

var x = ops.random(zeros([256, 256]))
  , y = ops.random(zeros([256, 256]))

//Forward transform x/y
fft(1, x, y)

//Invert transform
fft(-1, x, y)
```

## Install
Via npm:

    npm install ndarray-fft


### `require("ndarray-fft")(dir, x, y)`
Executes a fast Fourier transform on the complex valued array x/y.  

* `dir` - Either +/- 1.  Determines whether to use a forward or inverse FFT
* `x` the real part of the signal, encoded as an ndarray
* `y` the imaginary part of the signal, encoded as an ndarray

`x` and `y` are transformed in place.

**Note** This code is fastest when the components of the shapes arrays are all powers of two.  For non-power of two shapes, Bluestein's fft is used which is somewhat slower.

**Note2** The inverse FFT is scaled by 1/N, forward FFT is unnormalized.

# Credits
(c) 2013 Mikola Lysenko.  MIT License.

Radix 2 FFT based on code by Paul Bourke.