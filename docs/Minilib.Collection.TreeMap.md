# Minilib.Collection.TreeMap

Defined in minilib-collection@0.7.0-beta2

TreeMap is a map that manages keys in sorted order.

`TreeMap` implements the `Map` and `SortedMap` trait.
 If you import this module, you should also import `Minilib.Collection.Trait`.

The keys of a TreeMap must have a partial order,
and `less_than` is the comparison function for that partial order.

NOTE: `less_than()` function must meet following conditions.

- Irreflexivity: for all `x`, `less_than(x,x)` must be false.
- Asymmetry:     for all `x, y`, if `less_than(x,y)` is true, then `less_than(y,x)` must be false.
- Transitivity:  for all `x, y, z`, if `less_than(x,y)` is true and `less_than(y,z)` is true,
                 then `less_than(x,z)` must be true.

If two keys `x` and `y` are incomparable, i.e. neither `less_than(x,y)` nor `less_than(y,x)` holds,
then `x` and `y` are considered equivalent.

## Benchmark Result

```
test_perf (n=1000000)
 insert: 3.974124 seconds
 to_iter.to_array: 1.078280 seconds
 to_array: 0.099072 seconds
 erase: 9.535200 seconds
```

## Values

### namespace Minilib.Collection.TreeMap::TreeMap

#### find_range

Type: `[k : Minilib.Collection.TreeMap::TreeMap::TreeMapKey, v : Minilib.Collection.TreeMap::TreeMap::TreeMapValue] k -> k -> Minilib.Collection.TreeMap::TreeMap::TreeMap k v -> Std::Iterator::DynIterator (k, v)`

Deprecated: Use `select_range`.

`tm.find_range(begin, end)` finds all entries `(k,v)`
where `!less_than(k, begin) && less_than(k, end)` is true.
In default `LessThan` ordering, that condition is same as `begin <= k && k < end`.

#### find_raw_range

Type: `[k : Minilib.Collection.TreeMap::TreeMap::TreeMapKey, v : Minilib.Collection.TreeMap::TreeMap::TreeMapValue] ((k, v) -> Std::Bool) -> ((k, v) -> Std::Bool) -> Minilib.Collection.TreeMap::TreeMap::TreeMap k v -> Std::Iterator::DynIterator (k, v)`

`tm.find_raw_range(lt_begin, lt_end)` finds all entries `(k,v)`
where `!lt_begin((k, v)) && lt_end((k, v))` is true.
NOTE: `lt_begin` and `lt_end` must meet following condition:
for all `(k,v)`, `lt_begin((k,v))` is true then `lt_end((k,v))` must be true.

#### from_iter

Type: `[it : Std::Iterator, k : Minilib.Collection.TreeMap::TreeMap::TreeMapKey, k : Std::LessThan, v : Minilib.Collection.TreeMap::TreeMap::TreeMapValue, Std::Iterator::Item it = (k, v)] it -> Minilib.Collection.TreeMap::TreeMap::TreeMap k v`

Converts an iterator of key-value pairs into a TreeMap using default `LessThan` ordering.

#### from_iter_lt

Type: `[it : Std::Iterator, k : Minilib.Collection.TreeMap::TreeMap::TreeMapKey, v : Minilib.Collection.TreeMap::TreeMap::TreeMapValue, Std::Iterator::Item it = (k, v)] (k -> k -> Std::Bool) -> it -> Minilib.Collection.TreeMap::TreeMap::TreeMap k v`

Converts an iterator of key-value pairs into a TreeMap using specified ordering.

#### keys

Type: `[k : Minilib.Collection.TreeMap::TreeMap::TreeMapKey, v : Minilib.Collection.TreeMap::TreeMap::TreeMapValue] Minilib.Collection.TreeMap::TreeMap::TreeMap k v -> Std::Iterator::DynIterator k`

Returns an iterator of keys in ascending order.

#### make

Type: `[k : Minilib.Collection.TreeMap::TreeMap::TreeMapKey, k : Std::LessThan, v : Minilib.Collection.TreeMap::TreeMap::TreeMapValue] () -> Minilib.Collection.TreeMap::TreeMap::TreeMap k v`

`TreeMap::make()` creates an empty `TreeMap` using default `LessThan` ordering.

#### make_lt

Type: `[k : Minilib.Collection.TreeMap::TreeMap::TreeMapKey, v : Minilib.Collection.TreeMap::TreeMap::TreeMapValue] (k -> k -> Std::Bool) -> Minilib.Collection.TreeMap::TreeMap::TreeMap k v`

`TreeMap::make_lt(less_than)` creates an empty `TreeMap` using specified ordering.
NOTE: `less_than` function must meet specific conditions. For details, see documentation of
[`RBTree`](./rbtree.md).

#### upsert

Type: `[k : Minilib.Collection.TreeMap::TreeMap::TreeMapKey, v : Minilib.Collection.TreeMap::TreeMap::TreeMapValue] k -> v -> (v -> v) -> Minilib.Collection.TreeMap::TreeMap::TreeMap k v -> Minilib.Collection.TreeMap::TreeMap::TreeMap k v`

Inserts or updates an entry in a TreeMap.
For example, `tm.upsert(k, v, updater)` inserts an entry `(k,v)` into `tm`.

NOTE: If `tm` already contains an entry `(k1,v1)`
where the key `k1` is equivalent to `k`,
ie. `!less_than(k,k1) && !less_than(k1,k)` is true,
then `(k1,v1)` is replaced with `(k, updater(v1))`.

## Types and aliases

### namespace Minilib.Collection.TreeMap::TreeMap

#### TreeMap

Defined as: `type TreeMap k v = unbox struct { ...fields... }`

`TreeMap` is a structure that stores key-value pairs into a red-black tree.

##### field `root`

Type: `Minilib.Collection.Internal.RBTree::RBNode::RBNode (k, v)`

##### field `size`

Type: `Std::I64`

##### field `key_less_than`

Type: `k -> k -> Std::Bool`

##### field `entry_less_than`

Type: `(k, v) -> (k, v) -> Std::Bool`

## Traits and aliases

### namespace Minilib.Collection.TreeMap::TreeMap

#### trait `TreeMapKey = Std::ToString`

Kind: `*`

A trait of the key. Currently `ToString` is required.

#### trait `TreeMapValue = Std::ToString`

Kind: `*`

A trait of the value. Currently `ToString` is required.

## Trait implementations

### impl `[k : Minilib.Collection.TreeMap::TreeMap::TreeMapKey, v : Minilib.Collection.TreeMap::TreeMap::TreeMapValue] Minilib.Collection.TreeMap::TreeMap::TreeMap k v : Minilib.Collection.Trait::Map`

### impl `[k : Minilib.Collection.TreeMap::TreeMap::TreeMapKey, v : Minilib.Collection.TreeMap::TreeMap::TreeMapValue] Minilib.Collection.TreeMap::TreeMap::TreeMap k v : Minilib.Collection.Trait::SortedMapIF`

### impl `[k : Minilib.Collection.TreeMap::TreeMap::TreeMapKey, v : Minilib.Collection.TreeMap::TreeMap::TreeMapValue] Minilib.Collection.TreeMap::TreeMap::TreeMap k v : Std::ToString`