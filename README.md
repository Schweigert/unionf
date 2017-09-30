# Unionf

Welcome to your new gem! In this directory, you'll find the files you need to be able to package up your Ruby library into a gem. Put your Ruby code in the file `lib/unionf`. To experiment with that code, run `bin/console` for an interactive prompt.

TODO: Delete this and the text above, and describe your gem

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'unionf'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install unionf

## Usage

Create a new set:
```ruby
require 'unionf'

include Unionf

a = UnionFind.new [:marlon, :pamella, :matheus]
```

The return of a union is the size of the new set created.
The find method for a set tells you what element represents that set.

```ruby
a.union :marlon, :pamella      # => 2
a.find :marlon                 # => :pamella
a.connected? :marlon, :pamella # => true
a.connected? :marlon, :matheus # => false
```

You can also find the size of the set, and the subsets.

```ruby
a.size # => 4
a.size? :marlon, :pamella # => 2
```

You can acquire the elements of the set again.

```ruby
a.elements # => [:marlon, :pamella, :matheus]
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/unionf.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
