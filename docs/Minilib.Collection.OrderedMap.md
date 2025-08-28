# Minilib.Collection.OrderedMap

Defined in minilib-collection@0.6.0

Ordered map.
This is similar to HashMap except it preserves the order of entries.

## Values

### namespace Minilib.Collection.OrderedMap::OrderedMap

#### contains_key

Type: `[k : Hash::HashKey] k -> Minilib.Collection.OrderedMap::OrderedMap k v -> Std::Bool`

Check whether an OrderedMap contains a key.

#### empty

Type: `Std::I64 -> Minilib.Collection.OrderedMap::OrderedMap k v`

Create an empty OrderedMap which is reserved so that it will not rehash until size exceeds the spacified value.

#### erase

Type: `[k : Hash::HashKey] k -> Minilib.Collection.OrderedMap::OrderedMap k v -> Minilib.Collection.OrderedMap::OrderedMap k v`

Erase an element from an OrderedMap.

#### find

Type: `[k : Hash::HashKey] k -> Minilib.Collection.OrderedMap::OrderedMap k v -> Std::Option v`

Find an element from an OrderedMap.

#### find_or

Type: `[k : Hash::HashKey] k -> v -> Minilib.Collection.OrderedMap::OrderedMap k v -> v`

Find an element from an OrderedMap. If the map doesn't contain the key, it returns the given default value.

#### get_capacity

Type: `Minilib.Collection.OrderedMap::OrderedMap k v -> Std::I64`

Get capacity of an OrderedMap.

#### get_size

Type: `Minilib.Collection.OrderedMap::OrderedMap k v -> Std::I64`

Get size (number of elements) in an OrderedMap.

#### insert

Type: `[k : Hash::HashKey] k -> v -> Minilib.Collection.OrderedMap::OrderedMap k v -> Minilib.Collection.OrderedMap::OrderedMap k v`

Insert an element into an OrderedMap.

#### reserve

Type: `[k : Hash::HashKey] Std::I64 -> Minilib.Collection.OrderedMap::OrderedMap k v -> Minilib.Collection.OrderedMap::OrderedMap k v`

Reserve an OrderedMap so that it will not rehash until size exceeds the spacified value.

#### to_iter

Type: `Minilib.Collection.OrderedMap::OrderedMap k v -> Minilib.Collection.OrderedMap::OrderedMap::OrderedMapIterator k v`

Convert an OrderedMap into an iterator. The order of the elements is the same as
when they were inserted into the map.

## Types and aliases

### namespace Minilib.Collection.OrderedMap

#### OrderedMap

Defined as: `type OrderedMap k v = unbox struct { ...fields... }`

Similar to HashMap, but `to_iter()` returns entries in the same order as they were inserted.

##### field `map`

Type: `HashMap::HashMap k (Std::I64, v)`

##### field `serial`

Type: `Std::I64`

### namespace Minilib.Collection.OrderedMap::OrderedMap

#### OrderedMapIterator

Defined as: `type OrderedMapIterator k v = Std::Iterator::MapIterator (Std::Iterator::ArrayIterator (k, (Std::I64, v))) (k, (Std::I64, v)) (k, v)`

## Traits and aliases

## Trait implementations

### impl `[k : Hash::HashKey, v : Std::Eq] Minilib.Collection.OrderedMap::OrderedMap k v : Std::Eq`

### impl `[k : Hash::HashKey, k : Std::ToString, v : Std::ToString] Minilib.Collection.OrderedMap::OrderedMap k v : Std::ToString`