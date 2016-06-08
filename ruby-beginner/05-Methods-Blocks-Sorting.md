# Methods, Blocks & Sorting

## Why Methods?
```
def prime(n)
  puts "That's not an integer." unless n.is_a? Integer
  is_prime = true
  for i in 2..n-1
    if n % i == 0
      is_prime = false
    end
  end
  if is_prime
    puts "#{n} is prime!"
  else
    puts "#{n} is not prime."
  end
end

prime(2)
prime(9)
prime(11)
prime(51)
prime(97)
```

## Call It!
Defining a method is great, but it's not much use to you unless you call it. For example, if you call a method called cartoon_fox, Ruby will start looking for the method with that name and try to execute the code inside it. (If Ruby doesn't find a method called cartoon_fox, it will return a NameError. We'll cover errors in another lesson.)

You call a method just by typing its name. Remember when you saw us type puts_1_to_10 or greeting after our method definition in the last two exercises? That was us calling our methods!

Instructions
We've set up a function, array_of_10, in the editor to the right. Call it on line 5!

Solution
```
def array_of_10
  puts (1..10).to_a
end

array_of_10
```

Or
```
def array_of_10
  puts (1..10).to_a
end

array_of_10()
```

Output
```
1
2
3
4
5
6
7
8
9
10
```

## Splat!
Speaking of not knowing what to expect: your methods not only don't know what arguments they're going to get ahead of time, but occasionally, they don't even know how many arguments there will be.

Let's say you have a method, friend, that puts the argument it receives from the user. It might look something like this:
```
def friend(name):
  puts "My friend is " + name + "."
end
```
This is great for just one friend, but what if you want to print out the user's friends, without knowing how many friend names the user will put in ahead of time?

The solution: splat arguments. Splat arguments are arguments preceded by a *, which signals to Ruby: "Hey Ruby, I don't know how many arguments there are about to be, but it could be more than one."

Instructions
Click Save & Submit Code to test out the example in the editor. Feel free to play around and call what_up on as many bros as you like!

```
def what_up(greeting, *bros)
  bros.each { |bro| puts "#{greeting}, #{bro}!" }
end
 
what_up("What up", "Justin", "Ben", "Kevin Sorbo")
```

Output
```
What up, Justin!
What up, Ben!
What up, Kevin Sorbo!
["Justin", "Ben", "Kevin Sorbo"]
```

## Practice Makes Perfect
You won't become a Master Method Maker 'til you make a mess of methods. (Say that three times fast.)

def by_five?(n)
  return n % 5 == 0
end
The example above is just a reminder on how to define a method.

Instructions
Define two methods in the editor:

A greeter method that takes a single string parameter, name, and returns a string greeting that person. (Make sure to use return and don't use print or puts.)
A by_three? method that takes a single integer parameter, number, and returns true if that number is evenly divisible by three and false if not.

Solution
```
def greeter(name)
    return "Hello #{name}!"
end

def by_three?(number)
    return number % 3 == 0
end
```


## How Blocks Differ from Methods

```
# method that capitalizes a word
def capitalize(string) 
  puts "#{string[0].upcase}#{string[1..-1]}"
end

capitalize("ryan") # prints "Ryan"
capitalize("jane") # prints "Jane"

# block that capitalizes each string in the array
["ryan", "jane"].each {|string| puts "#{string[0].upcase}#{string[1..-1]}"} # prints "Ryan", then "Jane"
```

## Introduction to Sorting

Instructions
Use the .sort! method to sort the values in my_array. Magic, isn't it?
```
my_array = [3, 4, 8, 7, 1, 6, 5, 9, 2]

# Call the sort! method on my_array below.
# my_array should then equal [1, 2, 3, 4, 5, 6, 7, 8, 9].

my_array.sort!
```

## Foundations
```
# library sorting code
books = ["Charlie and the Chocolate Factory", "War and Peace", "Utopia", "A Brief History of Time", "A Wrinkle in Time"]

# How might we sort! the books in alphabetical order? (Hint, hint)

books.sort!
```

Output
```
["A Brief History of Time", "A Wrinkle in Time", "Charlie and the Chocolate Factory", "Utopia", "War and Peace"]
```

## The Combined Comparison Operator
We can also use a new operator called the combined comparison operator to compare two Ruby objects. The combined comparison operator looks like this: <=>. It returns 0 if the first operand (item to be compared) equals the second, 1 if first operand is greater than the second, and -1 if the first operand is less than the second.

A block that is passed into the sort method must return either 1, 0, -1. It should return -1 if the first block parameter should come before the second, 1 if vice versa, and 0 if they are of equal weight, meaning one does not come before the other (i.e. if two values are equal).

Instructions
Use the combined comparison operator to compare book_1 to book_2 (in that order). Before you click Save & Submit Code, what do you think the result will be?
```
book_1 = "A Wrinkle in Time"

book_2 = "A Brief History of Time"

book_1 <=> book_2
```

Output
```
1
```

## Getting Technical
What if we wanted to sort the books by title, but from Z – A, or descending order? It appears that Ruby's sort method only works for A – Z, or ascending order.

The sort method assumes by default that you want to sort in ascending order, but it accepts a block as an optional argument that allows you, the programmer, to specify how two items should be compared.

Instructions
Sort your books in descending order on line 8. Use the example of sorting in ascending order on line 4 as a guide.

```
books = ["Charlie and the Chocolate Factory", "War and Peace", "Utopia", "A Brief History of Time", "A Wrinkle in Time"]

# To sort our books in ascending order, in-place
books.sort! { |firstBook, secondBook| firstBook <=> secondBook }

# Sort your books in descending order, in-place below


```

Solution
```
books = ["Charlie and the Chocolate Factory", "War and Peace", "Utopia", "A Brief History of Time", "A Wrinkle in Time"]

# To sort our books in ascending order, in-place
books.sort! { |firstBook, secondBook| firstBook <=> secondBook }

# Sort your books in descending order, in-place below

books.sort! do |firstBook, secondBook|
    if firstBook > secondBook
        -1
    elsif firstBook < secondBook
        1
    else
        0
    end
end
```