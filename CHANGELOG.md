# Change Log

All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](http://semver.org/).

## 0.2.0 - 2016-05-04

### Added

 * Added an ArrayLoader and ChainableLoader.  The ChainableLoader was added to allow using multiple loaders for the same prefix.  The ArrayLoader is mostly for testing, when you want to return paths from an in memory array.

### Changed

* Only validate once when `passes`, `fails`, or `errors` is called instead of re-validating for each call.  This was causing a huge performance hit when validating nested schemas.  The properties constraint made two calls which resulted in an exponential slow down for each level of nesting.
* The `Ruleset` interface now requires throwing a `ConstraintNotFoundException` instead of returning null for missing constraints.
* Moved to the League namespace.
* The curl extension is now explicitly required for dev installs, since you need it to test the `CurlWebLoader`.
* The default max depth was increased to 50.  The validator can validate to that depth really quickly and it's high enough that it won't be reached with normal usage.
* The tests were switched to load json-schema.org urls from memory since their site went down and the build started failing.
