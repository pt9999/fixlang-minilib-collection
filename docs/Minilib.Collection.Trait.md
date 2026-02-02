# Minilib.Collection.Trait

Defined in minilib-collection@0.7.0-beta1

Trait definitions, default implementations of traits, and common type definitions for `Minilib.Collection.*`.

The following traits are defined in this module.
- `Set`: Abstract sets.
- `SortedSet`: Sorted sets.
- `Map`: Abstract maps.
- `SortedMap`: Sorted maps.
- `KeyCompare`: Key comparators.

Some trait methods have default implementations defined in `{trait-name}::Default` namespaces.

The following types are defined in this module.
- `Bound`: A bound of a range, used in `SortedMap` and `SortedSet`.
- `KeyLessThan`: Key comparators which compares keys with `LessThan::less_than`.
- `KeyGreaterThan`: Key comparators which compares keys with `LessThan::less_than` in reversed order.
- `KeyCompareWithFunc`: Key comparators which uses a function.

## Values

### namespace Minilib.Collection.Trait::KeyCompare

#### above_lower_bound

Type: `[kc : Minilib.Collection.Trait::KeyCompare, Minilib.Collection.Trait::KeyCompare::Key kc = k] Minilib.Collection.Trait::Bound k -> k -> kc -> Std::Bool`

Checks if the key is above the lower bound.

##### Parameters

- `lower_bound`: a lower bound.
- `key`: a key.
- `kc`: a key comparator.

#### below_upper_bound

Type: `[kc : Minilib.Collection.Trait::KeyCompare, Minilib.Collection.Trait::KeyCompare::Key kc = k] Minilib.Collection.Trait::Bound k -> k -> kc -> Std::Bool`

Checks if the key is below the uppwer bound.

##### Parameters

- `upper_bound`: a upper bound.
- `key`: a key.
- `kc`: a key comparator.

#### compare

Type: `[kc : Minilib.Collection.Trait::KeyCompare] Minilib.Collection.Trait::KeyCompare::Key kc -> Minilib.Collection.Trait::KeyCompare::Key kc -> kc -> Std::Bool`

Returns false if and only if the first key should appear after the second key.

#### empty

Type: `[kc : Minilib.Collection.Trait::KeyCompare] kc`

An empty key comparator.

### namespace Minilib.Collection.Trait::KeyCompareWithFunc

#### make

Type: `(k -> k -> Std::Bool) -> Minilib.Collection.Trait::KeyCompareWithFunc k`

Creates a key comparator using the specified function.

##### Parameters

- `compare`: a comparator function

### namespace Minilib.Collection.Trait::Map

#### act

Type: `[f : Std::Functor, map : Minilib.Collection.Trait::Map] Minilib.Collection.Trait::Map::MapKey map -> (Std::Option (Minilib.Collection.Trait::Map::MapValue map) -> f (Std::Option (Minilib.Collection.Trait::Map::MapValue map))) -> map -> f map`

Modifies a map by a functorial action.

Semantically, `map.act(key, fun)` is equivalent to
`fun(map.find(key)).Functor::map(|opt_v| map.set(key, opt_v))`.

`action` is a function which takes an `Option v` as an argument and returns an `f (Option v)`,
 where `v` is equal to `MapValue map`.
 The argument of `action` is `some(old_value)` if there is an entry for the specified key, `none()` if there is no entry.
 `action` should return a lifted value for `f` of `some(new_value)`
  if you want to keep the entry (with or without changing the value),
  or return a lifted value for `f` of `none()` if you want to remove the entry.

##### Parameters

- `key`: A key
- `action`: The functorial action to be performed on the value for the key `key`.
- `map`: A map

#### contains_key

Type: `[map : Minilib.Collection.Trait::Map] Minilib.Collection.Trait::Map::MapKey map -> map -> Std::Bool`

Checks whether any entry exists whose key is equivalent to the specified key.

##### Parameters

- `key`: a key
- `map`: a map

#### erase

Type: `[map : Minilib.Collection.Trait::Map] Minilib.Collection.Trait::Map::MapKey map -> map -> map`

Erases all entries whose key is equivalent to the specified key.

##### Parameters

- `key`: a key
- `map`: a map

