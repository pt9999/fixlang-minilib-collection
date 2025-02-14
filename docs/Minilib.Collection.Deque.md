# `module Minilib.Collection.Deque`

Deque (double-ended queue).
Deque can be used as a FIFO such as a message queue.
When used as a FIFO, the amortized costs of `push_back()` and
`pop_front()` are `O(1)`.

# Types and aliases

## `namespace Minilib.Collection.Deque`

### `type Deque a = unbox struct { ...fields... }`

A type that represents a double-ended queue.

#### field `front : Std::Array a`

#### field `back : Std::Array a`

## `namespace Minilib.Collection.Deque::Deque`

### `type DequeIterator = Std::Iterator::AppendIterator (Std::Iterator::ReverseIterator (Std::Iterator::ArrayIterator a) a) (Std::Iterator::ArrayIterator a)`

# Traits and aliases

# Trait implementations

# Values

## `namespace Minilib.Collection.Deque::Deque`

### `_reverse_array : Std::Array a -> Std::Array a`

Reverses an array.

### `empty : Std::I64 -> Minilib.Collection.Deque::Deque a`

Creates an empty double-ended queue.

### `get_back : Minilib.Collection.Deque::Deque a -> Std::Option a`

Gets the back element of the queue.

### `get_front : Minilib.Collection.Deque::Deque a -> Std::Option a`

Gets the front element of the queue.

### `get_size : Minilib.Collection.Deque::Deque a -> Std::I64`

Gets the size of the queue.

### `is_empty : Minilib.Collection.Deque::Deque a -> Std::Bool`

Returns true iff the queue is empty.

### `pop_back : Minilib.Collection.Deque::Deque a -> Minilib.Collection.Deque::Deque a`

Pops an element from the back of the queue. If the queue is empty, it does nothing.

### `pop_front : Minilib.Collection.Deque::Deque a -> Minilib.Collection.Deque::Deque a`

Pops an element from the front of the queue. If the queue is empty, it does nothing.

### `push_back : a -> Minilib.Collection.Deque::Deque a -> Minilib.Collection.Deque::Deque a`

Pushes an element to the back of the queue.

### `push_front : a -> Minilib.Collection.Deque::Deque a -> Minilib.Collection.Deque::Deque a`

Pushes an element to the front of the queue.

### `to_iter : Minilib.Collection.Deque::Deque a -> Minilib.Collection.Deque::Deque::DequeIterator a`

Returns an iterator of elements.