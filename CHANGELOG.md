## 0.x.x
### ** BREAKING CHANGES **
- Moved `Minilib.Collection.RBTree` to `Minilib.Collection.Internal.RBTree`.
### Added
- Added following modules:
  * `Minilib.Collection.PTreeMap`
  * `Minilib.Collection.PTreeSet`
  * `Minilib.Collection.TreapSet`
  * `Minilib.Collection.Trait.Map`
  * `Minilib.Collection.Trait.Set`
  * `Minilib.Collection.Trait.SortedMap`
  * `Minilib.Collection.Trait.SortedSet`
  * `Minilib.Collection.Internal.PatTree`
### Changed
- These types implements traits defined in `Minilib.Collection.Trait.*`.
  If you use these types, you may need to import the appropriate trait modules.
    - `Minilib.Collection.PTreeSet::PTreeSet`
    - `Minilib.Collection.PTreeMap::PTreeMap`
    - `Minilib.Collection.TreapSet::TreapSet`
    - `Minilib.Collection.TreeSet::TreeSet`
    - `Minilib.Collection.TreeMap::TreeMap`

## 0.6.5
### Changed
- fixproj.toml: change versions of dependencies to "*"
