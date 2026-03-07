# Snippets

## String & Parsing

### Split and convert in one line:

```python
nums = [int(x) for x in "1,2,3".split(',')]
words = "hello world".split()
```

### Extract digits/characters:

```python
digits = ''.join(c for c in text if c.isdigit())
uppercase = text.upper()
```

### Lines and strip:

```python
for line in input_text.strip().split('\n'):
    # process each line
```

### Regex for complex patterns:

```python
import re
nums = re.findall(r'\d+', text)
matches = re.findall(r'(\w+)=(\d+)', text)
```

---

## Collections & Iteration

### Enumerate with index:

```python
for i, item in enumerate(lst):
    print(f"{i}: {item}")
    ```

### Zip multiple iterables:

```python
for a, b in zip(list1, list2):
    # process pairs
```

### List comprehension with conditions:

```python
evens = [x for x in numbers if x % 2 == 0]
squared = [x**2 for x in numbers]
```

### Slice and stride:

```python
every_other = lst[::2]
reversed_lst = lst[::-1]
last_three = lst[-3:]
```

### Zip with offset (sliding window):

```python
pairs = list(zip(lst, lst[1:]))  # consecutive pairs
triplets = list(zip(lst, lst[1:], lst[2:]))
```

### Grouping consecutive elements:

```python
from itertools import groupby
for key, group in groupby(lst):
    items = list(group)
    ```

---

## Set & Dictionary

### Deduplicate with set:

```python
unique = set(lst)
count = len(unique)
```

### Count occurrences:

```python
from collections import Counter
counts = Counter(lst)
most_common = counts.most_common(1)  # [(item, count)]
```

### Set operations:

```python
set1 = set(list1)
set2 = set(list2)
common = set1 & set2          # intersection
all_items = set1 | set2       # union
only_in_set1 = set1 - set2    # difference
symmetric = set1 ^ set2       # symmetric difference
```

### Dictionary get with default:

```python
value = d.get(key, default_value)
d.setdefault(key, []).append(item)
```

### Dictionary comprehension:

```python
d = {k: v for k, v in pairs}
d = {x: x**2 for x in range(10)}
```

---

## Math & Ranges

### Generate ranges:

```python
for i in range(10):           # 0 to 9
    pass
for i in range(0, 10, 2):     # step by 2
    pass
for i in range(10, 0, -1):    # reverse
    pass
    ```

### Sum and product:

```python
total = sum(lst)
from math import prod
product = prod(lst)
```

### Min/max with key:

```python
max_val = max(lst)
min_val = min(lst)
max_by_key = max(lst, key=lambda x: x['value'])
```

### GCD and LCM:

```python
from math import gcd
from functools import reduce
gcd_result = gcd(a, b)
lcm = lambda a, b: a * b // gcd(a, b)
result = reduce(lcm, numbers)
```

---

## Sorting

### Sort with key:

```python
sorted_lst = sorted(lst, key=lambda x: x['value'])
sorted_lst = sorted(lst, reverse=True)
lst.sort(key=str.lower)  # in-place
```

### Sort by multiple criteria:

```python
sorted_lst = sorted(lst, key=lambda x: (x[0], x[1]))
```

---

## defaultdict & OrderedDict

Auto-initialize missing keys:

```python
from collections import defaultdict
d = defaultdict(list)
d[key].append(value)  # no KeyError

### d = defaultdict(int)
d[key] += 1  # auto-initializes to 0
```

---

## Deque for Efficient Queue Operations

### Fast append/pop from both ends:

```python
from collections import deque
q = deque(lst)
q.append(item)      # O(1)
q.popleft()         # O(1) - faster than list
q.rotate(1)         # rotate by n
```

---

## Itertools - Powerful Combinations

### Permutations and combinations:

```python
from itertools import permutations, combinations
perms = list(permutations(lst))
combs = list(combinations(lst, 2))  # 2-element combos
```

### Product (Cartesian product):

```python
from itertools import product
for a, b in product(range(3), repeat=2):
    # all pairs: (0,0), (0,1), ..., (2,2)
```

### Chain multiple iterables:

```python
from itertools import chain
combined = list(chain(list1, list2, list3))
```

### Cycle through values:

```python
from itertools import cycle
for item in cycle([1, 2, 3]):  # infinite loop
    pass
```

---

## Bit Operations (for optimization)

### Bitwise tricks:

```python
x & (x - 1)              # Remove rightmost set bit
x | (x + 1)              # Set rightmost unset bit
bin(x).count('1')        # Count set bits
x.bit_length()           # Number of bits needed
```

---

## Pattern Matching & Unpacking

### Tuple unpacking:

```python
a, b = pair
x, *rest = lst  # first element and rest
a, b, c = lst   # unpack exactly 3
```

### Walrus operator (Python 3.8+):

```python
if (n := len(lst)) > 10:
    print(f"List has {n} items")
```

### File Input 

```python

from pathlib import Path
lines = Path('input.txt').read_lines()

with open('input.txt') as f:
    lines = f.read().strip().split('\n')

with open('input.txt') as f:
    for line in f:
        # process line
```
