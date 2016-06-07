# Refactor Factory
## What You'll Be Fixing
All right! We're going to reinforce our knowledge of Ruby best practices by refactoring some existing code. As mentioned, refactoring is the process by which we improve a code's structure, appearance, and/or performance without modifying its overall behavior.

The code in the editor is a Ruby method, first_n_primes, that takes a number n and generates a list of the first n prime numbers. Unfortunately, our poor author hasn't yet mastered all the tools available in Ruby. But we can fix that!

Let's get to work. Click Save & Submit Code to start refactoring this monster of a program!
```
$VERBOSE = nil    # We'll explain this at the end of the lesson.
require 'prime'   # This is a module. We'll cover these soon!

def first_n_primes(n)

  unless n.is_a? Integer
    return "n must be an integer."
  end

  if n <= 0
    return "n must be greater than 0."
  end
  
  prime_array = [] if prime_array.nil?
  
  prime = Prime.new
  for num in (1..n)
    prime_array.push(prime.next)
  end
  return prime_array
end

first_n_primes(10)
```

Output
```
[2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
```

Solution
```

```

## To Be or Not to Be
First up, on line 14, our hapless programmer has decided to check whether prime_array has a value by using the .nil? method, which returns true if a value is nil and false otherwise. This isn't a bad idea, and he even has the one-line if statement right!

However, there's a better way—we can use conditional assignment to set prime_array to [] rather than bother with the .nil? check.
```
def my_method(optional_param)
  optional_param ||= 3
  puts optional_param
end

my_method(5)
# puts 5
my_method(nil)
# puts 3
```

Instructions
Refactor the code on line 14 to use conditional assignment to set prime_array to [] instead of using an if statement.

```
$VERBOSE = nil    # We'll explain this at the end of the lesson.
require 'prime'   # This is a module. We'll cover these soon!

def first_n_primes(n)

  unless n.is_a? Integer
    return "n must be an integer."
  end

  if n <= 0
    return "n must be greater than 0."
  end
  
  prime_array = [] if prime_array.nil?
  
  prime = Prime.new
  for num in (1..n)
    prime_array.push(prime.next)
  end
  return prime_array
end

first_n_primes(10)
```

Solution
```
$VERBOSE = nil    # We'll explain this at the end of the lesson.
require 'prime'   # This is a module. We'll cover these soon!

def first_n_primes(n)

  unless n.is_a? Integer
    return "n must be an integer."
  end

  if n <= 0
    return "n must be greater than 0."
  end
  
  prime_array ||= []
  
  prime = Prime.new
  for num in (1..n)
    prime_array.push(prime.next)
  end
  return prime_array
end

first_n_primes(10)
```

