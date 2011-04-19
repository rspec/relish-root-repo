RSpec is divided up into several sub-projects, each of which produces its own
Ruby gem.  They can be used together or separately.

The common case is to use rspec-core, rspec-expectations, and rspec-mocks as a
unit. In this case, you only need install the rspec gem, which depends on the
other three, so they will be installed at the same time. That part is simple.
Which _versions_ get installed is a bit trickier.

The rspec gem uses a [Pessimistic Version
Constraint](http://docs.rubygems.org/read/chapter/16#page74) (e.g. "~> 2.4.0")
to declare its dependencies on the rspec-core, rspec-expectations, and
rspec-mocks gems. This means that when you install rspec-2.4.0, you'll get the
latest patch releases of rspec-2.4, but you won't get versions >= 2.5.
