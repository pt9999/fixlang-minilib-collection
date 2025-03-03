# `module Minilib.Collection.TreeSet`

TreeSet is a set that manages elements in sorted order.

# Types and aliases

## `namespace Minilib.Collection.TreeSet::TreeSet`

### `type TreeSet a = unbox struct { ...fields... }`

A type of set that manages elements in sorted order.

#### field `root : Minilib.Collection.RBTree::RBNode::RBNode a`

#### field `less_than : a -> a -> Std::Bool`

# Traits and aliases

# Trait implementations

### `impl [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] Minilib.Collection.TreeSet::TreeSet::TreeSet a : Std::ToString`

Converts a TreeSet into a String.

# Values

## `namespace Minilib.Collection.TreeSet::TreeSet`

### `contains : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Std::Bool`

Checks whether a TreeSet contains an element.

### `erase : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

Erases an element from a TreeSet.
For example, `ts.erase(x)` removes `x` from `ts`.

NOTE: If `ts` contains an element `y` equivalent to `x`,
ie. `!less_than(x,y) && !less_than(y,x)` is true,
then `y` is removed.

### `find_range : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] a -> a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Std::Iterator::DynIterator a`

`ts.find_range(begin, end)` finds all elements `x`
where `!less_than(x, begin) && less_than(x, end)` is true.
In default `LessThan` ordering, that condition is same as `begin <= x && x < end`.

### `find_raw_range : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] (a -> Std::Bool) -> (a -> Std::Bool) -> Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Std::Iterator::DynIterator a`

`ts.find_raw_range(lt_begin, lt_end)` finds all elements `x`
where `!lt_begin(x) && lt_end(x)` is true.
NOTE: `lt_begin` and `lt_end` must meet following condition:
for all `x`, `x.lt_begin` is true then `x.lt_end` must be true.

### `from_iter : [a : Std::LessThan, a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem, it : Std::Iterator, Std::Iterator::Item it = a] it -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

Converts an iterator into a TreeSet using default `LessThan` ordering.

### `from_iter_lt : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem, it : Std::Iterator, Std::Iterator::Item it = a] (a -> a -> Std::Bool) -> it -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

Converts an iterator into a TreeSet using specified ordering.

### `get_size : Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Std::I64`

Gets the number of elements.

### `insert : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

Inserts an element into a TreeSet.
For example, `ts.insert(x)` inserts `x` into `ts`.

NOTE: If `ts` already contains an element `y` equivalent to `x`,
ie. `!less_than(x,y) && !less_than(y,x)` is true,
then `y` is replaced with `x`.

### `intersect : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

Calculates intersection of two TreeSets.

### `is_empty : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Std::Bool`

Checks whether a TreeSet is empty.

### `make : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem, a : Std::LessThan] () -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

`TreeSet::make()` creates an empty `TreeSet` using default `LessThan` ordering.

### `make_lt : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] (a -> a -> Std::Bool) -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

`TreeSet::make_lt(less_than)` creates an empty `TreeSet` using specified ordering.
NOTE: `less_than` function must meet specific conditions. For details, see documentation of
[`RBTree`](./rbtree.md).

### `merge : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

Calculates union of two TreeSets.

### `to_array : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Std::Array a`

Converts a TreeSet into an array in sorted order.

### `to_iter : [a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Std::Iterator::DynIterator a`

Converts a TreeSet into an iterator in sorted order.