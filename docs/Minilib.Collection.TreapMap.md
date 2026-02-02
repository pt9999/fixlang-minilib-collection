# Minilib.Collection.TreapMap

Defined in minilib-collection@0.7.0-beta1

`TreapMap` is a map that manages keys in sorted order.

A treap is a randomized binary search tree.
The time complexity of a single search, insertion, or deletion is `O(log n)` with high probability.

The order of keys can be changed using a key comparator that implements the `KeyCompare` trait.

`TreapMap` implements the `Map` and `SortedMap` trait.
 If you import this module, you should also import `Minilib.Collection.Trait`.

`TreapMap` manages entries as a node array.
If you modify the `TreapMap`, make sure it is unique, otherwise the entire node array will be copied.

## Benchmark Result

```
test_perf (n=1000000)
 insert: 2.024756 seconds
 to_iter.to_array: 0.224507 seconds
 to_array: 0.259296 seconds
 erase: 1.731516 seconds
```

## Values

### namespace Minilib.Collection.TreapMap::TNodeIndex

#### empty

Type: `Minilib.Collection.TreapMap::TNodeIndex`

A special index which represents an empty node.

### namespace Minilib.Collection.TreapMap::TreapMap

#### empty

Type: `[kc : Minilib.Collection.Trait::KeyCompare, Minilib.Collection.Trait::KeyCompare::Key kc = k] Minilib.Collection.TreapMap::TreapMap kc k v`

An empty TreapMap.

#### from_iter

Type: `[i : Std::Iterator, k : Std::LessThan, Std::Iterator::Item i = (k, v)] i -> Minilib.Collection.TreapMap::TreapMap (Minilib.Collection.Trait::KeyLessThan k) k v`

Converts an iterator to a TreapMap.

#### from_iter_kc

Type: `[i : Std::Iterator, kc : Minilib.Collection.Trait::KeyCompare, Minilib.Collection.Trait::KeyCompare::Key kc = k, Std::Iterator::Item i = (k, v)] kc -> i -> Minilib.Collection.TreapMap::TreapMap kc k v`

Converts an iterator to a TreapMap.

#### from_iter_kc_non_optimized

Type: `[i : Std::Iterator, kc : Minilib.Collection.Trait::KeyCompare, Minilib.Collection.Trait::KeyCompare::Key kc = k, Std::Iterator::Item i = (k, v)] kc -> i -> Minilib.Collection.TreapMap::TreapMap kc k v`

#### make

Type: `[kc : Minilib.Collection.Trait::KeyCompare, Minilib.Collection.Trait::KeyCompare::Key kc = k] kc -> Minilib.Collection.TreapMap::TreapMap kc k v`

Makes an empty TreapMap.

##### Parameters

##### - `kc`: a key comparator

## Types and aliases

### namespace Minilib.Collection.TreapMap

#### Priority

Defined as: `type Priority = Std::U64`

(used internally) The priority type.

#### TNode

Defined as: `type TNode k v = unbox struct { ...fields... }`

(used internally) The type of treap nodes.

##### field `prio`

Type: `Minilib.Collection.TreapMap::Priority`

##### field `key`

Type: `k`

##### field `value`

Type: `v`

##### field `left`

Type: `Minilib.Collection.TreapMap::TNodeIndex`

##### field `right`

Type: `Minilib.Collection.TreapMap::TNodeIndex`

#### TNodeIndex

Defined as: `type TNodeIndex = Std::I64`

(used internally) The type of index of the node array.

#### TreapMap

Defined as: `type TreapMap kc k v = box struct { ...fields... }`

The type of TreapMap.

##### field `root`

Type: `Minilib.Collection.TreapMap::TNodeIndex`

The root node.

##### field `kc`

Type: `kc`

The key comparator.

##### field `size`

Type: `Std::I64`

The number of elements.

##### field `seed`

Type: `Minilib.Collection.TreapMap::Priority`

The random seed.

##### field `nodes`

Type: `Std::Array (Std::Option (Minilib.Collection.TreapMap::TNode k v))`

The array of nodes.

##### field `freelist`

Type: `Std::Array Minilib.Collection.TreapMap::TNodeIndex`

The free list.

### namespace Minilib.Collection.TreapMap::TreapMap

#### TreapMapIterator

Defined as: `type TreapMapIterator kc k v = unbox struct { ...fields... }`

Type type of iterators which are returned by `to_iter`, `select_range`.

##### field `treap`

Type: `Minilib.Collection.TreapMap::TreapMap kc k v`

##### field `lower_bound`

Type: `Minilib.Collection.Trait::Bound k`

##### field `upper_bound`

Type: `Minilib.Collection.Trait::Bound k`

##### field `ascending`

Type: `Std::Bool`

##### field `stack`

Type: `Std::Array (Std::Result Minilib.Collection.TreapMap::TNodeIndex (k, v))`

## Traits and aliases

## Trait implementations

### impl `[kc : Minilib.Collection.Trait::KeyCompare] Minilib.Collection.TreapMap::TreapMap kc k v : Minilib.Collection.Trait::Map`

Implementation of the `Map` trait.

### impl `[kc : Minilib.Collection.Trait::KeyCompare] Minilib.Collection.TreapMap::TreapMap kc k v : Minilib.Collection.Trait::SortedMapIF`

Implementation of the `SortedMapIF` trait.

### impl `Minilib.Collection.TreapMap::TreapMap kc k v : Std::Indexable`

### impl `[kc : Minilib.Collection.Trait::KeyCompare] Minilib.Collection.TreapMap::TreapMap::TreapMapIterator kc k v : Std::Iterator`