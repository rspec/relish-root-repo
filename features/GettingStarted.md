### Prerequisites

* Ruby 1.8.7 or higher (we recommend Ruby 1.9 or 2.0)
* Rubygems 1.3.7

### Install

    gem install rspec

This installs five gems:

* rspec
* rspec-core
* rspec-expectations
* rspec-mocks
* rspec-support

The rspec-core gem installs an `rspec` executable. Run the `rspec` command with
the `--help` flag to see the available options:

    rspec --help

### Getting started

Begin with a very simple example that expresses some basic desired behaviour.

    # game_spec.rb
    
    describe Game do
      describe "#score" do
        it "returns 0 for all gutter game" do
          game = Game.new
          20.times { game.roll(0) }
          game.score.should == 0
        end
      end
    end

Run the example and watch it fail.

<pre style="color:red;">
$ rspec game_spec.rb 
  uninitialized constant Object::Game (NameError)
</pre>

Now write just enough code to make it pass.

<pre>
# game_spec.rb

require './game'
...
</pre>

    # game.rb

    class Game
      def roll(pins)
      end

      def score
        0
      end
    end

Run the example and bask in the joy that is green.

<pre style="color:green;">
$ rspec game_spec.rb --color --format doc

Game
  #score
    returns 0 for all gutter game

Finished in 0.00057 seconds
1 example, 0 failures
</pre>
