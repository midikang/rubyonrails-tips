# The Zen of Ruby

As a language, Ruby prioritizes programmer productivity over program optimization. This means that Ruby may not always run a program in the fastest way possible, but it strives to be a language that programmers (like you!) find easy and fun to use. The more intuitive a language's syntax is, the more productive its users can be. You're in control, not the machine!

Check out the code in the editor. It looks almost just like English, doesn't it?

## case 
```
case language
when "JS"
  puts "Websites!"
when "Python"
  puts "Science!"
when "Ruby"
  puts "Web apps!"
else
  puts "I don't know!"
end
```

```
case language
  when "JS" then puts "Websites!"
  when "Python" then puts "Science!"
  when "Ruby" then puts "Web apps!"
  else puts "I don't know!"
end
```

```
puts "Hello there!"
greeting = gets.chomp

# Add your case statement below!
case greeting
when "English"
    puts "Hello!"
when "French"
    puts "Bonjour!"
when "German"
    puts "Guten Tag!"
when "Finnish"
    puts "Haloo!"
else
    puts "I don't know that language!"
end
```

```
puts "Hello there!"
greeting = gets.chomp

# Add your case statement below!
case greeting
when "English" then    puts "Hello!"
when "French" then    puts "Bonjour!"
when "German" then     puts "Guten Tag!"
when "Finnish" then     puts "Haloo!"
else    puts "I don't know that language!"
end
```

## Conditional Assignment
We've seen that we can use the = operator to assign a value to a variable. But what if we only want to assign a variable if it hasn't already been assigned? For this, we can use the conditional assignment operator: ||=. It's made up of the or (||) logical operator and the normal = assignment operator.

```
favorite_book = nil
puts favorite_book

favorite_book ||= "Cat's Cradle"
puts favorite_book

favorite_book ||= "Why's (Poignant) Guide to Ruby"
puts favorite_book

favorite_book = "Why's (Poignant) Guide to Ruby"
puts favorite_book
```
Run the code in the editor. Here's what's happening:

- favorite_book is set to nil, which is Ruby for "nothing." When you try to puts it to the screen, you get exactly that: nothing!
- Now our variable is conditionally set to "Cat's Cradle." Since the value of the variable was nothing before, Ruby goes ahead and sets it, so you see "Cat's Cradle" printed out.
- We try conditional assignment again, this time with "Why's (Poignant) Guide to Ruby." But wait! Our variable already has a value, "Cat's Cradle," so it stays set to that value and that's what we see printed out.
- Finally, we use regular old assignment to tell Ruby to reset favorite_book to "Why's (Poignant) Guide to Ruby," which it gladly does.
- 

```
# Write your code on line 2!
favorite_language ||= "Ruby!"
puts favorite_language
```

## Implicit Return
We know that methods in Ruby can return values, and we ask a method to return a value when we want to use it in another part of our program. What if we don't put a return statement in our method definition, though?

For instance, if you don't tell a JavaScript function exactly what to return, it'll return undefined. For Python, the default return value is None. But for Ruby, it's something different: Ruby's methods will return the result of the last evaluated expression.

This means that if you have a Ruby method like this one:
```
def add(a,b)
  return a + b
end
```
You can simply write:
```
def add(a,b)
  a + b
end
```
And either way, when you call add(1,1), you'll get 2. Powerful stuff!

Modify the code in the editor to use an implicit return.
```
def multiple_of_three(n)
  return n % 3 == 0 ? "True" : "False"
end
```
after modification
```
def multiple_of_three(n)
   n % 3 == 0 ? "True" : "False"
end
```

## Short-Circuit Evaluation
Check out the code in the editor, then click Save & Submit Code. Because only false and nil are false values in Ruby, both strings are treated as true. Ruby knows true || anything is true, so in a || b, it only evaluates a. Since it might encounter a false in the b part of a && b, however, it has to evaluate b, which we see in the result!
```
def a
  puts "A was evaluated!"
  return true
end

def b
  puts "B was also evaluated!"
  return true
end

puts a || b
puts "------"
puts a && b
```

Output
```
A was evaluated!
true
------
A was evaluated!
B was also evaluated!
true
nil
```

## The Right Tool for the Job

Sooner or later, you're going to need to perform a repetitive task in your programs. Many programming languages allow you to do this with a for loop, and while Ruby does include for loops, there are better tools available to us.

If we want to do something a specific number of times, we can use the .times method, like so:
```
5.times { puts "Odelay!" }
# Prints 5 "Odelay!"s on separate lines
```

If we want to repeat an action for every element in a collection, we can use .each:
```
[1, 2, 3].each { |x| puts x * 10 }
# Prints 10, 20, 30 on separate  lines
```

Let's get a little inventive. Write a loop that only puts the even values of my_array. (Bonus points if you use a one-line if!)

