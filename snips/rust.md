# Snippets

```rust
use std::collections::{
    HashMap, HashSet,  // tracking seen states, counts, graph edges, etc.
    VecDeque,          // BFS queues
    BTreeMap, BTreeSet // sorted maps/sets (useful for interval queries).
    BinaryHeap // max heap priority queue, std::cmp::Reverse for min heap
};
use std::cmp::{min, max}; // simple min/max usage.
use std::iter::FromIterator;
use std::fs;  // fs::read_to_string – reading input files quickly.
```


## String & Parsing

### Split and collect into collections:

```rust
let nums: Vec<i32> = "1,2,3".split(',').map(|s| s.parse().unwrap()).collect();
let words: Vec<&str> = "hello world".split_whitespace().collect();
```

### Character iteration and filtering:

```rust
let digits: String = input.chars().filter(|c| c.is_numeric()).collect();
let uppercase: String = input.chars().map(|c| c.to_uppercase().to_string()).collect();
```

### Lines and trim:

```rust
for line in input.lines() {
    let trimmed = line.trim();
}
```

---

## Collections & Iteration

### Enumerate with index:

```rust
for (i, item) in vec.iter().enumerate() {
    println!("{}: {}", i, item);
}
```

### Zip two iterators:

```rust
for (a, b) in vec1.iter().zip(vec2.iter()) {
    // process pairs
}
```
### Partition into two groups:

```rust
let (evens, odds): (Vec<_>, Vec<_>) = numbers.into_iter().partition(|n| n % 2 == 0);
```

### Group consecutive elements:

```rust
for window in vec.windows(2) {
    let (a, b) = (window[0], window[1]);
}
```

### Chunk iterator (nightly) or manual chunking:

```rust
for chunk in vec.chunks(3) {
    // process 3-element chunks
}
```

---

## HashSet & HashMap

### Deduplicate with HashSet:

```rust
let unique: HashSet<_> = vec.into_iter().collect();
let count = unique.len();
```

### Count occurrences:

```rust
use std::collections::HashMap;
let mut counts = HashMap::new();
for item in vec {
    *counts.entry(item).or_insert(0) += 1;
}
```

### Find intersection/difference:

```rust
let set1: HashSet<_> = vec1.into_iter().collect();
let set2: HashSet<_> = vec2.into_iter().collect();
let common: HashSet<_> = set1.intersection(&set2).cloned().collect();
```

---

## Math & Ranges

### Generate ranges:

```rust
for i in 0..10 { }          // 0 to 9
for i in 0..=10 { }         // 0 to 10 inclusive
for i in (0..10).rev() { }  // reverse
```

### Sum and product:

```rust
let sum: i32 = vec.iter().sum();
let product: i32 = vec.iter().product();
```

### Min/max:

```rust
let max = vec.iter().max().unwrap();
let min = vec.iter().min().unwrap();
```

### GCD/LCM (not in std, but common pattern):

```rust
fn gcd(mut a: u64, mut b: u64) -> u64 {
    while b != 0 {
        let temp = b;
        b = a % b;
        a = temp;
    }
    a
}
```

---

## Sorting & Ordering

### Sort with custom logic:

```rust
vec.sort_by_key(|x| x.value);
vec.sort_by(|a, b| a.cmp(b).reverse());  // descending
```

### Unique/dedup:

```rust
vec.sort();
vec.dedup();
```

---

## BTreeMap for Ordered Keys

### Maintain sorted order automatically:

```rust
use std::collections::BTreeMap;
let mut map = BTreeMap::new();
for item in vec {
    map.insert(item, count);
}
// Iterate in sorted order
for (key, value) in map.iter() { }
```

---

## Pattern Matching & Unwrapping

### Safe unwrapping:

```rust
match option {
    Some(val) => println!("{}", val),
    None => println!("Not found"),
}
if let Some(val) = option {
    println!("{}", val);
}

### Unwrap with default:

```rust
let val = option.unwrap_or(0);
let val = option.unwrap_or_else(|| expensive_default());
```

---

## Bit Operations (for optimization challenges)

### Bitwise tricks:

```rust
x & (x - 1)              // Remove rightmost set bit
x | (x + 1)              // Set rightmost unset bit
(x ^ (x - 1)) >> 1       // Isolate rightmost set bit
x.count_ones()           // Count set bits
```

---

## Regex

### Quick pattern matching:

```rust
use regex::Regex;
let re = Regex::new(r"\d+").unwrap();
for cap in re.captures_iter(input) {
    let num: i32 = cap[0].parse().unwrap();
}
```
