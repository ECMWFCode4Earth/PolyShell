# PolyShell

A high-performance coverage-preserving polygon reduction library for Python, written in Rust.

![Benchmark](assets/Benchmark-Light.svg#only-light)
![Benchmark](assets/Benchmark-Dark.svg#only-dark)

---

## Highlights

- ✅ **Coverage guarantees** — guarantees encapsulation of the initial polygon.
- ⚡ **Rust-powered performance** — memory safe and highly performant algorithms.
- 🧩 **Simple Python API** — single storefront to access all reduction methods and modes.
- 🌍 **Geospatial ready** — works seamlessly with [NumPy](https://numpy.org/) and [Shapely](https://shapely.readthedocs.io/).
- 📏 **Tunable** — manually control reduction rates and precision.
- 🐍 **PyPy compatible** — out-of-the-box support for CPython and [PyPy](https://pypy.org/).

---

## Installation

PolyShell is available on [PyPI](https://pypi.org/) for easy installation:

<!-- termynal -->

```
$ pip install polyshell
---> 100%
Installed
```

Alternatively, PolyShell can also be built from source using [maturin](https://www.maturin.rs/). See the guide [here].

---

## Example

=== "Python 3.10+"

    ```python
    from polyshell import reduce_polygon

    original = [
        (),
        (),
        (),
        (),
        (),
        (),
    ]

    reduced = reduce_polygon(original, "auto", method="vw")
    ```

For a full guide see ...

---

## PolyShell's Contract

PolyShell promises to provide reliable high-performance polygon reduction algorithms which behave in a predictable way.
PolyShell's contract consists of both the assumptions PolyShell make about a user's input and, given these are upheld,
the assumptions the user can make about the output they receive.

### Our Assumptions

PolyShell provides little-to-no input validation on the input polygon. While PolyShell always guarantees memory-safety,
if the following assumptions are broken you may receive an error or invalid output. If you are uncertain whether your
data upholds these constraints we encourage you to use [Shapely](https://shapely.readthedocs.io/en/stable/) to perform
your own validation first.

1. The input polygon must be valid.

### Our Promises

Provided the assumptions made above are upheld, PolyShell makes the following promises:

1. The output polygon will always be valid.