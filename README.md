# Unionf

In computer science, a disjoint-set data structure, also called a union–find data structure or merge–find set, is a data structure that keeps track of a set of elements partitioned into a number of disjoint (non-overlapping) subsets. It provides near-constant-time operations (bounded by the inverse Ackermann function) to add new sets, to merge existing sets, and to determine whether elements are in the same set. In addition to many other uses (see the Applications section), disjoint-sets play a key role in Kruskal's algorithm for finding the minimum spanning tree of a graph.

A disjoint-set forest consists of a number of elements each of which stores an id, a parent pointer, and, in efficient algorithms, a value called the "rank".

The parent pointers of elements are arranged to form one or more trees, each representing a set. If an element's parent pointer points to no other element, then the element is the root of a tree and is the representative member of its set. A set may consist of only a single element. However, if the element has a parent, the element is part of whatever set is identified by following the chain of parents upwards until a representative element (one without a parent) is reached at the root of the tree.

Forests can be represented compactly in memory as arrays in which parents are indicated by their array index.

Disjoint-set data structures model the partitioning of a set, for example to keep track of the connected components of an undirected graph. This model can then be used to determine whether two vertices belong to the same component, or whether adding an edge between them would result in a cycle. The Union–Find algorithm is used in high-performance implementations of unification.

This data structure is used by the Boost Graph Library to implement its Incremental Connected Components functionality. It is also a key component in implementing Kruskal's algorithm to find the minimum spanning tree of a graph.

Note that the implementation as disjoint-set forests doesn't allow the deletion of edges, even without path compression or the rank heuristic.

Sharir and Agarwal report connections between the worst-case behavior of disjoint-sets and the length of Davenport–Schinzel sequences, a combinatorial structure from computational geometry.

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

*Note: Any comparable type is compatible with this gem.*

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
a.size                    # => 4
a.size? :marlon           # => 2
a.union :marlon, :matheus # => 3
a.size? :matheus          # => 3
a.size? :pamella          # => 3
```

You can acquire the elements of the set again.

```ruby
a.elements # => [:marlon, :pamella, :matheus]
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/Schweigert/unionf.

## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
