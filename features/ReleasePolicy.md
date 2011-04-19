Since the release of RSpec-2.0, RSpec follows the [Rubygems Rational Versioning
Policy](http://docs.rubygems.org/read/chapter/7). We are working toward
compliance with [Semantic Versioning](http://semver.org/), but that is a bit
down the road. You can read those documents for more detail, but the short
version is this:

Release numbers have three parts: Major, Minor, and Patch. For example, the
recent 2.4.1 release of rspec-rails means:

* Major: 2
* Minor: 4
* Patch: 1

The different parts follow the following conventions:

* Patch releases have only bug fixes.
* Minor releases have bug fixes and/or new functionality.
* Major releases have bug fixes and/or new functionality _possibly including breaking changes_.

### What this means for RSpec users

The first thing you'll notice is more frequent minor and major releases. We are
already at rspec-2.6.x instead of 2.0.5 because we've steadily added new
features, so the 2.1, 2.2, and 2.3 releases were inappropriate for a patch
release.

The real benefit is that you can now safely use a [Pessimistic Version
Constraint](http://docs.rubygems.org/read/chapter/16#page74) (e.g. "~> 2.3")
with confidence that you won't accidentally absorb breaking API changes.

### Exceptions

RSpec lives in a complex ecosystem, and often has to integrate with several
other tools. As much as we try to adhere strictly to the policy described
above, there are cases in which it makes more sense for us to release a change
that breaks at an integration point than push out a major release.

For example, rspec-core-2.5.1 changed how RSpec integrates with Autotest and
Bundler. The negative impact was that users may have seen missing dependency
errors (though none were reported) if they were relying on Bundler when running
Autotest. This was low impact, did not introduce a code-related API change,
and, most importantly, did not result in false-positives or silent failures. We
therefore opted to release these changes in a patch release rather than
introducing rspec-3.0, which would likely have caused much more confusion.