#### find

Type: `[map : Minilib.Collection.Trait::Map] Minilib.Collection.Trait::Map::MapKey map -> map -> Std::Option (Minilib.Collection.Trait::Map::MapValue map)`

Finds an entry whose key is equivalent to the specified key.
If an entry is found, returns `some(v)` where `v` is the value.
If no entry is found, returns `none()`.

##### Parameters

- `key`: a key
- `map`: a map

#### get_size

Type: `[map : Minilib.Collection.Trait::Map] map -> Std::I64`

Gets the number of entries in a map.

##### Parameters

- `map`: a map

#### insert

Type: `[map : Minilib.Collection.Trait::Map] (Minilib.Collection.Trait::Map::MapKey map, Minilib.Collection.Trait::Map::MapValue map) -> map -> map`

Inserts an entry into a map.

##### Parameters

- `key_value`: a key-value pair
- `map`: a map

#### is_empty

Type: `[map : Minilib.Collection.Trait::Map] map -> Std::Bool`

Checks whether a map is empty.

##### Parameters

- `map`: a map

#### set

Type: `[map : Minilib.Collection.Trait::Map] Minilib.Collection.Trait::Map::MapKey map -> Std::Option (Minilib.Collection.Trait::Map::MapValue map) -> map -> map`

Inserts an entry to a map, or erases an entry from a map.

Semantically, `map.set(key, opt_v)` is equivalent to
`match opt_v { some(v) => map.insert(key, v), none() => map.erase(key) }`.

##### Parameters

- `key`: A key
- `opt_value`: If `some(v)`, an element is inserted. if `none()`, any element for `key` is erased.
- `map`: A map

#### to_array

Type: `[map : Minilib.Collection.Trait::Map] map -> Std::Array (Minilib.Collection.Trait::Map::MapKey map, Minilib.Collection.Trait::Map::MapValue map)`

Converts a map into an array of entries.

##### Parameters

- `map`: a map

#### to_iter

Type: `[map : Minilib.Collection.Trait::Map] map -> Minilib.Collection.Trait::Map::MapIterator map`

Converts a map into an iterator of entries.

##### Parameters

- `map`: a map

### namespace Minilib.Collection.Trait::Map::Default

#### default_act

Type: `[f : Std::Functor, map : Minilib.Collection.Trait::Map] Minilib.Collection.Trait::Map::MapKey map -> (Std::Option (Minilib.Collection.Trait::Map::MapValue map) -> f (Std::Option (Minilib.Collection.Trait::Map::MapValue map))) -> map -> f map`

Default implementation of `Map::act`.

#### default_set

Type: `[map : Minilib.Collection.Trait::Map] Minilib.Collection.Trait::Map::MapKey map -> Std::Option (Minilib.Collection.Trait::Map::MapValue map) -> map -> map`

Default implementation of `Map::set`.

### namespace Minilib.Collection.Trait::Set

#### contains

Type: `[set : Minilib.Collection.Trait::Set] Minilib.Collection.Trait::Set::SetElem set -> set -> Std::Bool`

Checks whether a set contains the specified element.

##### Parameters

- `elem`: a element
- `set`: a set

#### erase

Type: `[set : Minilib.Collection.Trait::Set] Minilib.Collection.Trait::Set::SetElem set -> set -> set`

Erases all elements which is equivalent to the specified element.

##### Parameters

- `elem`: a element
- `set`: a set

#### get_size

Type: `[set : Minilib.Collection.Trait::Set] set -> Std::I64`

Gets the number of elements in a set.

##### Parameters

- `set`: a set

#### insert

Type: `[set : Minilib.Collection.Trait::Set] Minilib.Collection.Trait::Set::SetElem set -> set -> set`

Inserts an element into a set.

##### Parameters

- `elem`: a element
- `set`: a set

#### is_empty

Type: `[set : Minilib.Collection.Trait::Set] set -> Std::Bool`

Checks whether a set is empty.

##### Parameters

- `set`: a set

#### to_array

Type: `[set : Minilib.Collection.Trait::Set] set -> Std::Array (Minilib.Collection.Trait::Set::SetElem set)`

Converts a set into an array.

##### Parameters

- `set`: a set

#### to_iter

