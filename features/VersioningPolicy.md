Since the release of RSpec 3.0, RSpec aims to adhere to [Semantic Versioning 2.0.0](http://semver.org/). Violations
of this scheme should be reported as bugs. Specifically, if a minor or patch version is
released that breaks backward compatibility of a public API, that version should be
immediately yanked and/or a new version should be immediately released that restores
compatibility.  Breaking changes to the public API will only be introduced with new major
versions. As a result of this policy, you can (and should) specify a dependency on this gem
using the Pessimistic Version Constraint with two digits of precision. For example:

``` ruby
spec.add_dependency 'rspec', '~> 3.0'
```

### What does "public API" mean?

The concept of a "public API" is central to SemVer. The versioning semantics of SemVer only
apply to _public APIs_, which provides users with a strong guarantee that the APIs they rely on
will only be purposefully changed in a backwards-incompatible way in a major release,
while allowing library maintainers to explicitly reserve some APIs as being subject to change in any release.

For RSpec, we've chosen to document the public API using our API docs hosted on rubydoc.info:

* <a href="http://rubydoc.info/gems/rspec-core/frames">rspec-core</a>
* <a href="http://rubydoc.info/gems/rspec-expectations/frames">rspec-expectations</a>
* <a href="http://rubydoc.info/gems/rspec-mocks/frames">rspec-mocks</a>
* <a href="http://rubydoc.info/gems/rspec-rails/frames">rspec-rails</a>

Please do not use RSpec APIs that are not documented as being public, as your code is likely
to break when we release future versions of RSpec.  If you need something not provided by
our public APIs, please [open an issue](https://github.com/rspec/rspec-core/issues) describing your need.  We'll gladly add a new API or
declare an existing private API public.

