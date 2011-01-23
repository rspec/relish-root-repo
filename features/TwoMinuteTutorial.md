### Prerequisites

* Ruby 1.8.6 or higher
* Rubygems 1.3.7

### Install

    gem install rspec

This installs four gems:

* rspec
* rspec-core
* rspec-expectations
* rspec-mocks

The rspec-core gem installs an `rspec` executable. Run the `rspec` command with
the `--help` flag to see the available options:

    rspec --help

### Getting started

Begin with a very simple example that expresses some basic desired behaviour.

    # bowling_spec.rb
    
    describe Bowling do
      describe "#score" do
        it "returns 0 for all gutter game" do
          bowling = Bowling.new
          20.times { bowling.hit(0) }
          bowling.score.should == 0
        end
      end
    end

Run the example and watch it fail.

<pre style="color:red;">
$ rspec bowling_spec.rb 
  uninitialized constant Object::Bowling (NameError)
</pre>

Now write just enough code to make it pass.

<pre>
# bowling_spec.rb

require './bowling'
...
</pre>

<pre>
# bowling.rb

class Bowling
  def hit(pins)
  end

  def score
    0
  end
end
</pre>

Run the example and bask in the joy that is green.

<pre style="color:green;">
$ rspec bowling_spec.rb --color --format doc

Bowling
  #score
    returns 0 for all gutter game

Finished in 0.00057 seconds
1 example, 0 failures
</pre>