Type: `[set : Minilib.Collection.Trait::Set] set -> Minilib.Collection.Trait::Set::SetIterator set`

Converts a set into an iterator.

##### Parameters

- `set`: a set

### namespace Minilib.Collection.Trait::SortedMapIF

#### select_range

Type: `[map : Minilib.Collection.Trait::SortedMapIF] Minilib.Collection.Trait::Bound (Minilib.Collection.Trait::Map::MapKey map) -> Minilib.Collection.Trait::Bound (Minilib.Collection.Trait::Map::MapKey map) -> Std::Bool -> map -> Minilib.Collection.Trait::Map::MapIterator map`

Finds all entries in the specified range.

##### Parameters

- `lower_bound`: the lower bound of the range
- `upper_bound`: the upper bound of the range
- `ascending`: order of entries (true: ascending, false: descending)
- `map`: a map

Example:
```
map.select_range(included(5), excluded(10), true)    // finds all entries where 5 <= key < 10 in ascending order
map.select_range(excluded(5), included(10), false)   // finds all entries where 5 < key <= 10 in descending order
map.select_range(unbound(), excluded(10), true)    // finds all entries where key < 10 in ascending order
map.select_range(included(5), unbound(), true)    // finds all entries where 5 <= key in ascending order
map.select_range(unbound(), unbound(), true)    // finds all entries in ascending order
```

### namespace Minilib.Collection.Trait::SortedSetIF

#### select_range

Type: `[set : Minilib.Collection.Trait::SortedSetIF] Minilib.Collection.Trait::Bound (Minilib.Collection.Trait::Set::SetElem set) -> Minilib.Collection.Trait::Bound (Minilib.Collection.Trait::Set::SetElem set) -> Std::Bool -> set -> Minilib.Collection.Trait::Set::SetIterator set`

Finds all elements in the specified range.

##### Parameters

- `lower_bound`: the lower bound of the range
- `upper_bound`: the upper bound of the range
- `ascending`: order of elements (true: ascending, false: descending)
- `set`: a set

Example:
```
set.select_range(included(5), excluded(10), true)    // finds all elements where 5 <= key < 10 in ascending order
set.select_range(excluded(5), included(10), false)   // finds all elements where 5 < key <= 10 in descending order
set.select_range(unbound(), excluded(10), true)    // finds all elements where key < 10 in ascending order
set.select_range(included(5), unbound(), true)    // finds all elements where 5 <= key in ascending order
set.select_range(unbound(), unbound(), true)    // finds all elements in ascending order
```

## Types and aliases

### namespace Minilib.Collection.Trait

#### Bound

Defined as: `type Bound a = unbox union { ...variants... }`

A bound of a range, used in `SortedMap` and `SortedSet`.

##### variant `included`

Type: `a`

The bound is included

##### variant `excluded`

Type: `a`

The bound is excluded

##### variant `unbound`

Type: `()`

Unbound

#### KeyCompareWithFunc

Defined as: `type KeyCompareWithFunc k = unbox struct { ...fields... }`

The type of key comparators which uses a function.

The implementation of this type for `KeyCompare::empty` is a dummy; do not use it.

##### field `compare`

Type: `k -> k -> Std::Bool`

#### KeyGreaterThan

Defined as: `type KeyGreaterThan k = unbox struct { ...fields... }`

The type of key comparators which compares keys with `LessThan::less_than` in reversed order.

#### KeyLessThan

Defined as: `type KeyLessThan k = unbox struct { ...fields... }`

The type of key comparators which compares keys with `LessThan::less_than`.

## Traits and aliases

### namespace Minilib.Collection.Trait

#### trait `kc : KeyCompare`

The trait of key comparators.

##### type `Key`

Defined as: `Key kc`

The type of keys.

##### method `empty`

Type: `kc`

An empty key comparator.

##### method `compare`

Type: `Minilib.Collection.Trait::KeyCompare::Key kc -> Minilib.Collection.Trait::KeyCompare::Key kc -> kc -> Std::Bool`

Returns false if and only if the first key should appear after the second key.

#### trait `map : Map`

The trait for abstract maps.

##### type `MapValue`

Defined as: `MapValue map`

The type of the values.

##### type `MapKey`

