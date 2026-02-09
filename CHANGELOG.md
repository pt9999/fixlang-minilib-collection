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

## 0.6.6
### Changed
- fixproj.toml: change versions of dependencies to be fixed again

## 0.6.5
### Changed
- fixproj.toml: change versions of dependencies to "*"
