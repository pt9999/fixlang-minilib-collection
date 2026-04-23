## 0.8.0
### ** BREAKING CHANGES **
- The following functions now return an Iterator of opaque types.
  - `OrderedMap::to_iter`
- The following type aliases are now removed.
  - `OrderedMapIterator`
- The following trait methods now return an Iterator of opaque types.
  - `Set::to_iter`
  - `Map::to_iter`
  - `SortedSetIF::select_range`
  - `SortedMapIF::select_range`
- The following associated types are now removed.
  - `Set::SetIterator`
  - `Map::MapIterator`
- The following trait methods are moved to the parent traits, since they use associated types of the parent traits.
  - `SortedSet::select_range` -> `Set::select_range`
  - `SortedMap::select_range` -> `Map::select_range`
- `SortedSet` and `SortedMap` are now empty. These are used to indicate that `select_range` is correctly defined.
### Changed
- Utilized minilib-common@0.13.0.

## 0.7.1
### Added
- Minilib.Collection.TreapSet: Added `from_iter`, `from_iter_kc`.
### Fixed
- Fixed problems which were found by `fix check` command. (Thanks to tttmmm san)

## 0.7.0
### ** BREAKING CHANGES **
- These modules use traits such as `Set` and `Map` defined in `Minilib.Collection.Trait`.
  If you use these modules, you should also import `Minilib.Collection.Trait`.
    - `Minilib.Collection.TreeSet`
    - `Minilib.Collection.TreeMap`
- The signature of `Map::insert` is now `(k, v) -> map -> map`
  instead of `k -> v -> map -> map` to avoid ambiguity with `Set::insert`.
- Moved `Minilib.Collection.RBTree` to `Minilib.Collection.Internal.RBTree`.
### Added
- Added following modules:
  * `Minilib.Collection.PTreeMap`
  * `Minilib.Collection.PTreeSet`
  * `Minilib.Collection.TreapMap`
  * `Minilib.Collection.TreapSet`
  * `Minilib.Collection.Trait`
  * `Minilib.Collection.Internal.PatTree`
### Changed
- fixproj.toml: Bumped `fix_version` to 1.3.0. Depends on minilib-common@0.12.0. Moved random to test_dependencies.

## 0.6.6
### Changed
- fixproj.toml: change versions of dependencies to be fixed again

## 0.6.5
### Changed
- fixproj.toml: change versions of dependencies to "*"
