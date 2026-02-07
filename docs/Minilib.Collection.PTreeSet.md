# Minilib.Collection.PTreeSet

Defined in minilib-collection@0.7.0-beta2

`PTreeSet` is a set that manages elements in sorted order.

The elements of a `PTreeSet` can be of type `I64`, `I32`, `I16`, `I8`, `U64`,
`U32`, `U16`, or `U8`. It's limited, but fast.

The order of elements is fixed to ascending order and cannot be changed to descending order.

`PTreeSet` implements the `Set` and `SortedSet` trait.
 If you import this module, you should also import `Minilib.Collection.Trait`.

`PTreeSet` manages elements as a node array.
If you modify the `PTreeSet`, make sure it is unique, otherwise the entire node array will be copied.

`PTreeSet` is built upon [a Patricia Tree](https://en.wikipedia.org/wiki/Radix_tree).
In particular, I implemented the Patricia Tree with reference to the following paper:
[Chris Okasaki and Andy Gill, "Fast Mergeable Integer Maps"](https://web.archive.org/web/20150417234429/https://ittc.ku.edu/~andygill/papers/IntMap98.pdf).

## Benchmark Result

```
test_perf (n=1000000)
 insert: 0.925837 seconds
 to_iter.to_array: 0.206471 seconds
 to_array: 0.101298 seconds
 erase: 0.955463 seconds
```

## Values

### namespace Minilib.Collection.PTreeSet

#### empty

Type: `[e : Minilib.Collection.PTreeSet::PTreeSetElem] Minilib.Collection.PTreeSet::PTreeSet e`

An empty PTreeSet.

## Types and aliases

### namespace Minilib.Collection.PTreeSet

#### PTreeSet

Defined as: `type PTreeSet e = unbox struct { ...fields... }`

The type of Patricia Tree Sets.

##### field `tree`

Type: `Minilib.Collection.Internal.PatTree::PTree ()`

The internal Patricia Tree.

## Traits and aliases

### namespace Minilib.Collection.PTreeSet

#### trait `e : PTreeSetElem`

The trait of elements of a PTreeSet.

##### method `_to_pattree_key`

Type: `e -> Std::U64`

Converts from `e` to an internal key.

##### method `_from_pattree_key`

Type: `Std::U64 -> e`

Converts from an internal key to `e`.

## Trait implementations

### impl `[e : Minilib.Collection.PTreeSet::PTreeSetElem] Minilib.Collection.PTreeSet::PTreeSet e : Minilib.Collection.Trait::Set`

### impl `[e : Minilib.Collection.PTreeSet::PTreeSetElem] Minilib.Collection.PTreeSet::PTreeSet e : Minilib.Collection.Trait::SortedSetIF`

### impl `Std::I16 : Minilib.Collection.PTreeSet::PTreeSetElem`

### impl `Std::I32 : Minilib.Collection.PTreeSet::PTreeSetElem`

### impl `Std::I64 : Minilib.Collection.PTreeSet::PTreeSetElem`

### impl `Std::I8 : Minilib.Collection.PTreeSet::PTreeSetElem`

### impl `Std::U16 : Minilib.Collection.PTreeSet::PTreeSetElem`

### impl `Std::U32 : Minilib.Collection.PTreeSet::PTreeSetElem`

### impl `Std::U64 : Minilib.Collection.PTreeSet::PTreeSetElem`

### impl `Std::U8 : Minilib.Collection.PTreeSet::PTreeSetElem`