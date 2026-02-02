# Minilib.Collection.PTreeMap

Defined in minilib-collection@0.7.0-beta1

`PTreeMap` is a map that manages keys in sorted order.

The keys of a `PTreeMap` can be of type `I64`, `I32`, `I16`, `I8`, `U64`,
`U32`, `U16`, or `U8`. It's limited, but fast.

The order of keys is fixed to ascending order and cannot be changed to descending order.

`PTreeMap` implements the `Map` and `SortedMap` trait.
 If you import this module, you should also import `Minilib.Collection.Trait`.

`PTreeMap` manages entries as a node array.
If you modify the `PTreeMap`, make sure it is unique, otherwise the entire node array will be copied.

`PTreeMap` is built upon [a Patricia Tree](https://en.wikipedia.org/wiki/Radix_tree).
In particular, I implemented the Patricia Tree with reference to the following paper:
[Chris Okasaki and Andy Gill, "Fast Mergeable Integer Maps"](https://web.archive.org/web/20150417234429/https://ittc.ku.edu/~andygill/papers/IntMap98.pdf).

## Benchmark Result

```
test_perf (n=1000000)
 insert: 1.553386 seconds
 to_iter.to_array: 0.245620 seconds
 to_array: 0.128088 seconds
 erase: 1.188062 seconds
```

## Values

### namespace Minilib.Collection.PTreeMap

#### empty

Type: `[k : Minilib.Collection.PTreeMap::PTreeMapKey] Minilib.Collection.PTreeMap::PTreeMap k v`

An empty PTreeMap.

## Types and aliases

### namespace Minilib.Collection.PTreeMap

#### PTreeMap

Defined as: `type PTreeMap k v = unbox struct { ...fields... }`

The type of Patricia Tree Maps.

##### field `tree`

Type: `Minilib.Collection.Internal.PatTree::PTree v`

The internal Patricia Tree.

#### PTreeMapI64

Defined as: `type PTreeMapI64 = Minilib.Collection.PTreeMap::PTreeMap Std::I64`

The type of Patricia Tree Maps whose keys are of type `I64`.

#### PTreeMapU64

Defined as: `type PTreeMapU64 = Minilib.Collection.PTreeMap::PTreeMap Std::U64`

The type of Patricia Tree Maps whose keys are of type `U64`.

## Traits and aliases

### namespace Minilib.Collection.PTreeMap

#### trait `k : PTreeMapKey`

The trait of keys of a PTreeMap.

##### method `_to_pattree_key`

Type: `k -> Std::U64`

Converts from `k` to an internal key.

##### method `_from_pattree_key`

Type: `Std::U64 -> k`

Converts from an internal key to `k`.

## Trait implementations

### impl `[k : Minilib.Collection.PTreeMap::PTreeMapKey] Minilib.Collection.PTreeMap::PTreeMap k v : Minilib.Collection.Trait::Map`

### impl `[k : Minilib.Collection.PTreeMap::PTreeMapKey] Minilib.Collection.PTreeMap::PTreeMap k v : Minilib.Collection.Trait::SortedMapIF`

### impl `Std::I16 : Minilib.Collection.PTreeMap::PTreeMapKey`

### impl `Std::I32 : Minilib.Collection.PTreeMap::PTreeMapKey`

### impl `Std::I64 : Minilib.Collection.PTreeMap::PTreeMapKey`

### impl `Std::I8 : Minilib.Collection.PTreeMap::PTreeMapKey`

### impl `Std::U16 : Minilib.Collection.PTreeMap::PTreeMapKey`

### impl `Std::U32 : Minilib.Collection.PTreeMap::PTreeMapKey`

### impl `Std::U64 : Minilib.Collection.PTreeMap::PTreeMapKey`

### impl `Std::U8 : Minilib.Collection.PTreeMap::PTreeMapKey`