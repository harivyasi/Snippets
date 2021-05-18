# Python Tips and Tricks

## Optimization hacks

### Using string instead of list when validating a character
If you are validating if the input _character_ exists in a _list of characters_, use a string instead of the _list of characters_. Using `ipython` `%timeit`:
```python
In [1]: def a():
   ...:     return 'a' in ('d','c','b','a')
   ...:

In [2]: def b():
   ...:     return 'a' in 'dcba'
   ...:

In [3]: %timeit a()
157 ns ± 0.861 ns per loop (mean ± std. dev. of 7 runs, 10000000 loops each)

In [4]: %timeit b()
104 ns ± 0.813 ns per loop (mean ± std. dev. of 7 runs, 10000000 loops each)
```