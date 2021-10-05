# Link 
Original repo https://github.com/makerdao/osm, for fetching and merge change add new remote with command git remote add maker https://github.com/makerdao/osm.



# Oracle Security Module

This contract is given a `DSValue` as a source to read from. You set a time interval with `step`. Whenever that `step` time has passed, it will let you `poke`. When you `poke` it reads the value from the source and stores it. The previous stored value becomes the current value. 

This contracts implements `read` and `peek` from DSValue, but it is not one. It also has a new function `peep` to read what the next value will be after a `poke`.

```
// create
OSM osm = new OSM(DSValue(src));

// can be poked every hour, on the hour
osm.step(3600);

(val, ok) = osm.peek() // get current value
(val, ok) = osm.peep() // get upcoming value
val       = osm.read() // get current value, or fail

```

If this `DSValue` has a valid value on creation, the OSM with start with that same value.
