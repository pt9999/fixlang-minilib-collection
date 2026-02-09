# Minilib.Collection.TreapSet

Defined in minilib-collection@0.7.0

`TreapSet` is a set that manages elements in sorted order.

A treap is a randomized binary search tree.
The time complexity of a single search, insertion, or deletion is `O(log n)` with high probability.

The order of elements can be changed using a key comparator that implements the `KeyCompare` trait.

`TreapSet` implements the `Set` and `SortedSet` trait.
 If you import this module, you should also import `Minilib.Collection.Trait`.

`TreapSet` manages elements as a node array.
If you modify the `TreapSet`, make sure it is unique, otherwise the entire node array will be copied.

## Benchmark Result

```
test_perf (n=1000000)
 insert: 1.365991 seconds
 to_iter.to_array: 0.176191 seconds
 to_array: 0.216342 seconds
 erase: 1.040427 seconds
```

## Values

### namespace Minilib.Collection.TreapSet::TreapSet

#### empty

Type: `[kc : Minilib.Collection.Trait::KeyCompare, Minilib.Collection.Trait::KeyCompare::Key kc = k] Minilib.Collection.TreapSet::TreapSet kc k`

An empty TreapSet.

#### make

Type: `[kc : Minilib.Collection.Trait::KeyCompare, Minilib.Collection.Trait::KeyCompare::Key kc = k] kc -> Minilib.Collection.TreapSet::TreapSet kc k`

Makes an empty TreapSet.

##### Parameters

##### - `kc`: a key comparator

## Types and aliases

### namespace Minilib.Collection.TreapSet

#### TreapSet

Defined as: `type TreapSet kc k = box struct { ...fields... }`

The type of TreapSet.

##### field `map`

Type: `Minilib.Collection.TreapMap::TreapMap kc k ()`

## Traits and aliases

## Trait implementations

### impl `[kc : Minilib.Collection.Trait::KeyCompare] Minilib.Collection.TreapSet::TreapSet kc k : Minilib.Collection.Trait::Set`

Implementation of the `Set` trait.

### impl `[kc : Minilib.Collection.Trait::KeyCompare] Minilib.Collection.TreapSet::TreapSet kc k : Minilib.Collection.Trait::SortedSetIF`

Implementation of the `SortedSetIF` trait.