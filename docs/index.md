# PolyShell

A high-performance coverage-preserving polygon reduction library for Python, written in Rust.

![Benchmark](assets/Benchmark-Light.svg#only-light)
![Benchmark](assets/Benchmark-Dark.svg#only-dark)
/// caption
A 90% reduction of a 50,000 point polygon.
///

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

!!! tip "Build from source"

    PolyShell can also be built from source using [maturin](https://www.maturin.rs/). See the guide [here](./getting-started/installation.md).

---

## Example

=== "Python 3.10+"

    ```python
    from polyshell import reduce_polygon

    original = [
        (0.0, 0.0),
        (0.0, 1.0),
        (0.5, 0.5),
        (1.0, 1.0),
        (1.0, 0.0),
        (0.0, 0.0),
    ]

    reduced = reduce_polygon(original, "auto", method="vw")
    ```

All of PolyShell's reduction algorithms are accessible through a single function.

For all the available options, see the [guide](./getting-started/user-guide.md).


---

## PolyShell's Axioms 

PolyShell promises to provide reliable high-performance polygon reduction algorithms which behave in a predictable way.
PolyShell's axioms consist of both the assumptions we make about a user's input and, given these are upheld, the
assumptions the user can make about the output they receive.

???+ warning "Input validation"

    PolyShell provides little-to-no input validation. While memory-safety is always guaranteed, if the following
    assumptions are broken you may receive an error or an invalid reduction. If you are uncertain whether your data upholds
    these requirements, we encourage you to use [Shapely](https://shapely.readthedocs.io/en/stable/) to perform your own
    validation first.


### Polygon Validity

All input to PolyShell is expected to be valid.

!!! abstract "Definition: Polygon validity"

    A polygon is said to be valid if:

    1. It is a [simple polygon].
    2. The vertices are stored as a sequence in clockwise order.
    3. The first and last coordinate in the sequence are equal.

[simple polygon]: https://en.wikipedia.org/wiki/Simple_polygon, "A polygon with no holes or self-intersections."

### Our Promise

Provided the assumptions made above are upheld, PolyShell makes the following promises:

1. The reduced polygon will always be [valid](#polygon-validity).
2. The reduced polygon will always contain the input polygon in its interior.
3. Vertices are never moved nor added. 
4. Reduction preserves the ordering of the vertices, but is not necessarily stable.

???+ note "Vertex order stability"

    While the sequence of vertices within the polygon is preserved, the location of the first vertex may shift depending on
    the algorithm used.

