### Release Policy

Since the release of RSpec-2.0, RSpec follows the [Rubygems Rational Versioning
Policy](http://docs.rubygems.org/read/chapter/7). We are working toward
compliance with [Semantic Versioning](http://semver.org/), but that is a bit
down the road. You can read those documents for more detail, but the short
version is this:

Release numbers have three parts:

* Major
* Minor
* Patch

For example, the recent 2.3.0 release means:

* Major: 2
* Minor: 3
* Patch: 0

The different parts follow the following conventions:

* Patch releases have only bug fixes.
* Minor releases have bug fixes and/or new functionality.
* Major releases have bug fixes and/or new functionality _possibly including breaking changes_.

#### What this means for RSpec users

The first thing you'll notice is more frequent minor and major releases. We are
already at rspec-2.4.x instead of 2.0.5 because we've steadily added new
features, so the 2.1, 2.2, and 2.3 releases were inappropriate for a patch
release.

The real benefit is that you can now safely use a [Pessimistic Version
Constraint](http://docs.rubygems.org/read/chapter/16#page74) (e.g. "~> 2.3")
with confidence that you won't accidentally absorb breaking changes.
