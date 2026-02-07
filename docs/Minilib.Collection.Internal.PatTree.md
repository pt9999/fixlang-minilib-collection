# Minilib.Collection.Internal.PatTree

Defined in minilib-collection@0.7.0-beta2

Simple map using Patricia Tree.

The type of key is `U64`, and the type of value is any type.

## Reference

This module was inspired by [Haskell's `Data.IntMap` package](https://hackage-content.haskell.org/package/containers-0.8/docs/Data-IntMap.html).

In particular, I used the following papers mentioned in the `Data.IntMap` package's documentation:

[Chris Okasaki and Andy Gill, "Fast Mergeable Integer Maps", Workshop on ML, September 1998, pages 77-86](https://web.archive.org/web/20150417234429/https://ittc.ku.edu/~andygill/papers/IntMap98.pdf)

## Values

### namespace Minilib.Collection.Internal.PatTree::Combine

#### append

Type: `[a : Std::Add] Minilib.Collection.Internal.PatTree::Combine a`

A combining function that appends the new value after the old value.

#### overwrite

Type: `Minilib.Collection.Internal.PatTree::Combine a`

A combining function that replaces the old value into the new value.

### namespace Minilib.Collection.Internal.PatTree::PNodeIndex

#### empty

Type: `Minilib.Collection.Internal.PatTree::PNodeIndex`

A special index which represents an empty node.

### namespace Minilib.Collection.Internal.PatTree::PTree

#### empty

Type: `Minilib.Collection.Internal.PatTree::PTree a`

An empty Patricia Tree.

## Types and aliases

### namespace Minilib.Collection.Internal.PatTree

#### Combine

Defined as: `type Combine a = a -> a -> a`

The type of combining functions that resolve collisions.
`combine(old_value, new_value)` should return a value combined from `old_value` and `new_value`.

#### PKey

Defined as: `type PKey = Std::U64`

The key type of Patricia Trees.

#### PMask

Defined as: `type PMask = Std::U64`

The mask type. (used internally)

#### PNode

Defined as: `type PNode a = unbox union { ...variants... }`

The type of tree nodes.

##### variant `empty`

Type: `()`

An empty node.

##### variant `leaf`

Type: `(Minilib.Collection.Internal.PatTree::PKey, a)`

A leaf node. (key, data)

##### variant `branch`

Type: `(Minilib.Collection.Internal.PatTree::Prefix, Minilib.Collection.Internal.PatTree::PMask, Minilib.Collection.Internal.PatTree::PNodeIndex, Minilib.Collection.Internal.PatTree::PNodeIndex)`

A branch node. (prefix, mask of the branching bit, left, right)

#### PNodeIndex

Defined as: `type PNodeIndex = Std::I64`

The type of index of the node array.

#### PTree

Defined as: `type PTree a = unbox struct { ...fields... }`

The type of Patricia Trees.

##### field `_root`

Type: `Minilib.Collection.Internal.PatTree::PNodeIndex`

##### field `_size`

Type: `Std::I64`

##### field `_combine`

Type: `Minilib.Collection.Internal.PatTree::Combine a`

##### field `_nodes`

Type: `Std::Array (Minilib.Collection.Internal.PatTree::PNode a)`

##### field `_freelist`

Type: `Std::Array Minilib.Collection.Internal.PatTree::PNodeIndex`

#### Prefix

Defined as: `type Prefix = Std::U64`

The prefix type. (used internally)

### namespace Minilib.Collection.Internal.PatTree::PTree

#### PTreeIterator

Defined as: `type PTreeIterator a = unbox struct { ...fields... }`

##### field `tree`

Type: `Minilib.Collection.Internal.PatTree::PTree a`

##### field `lower_bound`

Type: `Minilib.Collection.Trait::Bound Minilib.Collection.Internal.PatTree::PKey`

##### field `upper_bound`

Type: `Minilib.Collection.Trait::Bound Minilib.Collection.Internal.PatTree::PKey`

##### field `ascending`

Type: `Std::Bool`

##### field `stack`

Type: `Std::Array Minilib.Collection.Internal.PatTree::PNodeIndex`

## Traits and aliases

## Trait implementations

### impl `Minilib.Collection.Internal.PatTree::PTree a : Minilib.Collection.Trait::Map`

### impl `Minilib.Collection.Internal.PatTree::PTree a : Minilib.Collection.Trait::SortedMapIF`

### impl `[a : Std::ToString] Minilib.Collection.Internal.PatTree::PTree a : Std::ToString`

### impl `Minilib.Collection.Internal.PatTree::PTree::PTreeIterator a : Std::Iterator`