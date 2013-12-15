RSpec 3 includes many breaking changes, but our hope is to make this
the smoothest major-version gem upgrade you've ever done. To assist
with that process, we've been developing RSpec 2.99 in tandem with
RSpec 3.  Every time we make a breaking change in the master branch
for 3.0, we've been adding a corresponding deprecation to 2.99.  This
isn't just for APIs that have been removed; it's also for slight changes
in edge-case semantics (in order to make RSpec more consistent) that
some projects may rely on. Rather than just giving you a generic
upgrade document that describes _all_ of the breaking changes
(ost of which affect very few users!), RSpec 2.99 gives you
a detailed upgrade checklist.

In addition, [Yuji Nakayama](https://twitter.com/nkym37) has been developing
[transpec](https://github.com/yujinakayama/transpec) -- an absolutely amazing
tool that can automatically upgrade most RSpec suites. We've tried it on a
few projects and have been _amazed_ at how well it works.

## Step-by-step Instructions

1. Ensure your test suite is already green on whatever RSpec 2.x version
   you're already using.
2. Install RSpec 2.99.0.beta1 (or whatever the latest 2.99 release is
   when you go through this process).
3. Run your test suite and ensure it's still green. (It should be, but
   we may have made a mistake -- if it breaks anything, please report
   a bug!). Now would be a good time to commit.
4. You'll notice a bunch of deprecation warnings printed off at the
   end of the spec run. These may be truncated since we don't to
   spam you with the same deprecation warning over and over again. To
   get the full list of deprecations, you can pipe them into a file
   by setting the `config.deprecation_stream = 'rspec.log'` option.
5. If you want to understand all of what is being deprecated, it's a
   good idea to read through the deprecation messages.  In some cases,
   you have choices -- such as continuing to use the `have` collection
   cardinality matchers via the extracted
   [rspec-collection_matchers](https://github.com/rspec/rspec-collection_matchers)
   gem, or by rewriting the expectation expression to something like
   `expect(list.size).to eq(3)`.
6. `gem install transpec` (Note that this need not go into your
   `Gemfile`: you run `transpec` as a standalone executable
    outside the context of your bundle).
7. Run transpec on your project. Check `transpec --help` or
   [the README](https://github.com/yujinakayama/transpec#transpec)
   for a full list of options.
8. Run the test suite (it should still be green but it's always good to
   check!) and commit.
9. If there are any remaining deprecation warnings (transpec doesn't
   quite handle all of the warnings you may get), deal with them.
9. Once you've got a deprecation-free test suite running against RSpec
   2.99, you're ready to upgrade to RSpec 3. Install RSpec 3.0.0.beta1
   (or whatever the latest 3.x release is when you go through this process).
10. Run your test suite. It should still be green. If anything fails,
    please open a Github issue -- we consider it a bug[^foot_1]! Note
    that you may still get a few additional deprecation warnings on
    RSpec 3 that weren't present on 2.99.  This is normal -- there are
    a few things we couldn't easily deprecate in 2.99 and remove in 3.0,
    so they trigger deprecations in 3.0 with the plan to remove them in
    RSpec 4.
11. Commit and enjoy using the latest RSpec release!

[^foot_1]: There is one caveat to that, though: we only consider it a bug
  to the extent that your test suite uses the RSpec APIs as they are
  documented. The dynamic nature of Ruby makes it possible to use RSpec
  in ways that we can't support.

