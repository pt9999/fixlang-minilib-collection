## 0.x.x
### ** BREAKING CHANGES **
- Moved `Minilib.Collection.RBTree` to `Minilib.Collection.Internal.RBTree`.
### Added
- Added following modules:
  * `Minilib.Collection.PTreeMap`
  * `Minilib.Collection.PTreeSet`
  * `Minilib.Collection.Treap`
  * `Minilib.Collection.Trait.Set`
  * `Minilib.Collection.Trait.Map`
  * `Minilib.Collection.Internal.PatTree`
### Changed
- Minilib.Collection.Treap: Implemented `Minilib.Collection.Trait.Set`.
  If you use `Treap`, you should also import `Minilib.Collection.Trait.Set`.
- Minilib.Collection.TreeSet: Implemented `Minilib.Collection.Trait.Set`.
  If you use `TreeSet`, you should also import `Minilib.Collection.Trait.Set`.
- Minilib.Collection.TreeMap: Implemented `Minilib.Collection.Trait.Map`.
  If you use `TreeMap`, you should also import `Minilib.Collection.Trait.Map`.

## 0.6.5
### Changed
- fixproj.toml: change versions of dependencies to "*"
