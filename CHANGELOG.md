# v1.4.1

- Add in overlooked `detectLimit` method (#866)
- Removed unnecessary files from npm releases (#861)
- Removed usage of a reserved word to prevent :boom: in older environments (#870)

# v1.4.0

- `asyncify` now supports promises (#840)
- Added `Limit` versions of `filter` and `reject` (#836)
- Add `Limit` versions of `detect`, `some` and `every` (#828, #829)
- `some`, `every` and `detect` now short circuit early (#828, #829)
- Improve detection of the global object (#804), enabling use in WebWorkers
- `whilst` now called with arguments from iterator (#823)
- `during` now gets called with arguments from iterator (#824)
- Code simplifications and optimizations aplenty ([diff](https://github.com/caolan/async/compare/v1.3.0...v1.4.0))


# v1.3.0

New Features:
- Added `constant`
- Added `asyncify`/`wrapSync` for making sync functions work with callbacks. (#671, #806)
- Added `during` and `doDuring`, which are like `whilst` with an async truth test. (#800)
- `retry` now accepts an `interval` parameter to specify a delay between retries. (#793)
- `async` should work better in Web Workers due to better `root` detection (#804)
- Callbacks are now optional in `whilst`, `doWhilst`, `until`, and `doUntil` (#642)
- Various internal updates (#786, #801, #802, #803)
- Various doc fixes (#790, #794)

Bug Fixes:
- `cargo` now exposes the `payload` size, and `cargo.payload` can be changed on the fly after the `cargo` is created. (#740, #744, #783)


# v1.2.1

Bug Fix:

- Small regression with synchronous iterator behavior in `eachSeries` with a 1-element array.  Before 1.1.0, `eachSeries`'s callback was called on the same tick, which this patch restores.  In 2.0.0, it will be called on the next tick.  (#782)


# v1.2.0

New Features:

- Added `timesLimit` (#743)
- `concurrency` can be changed after initialization in `queue` by setting `q.concurrency`.  The new concurrency will be reflected the next time a task is processed. (#747, #772)

Bug Fixes:

- Fixed a regression in `each` and family with empty arrays that have additional properties. (#775, #777)


# v1.1.1

Bug Fix:

- Small regression with synchronous iterator behavior in `eachSeries` with a 1-element array.  Before 1.1.0, `eachSeries`'s callback was called on the same tick, which this patch restores.  In 2.0.0, it will be called on the next tick.  (#782) 


# v1.1.0

New Features:

- `cargo` now supports all of the same methods and event callbacks as `queue`.
- Added `ensureAsync` - A wrapper that ensures an async function calls its callback on a later tick. (#769)
- Optimized `map`, `eachOf`, and `waterfall` families of functions
- Passing a `null` or `undefined` array to `map`, `each`, `parallel` and families will be treated as an empty array (#667).
- The callback is now optional for the composed results of `compose` and `seq`. (#618)
- Reduced file size by 4kb, (minified version by 1kb) 
- Added code coverage through `nyc` and `coveralls` (#768)

Bug Fixes:

- `forever` will no longer stack overflow with a synchronous iterator (#622)
- `eachLimit` and other limit functions will stop iterating once an error occurs (#754)
- Always pass `null` in callbacks when there is no error (#439)
- Ensure proper conditions when calling `drain()` after pushing an empty data set to a queue (#668)
- `each` and family will properly handle an empty array (#578)
- `eachSeries` and family will finish if the underlying array is modified during execution (#557)
- `queue` will throw if a non-function is passed to `q.push()` (#593)
- Doc fixes (#629, #766)


# v1.0.0

No known breaking changes, we are simply complying with semver from here on out.

Changes:

- Start using a changelog!
- Add `forEachOf` for iterating over Objects (or to iterate Arrays with indexes available) (#168 #704 #321)
- Detect deadlocks in `auto` (#663)
- Better support for require.js (#527)
- Throw if queue created with concurrency `0` (#714)
- Fix unneeded iteration in `queue.resume()` (#758)
- Guard against timer mocking overriding `setImmediate` (#609 #611)
- Miscellaneous doc fixes (#542 #596 #615 #628 #631 #690 #729)
- Use single noop function internally (#546)
- Optimize internal `_each`, `_map` and `_keys` functions.