## Omit Needless Words
If you've taken a writing class, you might have come across Strunk & White's [The Elements of Style](http://www.bartleby.com/141/). One of their suggestions is to omit needless words, and it applies just as much to writing Ruby as writing essays.

There are two control structures to change here:

- The unless on line 6
- The if on line 10

Instructions
Refactor the code in the editor to use single-line ifs and unlesss.

```
$VERBOSE = nil    # We'll explain this at the end of the lesson.
require 'prime'   # This is a module. We'll cover these soon!

def first_n_primes(n)

  unless n.is_a? Integer
    return "n must be an integer."
  end

  if n <= 0
    return "n must be greater than 0."
  end
  
  prime_array ||= []
  
  prime = Prime.new
  for num in (1..n)
    prime_array.push(prime.next)
  end
  return prime_array
end

first_n_primes(10)
```

Solution
**Notes** 
n.is_a?(Integer)
n.is_a? Integer 
are equal
```
$VERBOSE = nil    # We'll explain this at the end of the lesson.
require 'prime'   # This is a module. We'll cover these soon!

def first_n_primes(n)
  
  return "n must be an integer." unless n.is_a?(Integer)
  
  return "n must be greater than 0." if n <= 0
  
  prime_array ||= []
  
  prime = Prime.new
  for num in (1..n)
    prime_array.push(prime.next)
  end
  return prime_array
end

first_n_primes(10)
```

## Less is More
Great work! This code looks better already.

We can remove even more, however. There's one return statement in this code that we can change from explicit to implicit!

Recall that Ruby will automatically return **the value of the last expression it evaluates**.

Instructions
Find the unnecessary return keyword and remove it.
```
$VERBOSE = nil    # We'll explain this at the end of the lesson.
require 'prime'   # This is a module. We'll cover these soon!

def first_n_primes(n)
  
  return "n must be an integer." unless n.is_a? Integer
  
  return "n must be greater than 0." if n <= 0
  
  prime_array ||= []
  
  prime = Prime.new
  for num in (1..n)
    prime_array.push(prime.next)
  end
  return prime_array
end

first_n_primes(10)
```

Solution
```
$VERBOSE = nil    # We'll explain this at the end of the lesson.
require 'prime'   # This is a module. We'll cover these soon!

def first_n_primes(n)
  
  return "n must be an integer." unless n.is_a? Integer
  
  return "n must be greater than 0." if n <= 0
  
  prime_array ||= []
  
  prime = Prime.new
  for num in (1..n)
    prime_array.push(prime.next)
  end
  prime_array
end

first_n_primes(10)
```

## The Rubyist's Loop
Excellent! Now we'll want to attack that funky-looking for loop. Let's go ahead and replace it with a nice n.times.

Instructions
Replace the for loop with a call to .times.
```
$VERBOSE = nil    # We'll explain this at the end of the lesson.
require 'prime'   # This is a module. We'll cover these soon!

def first_n_primes(n)
  
  return "n must be an integer." unless n.is_a? Integer
  
  return "n must be greater than 0." if n <= 0
  
  prime_array ||= []
  
  prime = Prime.new
  for num in (1..n)
    prime_array.push(prime.next)
  end
  prime_array
end

first_n_primes(10)
```

Solution
```
$VERBOSE = nil    # We'll explain this at the end of the lesson.
require 'prime'   # This is a module. We'll cover these soon!

def first_n_primes(n)
  
  return "n must be an integer." unless n.is_a? Integer
  
  return "n must be greater than 0." if n <= 0
  
  prime_array ||= []
  
  prime = Prime.new
  n.times {prime_array.push(prime.next)}
  prime_array
end

first_n_primes(10)
```

### Final Push
Nearly there! To finish this up, let's take out the .push and use the concatenation operator instead.

Instructions
Replace the call to .push with the << operator.

```
$VERBOSE = nil    # We'll explain this at the end of the lesson.
require 'prime'   # This is a module. We'll cover these soon!

def first_n_primes(n)
  
  return "n must be an integer." unless n.is_a? Integer
  
  return "n must be greater than 0." if n <= 0
  
  prime_array ||= []
  
  prime = Prime.new
  n.times {prime_array.push(prime.next)}
  prime_array
end

first_n_primes(10)
```

Solution
```
$VERBOSE = nil    # We'll explain this at the end of the lesson.
require 'prime'   # This is a module. We'll cover these soon!

def first_n_primes(n)
  
  return "n must be an integer." unless n.is_a? Integer
  
  return "n must be greater than 0." if n <= 0
  
  prime_array ||= []
  
  prime = Prime.new
  n.times { prime_array <<prime.next }
  prime_array
end

first_n_primes(10)
```

## Nice work!

Fantastic! You really improved that code, and all it took was a little Ruby know-how.

Check out the code in the editor to the right; it's even more streamlined than what we had before!

If you remember, we had that weird-looking $VERBOSE = nil on line 1; this allowed us to use the old-style Prime.new from Ruby 1.8 without the interpreter yelling at us. In Ruby 1.9, we use Prime.instance instead, and the array magic is already built-in—we don't have to create prime_array or loop through it ourselves! (Then again, if we'd used .instance from the start, you wouldn't have gotten to do all that cool refactoring.)

The new code is on lines 8 - 10.

Instructions
Feel free to play around with the code for as long as you like, then click Save & Submit Code to complete this project!
```
require 'prime'

def first_n_primes(n)
  # Check for correct input!
  "n must be an integer" unless n.is_a? Integer
  "n must be greater than 0" if n <= 0

  # The Ruby 1.9 Prime class makes the array automatically!
  prime = Prime.instance
  prime.first n
end

first_n_primes(10)
```