Defined as: `MapKey map`

The type of the keys.

##### type `MapIterator`

Defined as: `MapIterator map`

The type of the iterator returned by `to_iter` and `SortedMapIF::select_range`.
`Item (MapIterator map)` should be equal to `(MapKey map, MapValue map)`.

##### method `is_empty`

Type: `map -> Std::Bool`

Checks whether a map is empty.

###### Parameters

- `map`: a map

##### method `get_size`

Type: `map -> Std::I64`

Gets the number of entries in a map.

###### Parameters

- `map`: a map

##### method `contains_key`

Type: `Minilib.Collection.Trait::Map::MapKey map -> map -> Std::Bool`

Checks whether any entry exists whose key is equivalent to the specified key.

###### Parameters

- `key`: a key
- `map`: a map

##### method `find`

Type: `Minilib.Collection.Trait::Map::MapKey map -> map -> Std::Option (Minilib.Collection.Trait::Map::MapValue map)`

Finds an entry whose key is equivalent to the specified key.
If an entry is found, returns `some(v)` where `v` is the value.
If no entry is found, returns `none()`.

###### Parameters

- `key`: a key
- `map`: a map

##### method `insert`

Type: `(Minilib.Collection.Trait::Map::MapKey map, Minilib.Collection.Trait::Map::MapValue map) -> map -> map`

Inserts an entry into a map.

###### Parameters

- `key_value`: a key-value pair
- `map`: a map

##### method `erase`

Type: `Minilib.Collection.Trait::Map::MapKey map -> map -> map`

Erases all entries whose key is equivalent to the specified key.

###### Parameters

- `key`: a key
- `map`: a map

##### method `set`

Type: `Minilib.Collection.Trait::Map::MapKey map -> Std::Option (Minilib.Collection.Trait::Map::MapValue map) -> map -> map`

Inserts an entry to a map, or erases an entry from a map.

Semantically, `map.set(key, opt_v)` is equivalent to
`match opt_v { some(v) => map.insert(key, v), none() => map.erase(key) }`.

###### Parameters

- `key`: A key
- `opt_value`: If `some(v)`, an element is inserted. if `none()`, any element for `key` is erased.
- `map`: A map

##### method `act`

Type: `[f : Std::Functor] Minilib.Collection.Trait::Map::MapKey map -> (Std::Option (Minilib.Collection.Trait::Map::MapValue map) -> f (Std::Option (Minilib.Collection.Trait::Map::MapValue map))) -> map -> f map`

Modifies a map by a functorial action.

Semantically, `map.act(key, fun)` is equivalent to
`fun(map.find(key)).Functor::map(|opt_v| map.set(key, opt_v))`.

`action` is a function which takes an `Option v` as an argument and returns an `f (Option v)`,
 where `v` is equal to `MapValue map`.
 The argument of `action` is `some(old_value)` if there is an entry for the specified key, `none()` if there is no entry.
 `action` should return a lifted value for `f` of `some(new_value)`
  if you want to keep the entry (with or without changing the value),
  or return a lifted value for `f` of `none()` if you want to remove the entry.

###### Parameters

- `key`: A key
- `action`: The functorial action to be performed on the value for the key `key`.
- `map`: A map

##### method `to_iter`

Type: `map -> Minilib.Collection.Trait::Map::MapIterator map`

Converts a map into an iterator of entries.

###### Parameters

- `map`: a map

##### method `to_array`

Type: `map -> Std::Array (Minilib.Collection.Trait::Map::MapKey map, Minilib.Collection.Trait::Map::MapValue map)`

Converts a map into an array of entries.

###### Parameters

- `map`: a map

#### trait `set : Set`

The trait for abstract sets.

##### type `SetElem`

Defined as: `SetElem set`

The type of the elements.

##### type `SetIterator`

Defined as: `SetIterator set`

The type of the iterator returned by `to_iter` and `SortedSetIF::select_range`.
`Item (SetIterator set)` should be equal to `SetElem set`.

##### method `is_empty`

Type: `set -> Std::Bool`

Checks whether a set is empty.

###### Parameters

- `set`: a set

##### method `get_size`

Type: `set -> Std::I64`

Gets the number of elements in a set.

