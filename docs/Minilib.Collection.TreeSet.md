# Minilib.Collection.TreeSet

Defined in minilib-collection@0.7.0-beta2

TreeSet is a set that manages elements in sorted order.

`TreeSet` implements the `Set` and `SortedSet` trait.
 If you import this module, you should also import `Minilib.Collection.Trait`.

The elements of a TreeSet must have a partial order,
and `less_than` is the comparison function for that partial order.

NOTE: `less_than()` function must meet following conditions.

- Irreflexivity: for all `x`, `less_than(x,x)` must be false.
- Asymmetry:     for all `x, y`, if `less_than(x,y)` is true, then `less_than(y,x)` must be false.
- Transitivity:  for all `x, y, z`, if `less_than(x,y)` is true and `less_than(y,z)` is true,
                 then `less_than(x,z)` must be true.

If two elements `x` and `y` are incomparable, i.e. neither `less_than(x,y)` nor `less_than(y,x)` holds,
then `x` and `y` are considered equivalent.

## Benchmark Result

```
test_perf (n=1000000)
 insert: 2.683039 seconds
 to_iter.to_array: 0.919490 seconds
 to_array: 0.074071 seconds
 erase: 8.977304 seconds
```

## Values

### namespace Minilib.Collection.TreeSet::TreeSet

#### find_range

Type: `[a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] a -> a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Std::Iterator::DynIterator a`

Deprecated: use `select_range`.

`ts.find_range(begin, end)` finds all elements `x`
where `!less_than(x, begin) && less_than(x, end)` is true.
In default `LessThan` ordering, that condition is same as `begin <= x && x < end`.

##### Parameters

- `begin`: the beginning of range
- `end`: the end of range
- `ts`: a TreeSet

#### find_range_descending

Type: `[a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] a -> a -> Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Std::Iterator::DynIterator a`

Deprecated: use `select_range`.

`ts.find_range(begin, end)` finds all elements `x`
where `!less_than(x, begin) && less_than(x, end)` is true,  in descending order.
In default `LessThan` ordering, that condition is same as `begin <= x && x < end`.

##### Parameters

- `begin`: the beginning of range
- `end`: the end of range
- `ts`: a TreeSet

#### find_raw_range

Type: `[a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] (a -> Std::Bool) -> (a -> Std::Bool) -> Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Std::Iterator::DynIterator a`

`ts.find_raw_range(lt_begin, lt_end)` finds all elements `x`
where `!lt_begin(x) && lt_end(x)` is true.
NOTE: `lt_begin` and `lt_end` must meet following condition:
for all `x`, `x.lt_begin` is true then `x.lt_end` must be true.

##### Parameters

- `lt_begin`: a function that determines the beginning of range
- `lt_end`: a function that determines the end of range
- `ts`: a TreeSet

#### find_raw_range_descending

Type: `[a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] (a -> Std::Bool) -> (a -> Std::Bool) -> Minilib.Collection.TreeSet::TreeSet::TreeSet a -> Std::Iterator::DynIterator a`

`ts.find_raw_range_descending(lt_begin, lt_end)` finds all elements `elem`
such that `!lt_begin(x) && lt_end(x)` is true, in descending order.
NOTE: `lt_begin` and `lt_end` must meet following condition:
for all `x`, `x.lt_begin` is true then `x.lt_end` must be true.

##### Parameters

- `lt_begin`: a function that determines the beginning of range
- `lt_end`: a function that determines the end of range
- `ts`: a TreeSet

#### from_iter

Type: `[a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem, a : Std::LessThan, it : Std::Iterator, Std::Iterator::Item it = a] it -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

Converts an iterator into a TreeSet using default `LessThan` ordering.

##### Parameters

- `iter`: an iterator of elements

#### from_iter_lt

Type: `[a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem, it : Std::Iterator, Std::Iterator::Item it = a] (a -> a -> Std::Bool) -> it -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

Converts an iterator into a TreeSet using specified ordering.

##### Parameters

- `less_than`: a comparision function
- `iter`: an iterator of elements

#### make

Type: `[a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem, a : Std::LessThan] () -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

`TreeSet::make()` creates an empty `TreeSet` using default `LessThan` ordering.

#### make_lt

Type: `[a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] (a -> a -> Std::Bool) -> Minilib.Collection.TreeSet::TreeSet::TreeSet a`

`TreeSet::make_lt(less_than)` creates an empty `TreeSet` using specified ordering.

##### Parameters

- `less_than`: a comparision function

## Types and aliases

### namespace Minilib.Collection.TreeSet::TreeSet

#### TreeSet

Defined as: `type TreeSet a = unbox struct { ...fields... }`

A type of set that manages elements in sorted order.

##### field `root`

Type: `Minilib.Collection.Internal.RBTree::RBNode::RBNode a`

##### field `size`

Type: `Std::I64`

##### field `less_than`

Type: `a -> a -> Std::Bool`

## Traits and aliases

### namespace Minilib.Collection.TreeSet::TreeSet

#### trait `TreeSetElem = Std::ToString`

Kind: `*`

A trait of the element. Currently `ToString` is required.

## Trait implementations

### impl `[a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] Minilib.Collection.TreeSet::TreeSet::TreeSet a : Minilib.Collection.Trait::Set`

Implementation of the `Set` trait.

### impl `[a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] Minilib.Collection.TreeSet::TreeSet::TreeSet a : Minilib.Collection.Trait::SortedSetIF`

### impl `[a : Minilib.Collection.TreeSet::TreeSet::TreeSetElem] Minilib.Collection.TreeSet::TreeSet::TreeSet a : Std::ToString`

Converts a TreeSet into a String.