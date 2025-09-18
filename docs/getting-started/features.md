# Features

PolyShell currently provides three reduction algorithms to fit your needs. Each has different performance
characteristics and will ...

| Algorithm                                       | Available modes | Parallel                | Fastest for      | Characteristics |
|-------------------------------------------------|-----------------|-------------------------|------------------|-----------------|
| [Visvalingam-Whyatt](#visvalingam-whyatt)       | epsilon, length | :octicons-check-16:[^1] | Small reductions | Smoothing       |
| [Ramer-Douglas-Peucher](#ramer-douglas-peucker) | epsilon         | :octicons-check-16:     | Large reductions | ???             |
| [Charshape](#charshape)                         | epsilon, length | :octicons-x-16:         | Large reductions | ???             |

[^1]: Parallelism is only supported by epsilon mode.

!!! tip "Parallelism"

    Whenever possible PolyShell will run reduction of a single polygon across multiple cores. This is handled
    automatically and will lead to a sizable increase in performance. Even in parallel execution mode, PolyShell
    guarantees no data-races.

## Algorithms

If no method is provided

### Visvalingam-Whyatt

For more information on the algorithm see the [reference](../reference/algorithms/visvalingam-whyatt.md).


### Ramer-Douglas-Peucker

For more information on the algorithm see the [reference](../reference/algorithms/ramer-douglas-peucker.md).

### Charshape

For more information on the algorithm see the [reference].

## Running Modes

### Epsilon

... meaning of epsilon varies.

Epsilon reduction mode can be enabled for supported algorithms using the `reduction_mode` argument, providing tolerance
in the third position or using the keyword argument `epsilon`:

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

    reduced = reduce_polygon(original, "eps", epsilon=0.1, method="vw")
    ```

### Length

... length is min or max depending on reduction direction.

Length reduction mode can be enabled for supported algorithms using the `reduction_mode` argument, providing the desired
length in the third position or using the keyword argument `length`:

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

    reduced = reduce_polygon(original, "length", length=5, method="charshape")
    ```

## External Package Support

PolyShell currently supports ...