###### Parameters

- `set`: a set

##### method `contains`

Type: `Minilib.Collection.Trait::Set::SetElem set -> set -> Std::Bool`

Checks whether a set contains the specified element.

###### Parameters

- `elem`: a element
- `set`: a set

##### method `insert`

Type: `Minilib.Collection.Trait::Set::SetElem set -> set -> set`

Inserts an element into a set.

###### Parameters

- `elem`: a element
- `set`: a set

##### method `erase`

Type: `Minilib.Collection.Trait::Set::SetElem set -> set -> set`

Erases all elements which is equivalent to the specified element.

###### Parameters

- `elem`: a element
- `set`: a set

##### method `to_iter`

Type: `set -> Minilib.Collection.Trait::Set::SetIterator set`

Converts a set into an iterator.

###### Parameters

- `set`: a set

##### method `to_array`

Type: `set -> Std::Array (Minilib.Collection.Trait::Set::SetElem set)`

Converts a set into an array.

###### Parameters

- `set`: a set

#### trait `SortedMap = Minilib.Collection.Trait::Map + Minilib.Collection.Trait::SortedMapIF`

Kind: `*`

The trait for sorted maps.

#### trait `map : SortedMapIF`

The interface for sorted maps.

##### method `select_range`

Type: `Minilib.Collection.Trait::Bound (Minilib.Collection.Trait::Map::MapKey map) -> Minilib.Collection.Trait::Bound (Minilib.Collection.Trait::Map::MapKey map) -> Std::Bool -> map -> Minilib.Collection.Trait::Map::MapIterator map`

Finds all entries in the specified range.

###### Parameters

- `lower_bound`: the lower bound of the range
- `upper_bound`: the upper bound of the range
- `ascending`: order of entries (true: ascending, false: descending)
- `map`: a map

Example:
```
map.select_range(included(5), excluded(10), true)    // finds all entries where 5 <= key < 10 in ascending order
map.select_range(excluded(5), included(10), false)   // finds all entries where 5 < key <= 10 in descending order
map.select_range(unbound(), excluded(10), true)    // finds all entries where key < 10 in ascending order
map.select_range(included(5), unbound(), true)    // finds all entries where 5 <= key in ascending order
map.select_range(unbound(), unbound(), true)    // finds all entries in ascending order
```

#### trait `SortedSet = Minilib.Collection.Trait::Set + Minilib.Collection.Trait::SortedSetIF`

Kind: `*`

The trait for sorted sets.

#### trait `set : SortedSetIF`

The interface for sorted sets.

##### method `select_range`

Type: `Minilib.Collection.Trait::Bound (Minilib.Collection.Trait::Set::SetElem set) -> Minilib.Collection.Trait::Bound (Minilib.Collection.Trait::Set::SetElem set) -> Std::Bool -> set -> Minilib.Collection.Trait::Set::SetIterator set`

Finds all elements in the specified range.

###### Parameters

- `lower_bound`: the lower bound of the range
- `upper_bound`: the upper bound of the range
- `ascending`: order of elements (true: ascending, false: descending)
- `set`: a set

Example:
```
set.select_range(included(5), excluded(10), true)    // finds all elements where 5 <= key < 10 in ascending order
set.select_range(excluded(5), included(10), false)   // finds all elements where 5 < key <= 10 in descending order
set.select_range(unbound(), excluded(10), true)    // finds all elements where key < 10 in ascending order
set.select_range(included(5), unbound(), true)    // finds all elements where 5 <= key in ascending order
set.select_range(unbound(), unbound(), true)    // finds all elements in ascending order
```

## Trait implementations

### impl `Minilib.Collection.Trait::Bound : Std::Functor`

### impl `[a : Std::ToString] Minilib.Collection.Trait::Bound a : Std::ToString`

### impl `Minilib.Collection.Trait::KeyCompareWithFunc k : Minilib.Collection.Trait::KeyCompare`

### impl `[k : Std::LessThan] Minilib.Collection.Trait::KeyGreaterThan k : Minilib.Collection.Trait::KeyCompare`

### impl `[k : Std::LessThan] Minilib.Collection.Trait::KeyLessThan k : Minilib.Collection.Trait::KeyCompare`