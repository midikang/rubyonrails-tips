## Iterating Over Hashes

Iterate over the matz hash and print each value to the console using puts. Don't print out the keys!
```
matz = { "First name" => "Yukihiro",
  "Last name" => "Matsumoto",
  "Age" => 47,
  "Nationality" => "Japanese",
  "Nickname" => "Matz"
}
```

Solution
```
matz.each do |key, value|
    puts matz[key]
end
```

## Nil: a Formal Introduction

In many languages, you'll get an error of some kind. Not so in Ruby: you'll instead get the special value nil.
Along with false, nil is one of two non-true values in Ruby. (Every other object is regarded as "truthy," meaning that if you were to type if 2 or if "bacon", the code in that if statement would be run.)
It's important to realize that false and nil are not the same thing: false means "not true," while nil is Ruby's way of saying "nothing at all."

Go ahead and try to access a key in creatures that doesn't exist.
```
creatures = { "weasels" => 0,
  "puppies" => 6,
  "platypuses" => 3,
  "canaries" => 1,
  "Heffalumps" => 7,
  "Tiggers" => 1
}
```

Solution
```
creatures = { "weasels" => 0,
  "puppies" => 6,
  "platypuses" => 3,
  "canaries" => 1,
  "Heffalumps" => 7,
  "Tiggers" => 1
}

creatures["Dogs"]

```

## Setting Your Own Default
You don't have to settle for nil as a default value, however. If you create your hash using the Hash.new syntax, you can specify a default like so:
```
my_hash = Hash.new("Trady Blix")
```
Now if you try to access a nonexistent key in my_hash, you'll get "Trady Blix" as a result.

In the meantime, create a hash called no_nil_hash and give it any default value other than nil.

Solution
```
no_nil_hash = Hash.new("Midi")
no_nil_hash["haha"]
```

## A Key of a Different Color
We can certainly use strings as Ruby hash keys; as we've seen, there's always more than one way to do something in Ruby. However, the Rubyist's approach would be to use **symbols**.

Check out the code in the editor. Those funny-looking variables that start with colons are symbols. Click Save & Submit Code to see what happens, then head to the next section for a symbol rundown.

```
menagerie = { :foxes => 2,
  :giraffe => 1,
  :weezards => 17,
  :elves => 1,
  :canaries => 4,
  :ham => 1
}
```

## What's a Symbol?

to_sym and intern are same

```
strings = ["HTML", "CSS", "JavaScript", "Python", "Ruby"]

# Add your code below!

symbols =[]
strings.each do |value|
    symbols.push(value.to_sym)
end
```

```
# Add your code below!

symbols =[]
strings.each do |value|
    symbols.push value.to_sym
end
```

```
strings = ["HTML", "CSS", "JavaScript", "Python", "Ruby"]

# Add your code below!

symbols =[]
strings.each do |value|
    symbols.push(value.intern)
end
```

Create a hash called movies with symbols as keys and strings as values.
Inside your hash, add two key/value pairs.
The keys should be the names of movies.
The values should be quick descriptions or reviews.
```
movies ={
    :a_good_man => "Awesome",
    :inception => "I like it!"
    }
```

## The Hash Rocket Has Landed
However, the hash syntax has changed in Ruby 1.9. Just when you were getting comfortable!

```
new_hash = { one: 1,
  two: 2,
  three: 3
}
```
The two changes are:

- You put the colon at the end of the symbol, not at the beginning;
- You don't need the hash rocket anymore.

It's important to note that even though these keys have colons at the end instead of the beginning, they're still symbols!
```
puts new_hash
# ==> {:one=>1, :two=>2, :three=>3}
```
From now on, we'll use the new 1.9 hash syntax when giving examples or providing default code. You'll want to be familiar with the hash rocket style when reading other people's code, which might be older.

Update your hash from the previous exercise to use the new 1.9 hash syntax instead of the older hash rocket syntax.

```
movies ={
    a_good_man: "Awesome",
    inception: "I like it!"
    }
```

## Dare to Compare
We mentioned that hash lookup is faster with symbol keys than with string keys. Here, we'll prove it!

The code in the editor uses some new syntax, so don't worry about understanding all of it just yet. It builds two alphabet hashes: one that pairs string letters with their place in the alphabet ( "a" with 1, "b" with 2...) and one that uses symbols (:a with 1, :b with 2...). We'll look up the letter "r" 100,000 times to see which process runs faster!

It's good to keep in mind that the numbers you'll see are only fractions of a second apart, and we did the hash lookup 100,000 times each. It's not much of a performance increase to use symbols in this case, but it's definitely there!
```
require 'benchmark'

string_AZ = Hash[("a".."z").to_a.zip((1..26).to_a)]
symbol_AZ = Hash[(:a..:z).to_a.zip((1..26).to_a)]

string_time = Benchmark.realtime do
  10_100_000.times { string_AZ["r"] }
end

symbol_time = Benchmark.realtime do
  10_100_000.times { symbol_AZ[:r] }
end

puts "String time: #{string_time} seconds."
puts "Symbol time: #{symbol_time} seconds."
```

Output
```
String time: 2.925422568 seconds.
Symbol time: 1.12424527 seconds.
nil
```

## Becoming More Selective
We know how to grab a specific value from a hash by specifying the associated key, but what if we want to filter a hash for values that meet certain criteria? For that, we can use .select.

```
grades = { alice: 100,
  bob: 92,
  chris: 95,
  dave: 97
}

grades.select {|name, grade| grade < 97}
# ==> {:bob=>92, :chris=>95}

grades.select { |k, v| k == :alice }
# ==> {:alice=>100}
```

- In the example above, we first create a grades hash that maps symbols to integers.
- Then we call the .select method and pass in a block of code. The block contains an expression for selecting matching key/value pairs. It returns a hash containing :bob and :chris.
- Finally, we call the .select method again. Our block looks only for the key :alice. This is an inefficient method of getting a key/value pair, but it shows that .select does not modify the hash.

Create a new variable, good_movies, and set it equal to the result of calling .select on movie_ratings, selecting only movies with a rating strictly greater than 3.


```
movie_ratings = {
  memento: 3,
  primer: 3.5,
  the_matrix: 5,
  truman_show: 4,
  red_dawn: 1.5,
  skyfall: 4,
  alex_cross: 2,
  uhf: 1,
  lion_king: 3.5
}
# Add your code below!

good_movies= movie_ratings.select{ |k,v| v > 3}
```

## More Methods, More Solutions
We've often found we only want the key or value associated with a key/value pair, and it's kind of a pain to put both into our block and only work with one. Can we iterate over just keys or just values?

This is Ruby. Of course we can.

Ruby includes two hash methods, .each_key and .each_value, that do exactly what you'd expect:
```
my_hash = { one: 1, two: 2, three: 3 }

my_hash.each_key { |k| print k, " " }
# ==> one two three

my_hash.each_value { |v| print v, " " }
# ==> 1 2 3
```

Let's wrap up our study of Ruby hashes and symbols by testing these methods out.

Go ahead and print out just the titles of our movies using puts.

```
movie_ratings = {
  memento: 3,
  primer: 3.5,
  the_matrix: 3,
  truman_show: 4,
  red_dawn: 1.5,
  skyfall: 4,
  alex_cross: 2,
  uhf: 1,
  lion_king: 3.5
}
# Add your code below!

movie_ratings.each_key{ |k| puts k}
```