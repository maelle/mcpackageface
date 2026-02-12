# Make a new graph

This is a generic function for creating graphs.

## Usage

``` r
make_(...)
```

## Arguments

- ...:

  Parameters, see details below.

## Details

`make_()` is a generic function for creating graphs. For every graph
constructor in igraph that has a `make_` prefix, there is a
corresponding function without the prefix: e.g. for `make_ring()` there
is also [`ring()`](https://rdrr.io/r/grDevices/plotmath.html), etc.

The same is true for the random graph samplers, i.e. for each
constructor with a `sample_` prefix, there is a corresponding function
without that prefix.

These shorter forms can be used together with `make_()`. The advantage
of this form is that the user can specify constructor modifiers which
work with all constructors. E.g. the `with_vertex_()` modifier adds
vertex attributes to the newly created graphs.

See the examples and the various constructor modifiers below.

## Related documentation in the C library

[`simplify`](https://igraph.org/c/html/0.10.17/igraph-Operators.html#igraph_simplify),
[`vcount`](https://igraph.org/c/html/0.10.17/igraph-Basic.html#igraph_vcount),
[`edges`](https://igraph.org/c/html/0.10.17/igraph-Basic.html#igraph_edges),
[`get_eids`](https://igraph.org/c/html/0.10.17/igraph-Basic.html#igraph_get_eids),
[`ecount`](https://igraph.org/c/html/0.10.17/igraph-Basic.html#igraph_ecount)

## See also

Other deterministic constructors: `graph_from_atlas()`,
`graph_from_edgelist()`, `graph_from_literal()`, `make_chordal_ring()`,
`make_circulant()`, `make_empty_graph()`, `make_full_citation_graph()`,
`make_full_graph()`, `make_full_multipartite()`, `make_graph()`,
`make_lattice()`, `make_ring()`, `make_star()`, `make_tree()`,
`make_turan()`, `make_wheel()`

Constructor modifiers (and related functions) `sample_()`,
`simplified()`, `with_edge_()`, `with_graph_()`, `with_vertex_()`,
`without_attr()`, `without_loops()`, `without_multiples()`

## Examples

``` r
r <- make_(ring(10))
#> Error in make_(ring(10)): could not find function "make_"
l <- make_(lattice(c(3, 3, 3)))
#> Error in make_(lattice(c(3, 3, 3))): could not find function "make_"

r2 <- make_(ring(10), with_vertex_(color = "red", name = LETTERS[1:10]))
#> Error in make_(ring(10), with_vertex_(color = "red", name = LETTERS[1:10])): could not find function "make_"
l2 <- make_(lattice(c(3, 3, 3)), with_edge_(weight = 2))
#> Error in make_(lattice(c(3, 3, 3)), with_edge_(weight = 2)): could not find function "make_"

ran <- sample_(degseq(c(3, 3, 3, 3, 3, 3), method = "configuration"), simplified())
#> Error in sample_(degseq(c(3, 3, 3, 3, 3, 3), method = "configuration"),     simplified()): could not find function "sample_"
degree(ran)
#> Error in degree(ran): could not find function "degree"
is_simple(ran)
#> Error in is_simple(ran): could not find function "is_simple"
```
