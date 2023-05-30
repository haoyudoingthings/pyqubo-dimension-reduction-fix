# Important: The code doesn't seem to be working as intended. Use at your own discretion.
# pyqubo-dimension-reduction-fix

Fix the dimension reduction process so that the penalty strength is automatically chosen to be the smallest appropriate value.

## Usage

Don't specify any value for the `strength` argument (default to `None`) when calling `H.compile()`. The function will handle the choice of penalty strength automatically.

If a value for `strength` is specified, the function will revert to its original behavior.

## Example Code

```bash
>>> import pyqubo as pq
>>> a, b, c, d = pq.Binary('a'), pq.Binary('b'), pq.Binary('c'), pq.Binary('d')
>>> (2*a*b*c-a*b*d).compile()
Model(CompiledQubo({('a', 'a'): 0.0,
 ('a', 'a*b'): -4.0,
 ('a', 'b'): 2.0,
 ('a*b', 'a*b'): 6.0,
 ('a*b', 'b'): -4.0,
 ('a*b', 'c'): 2.0,
 ('a*b', 'd'): -1.0,
 ('b', 'b'): 0.0,
 ('c', 'c'): 0.0,
 ('d', 'd'): 0.0}, offset=0.0), structure={'a': ('a',), 'b': ('b',), 'c': ('c',), 'd': ('d',)})
>>> (2*a*b*c-5*a*b*d).compile()
Model(CompiledQubo({('a', 'a'): 0.0,
 ('a', 'a*b'): -10.0,
 ('a', 'b'): 5.0,
 ('a*b', 'a*b'): 15.0,
 ('a*b', 'b'): -10.0,
 ('a*b', 'c'): 2.0,
 ('a*b', 'd'): -5.0,
 ('b', 'b'): 0.0,
 ('c', 'c'): 0.0,
 ('d', 'd'): 0.0}, offset=0.0), structure={'a': ('a',), 'b': ('b',), 'c': ('c',), 'd': ('d',)})
>>> (2*a*b*c+a*b*d).compile()
Model(CompiledQubo({('a', 'a'): 0.0,
 ('a', 'a*b'): -3.0,
 ('a', 'b'): 3.0,
 ('a*b', 'a*b'): 3.0,
 ('a*b', 'b'): -3.0,
 ('a*b', 'c'): 2.0,
 ('a*b', 'd'): 1.0,
 ('b', 'b'): 0.0,
 ('c', 'c'): 0.0,
 ('d', 'd'): 0.0}, offset=0.0), structure={'a': ('a',), 'b': ('b',), 'c': ('c',), 'd': ('d',)})
```

## Installation

Copy the files in `anaconda3` folder and overwrite the correpsonding files in your directory.

## Dependency

The fix is based on `pyqubo 0.4.0` and `dimod 0.11.5`. This fix will not work for `pyqubo >= 1.0.0` since the core code transitioned to c++. Not sure about the dependency on `dimod` version.
