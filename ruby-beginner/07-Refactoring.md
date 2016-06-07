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
```
my_array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

Solution
```
my_array = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

my_array.each {|x| puts x if x%2==0}
```

## Up the Down Staircase
We might use .upto to print out a specific range of values:
```
95.upto(100) { |num| print num, " " }
# Prints 95 96 97 98 99 100
```
and we can use .downto to do the same thing with descending values.

Do you think .upto and .downto work on the alphabet? Only one way to find out!

Use .upto to puts the capital letters "L" through "P".

(Make sure to use puts and not print, so each letter is on its own line!)

Solution
```
# Write your code below!

"L".upto("P") { |char| puts char}
```

Output
```
L
M
N
O
P
"L"
```

## Call and Response
Ruby is less concerned about what kind of thing an object is and only really cares about what method calls it responds to.

Remember when we mentioned that symbols are awesome for referencing method names? Well, .respond_to? takes a symbol and returns true if an object can receive that method and false otherwise. For example,
```
[1, 2, 3].respond_to?(:push)
```
would return true, since you can call .push on an array object. However,
```
[1, 2, 3].respond_to?(:to_sym)
```
would return false, since you can't turn an array into a symbol.

### Instructions
Rather than checking to see if our age variable is an integer, check to see if it will .respond_to? the .next method. (.next will return the integer immediately following the integer it's called on, meaning 4.next will return 5.)

```
age = 26

# Add your code below!

age.respond_to?(:next)
```

Output
```
true
```

## Being Pushy
Speaking of pushing to arrays, Ruby has some nice shortcuts for common method names. As luck would have it, one is for .push!

Instead of typing out the .push method name, you can simply use <<, the concatenation operator (also known as "the shovel") to add an element to the end of an array:
```
[1, 2, 3] << 4
# ==> [1, 2, 3, 4]
```

Good news: it also works on strings! You can do:
```
"Yukihiro " << "Matsumoto"
# ==> "Yukihiro Matsumoto"
```

### Instructions
Update the code in the editor to use the concatenation operator instead of .push and +.

```
alphabet = ["a", "b", "c"]
alphabet.push("d") # Update me!

caption = "A giraffe surrounded by "
caption += "weezards!" # Me, too!
```

Solution
```
alphabet = ["a", "b", "c"]
alphabet << "d" # Update me!

caption = "A giraffe surrounded by "
caption << "weezards!" # Me, too!
```

## String Interpolation
You can always use plain old + or << to add a variable value into a string:
```
drink = "espresso"
"I love " + drink
# ==> I love espresso
"I love " << drink
# ==> I love espresso
```

But if you want to do it for non-string values, you have to use .to_s to make it a string:
```
age = 26
"I am " + age.to_s + " years old."
# ==> "I am 26 years old."
"I am " << age.to_s << " years old."
# ==> "I am 26 years old."
```
This is complicated, and complicated is not the Ruby way. A better way to do this is with string interpolation. The syntax looks like this:
```
"I love #{drink}."
# ==> I love espresso.
"I am #{age} years old."
# ==> I am 26 years old.
```
All you need to do is place the variable name inside #{} within a string!

### Instructions
Remove the concatenation operator and rewrite the code to use #{thing}.

You will want to puts one complete string on line 6.

```
favorite_things = ["Ruby", "espresso", "candy"]

puts "A few of my favorite things:"

favorite_things.each do |thing|
  puts "I love " << thing << "!"
end
```

Solution
```
favorite_things = ["Ruby", "espresso", "candy"]

puts "A few of my favorite things:"

favorite_things.each do |thing|
  puts "I love #{thing}!"
end
```

## One-Liners

### Refactor the contents of the editor to just one line of code.
```
if 1 < 2
  puts "One is less than two!" 
end
```

Solution
```
puts "One is less than two!" if 1 < 2
```

## The Ternary Operator
```
if 1 < 2
  puts "One is less than two!"
else
  puts "One is not less than two."
end
```

Solution
```
puts 1 < 2 ? "One is less than two!" : "One is not less than two."
```

## In Case of Many Options
Excellent. Regular if/else statements aren't the only ones we can refactor, though—a chain of if/elsif/else statements can clean up really nicely, too!

Instructions
Refactor the if/elsif/else statement in the editor into a tidy case statement.
```
puts "What's your favorite language?"
language = gets.chomp

if language == "Ruby"
  puts "Ruby is great for web apps!"
elsif language == "Python"
  puts "Python is great for science."
elsif language == "JavaScript"
  puts "JavaScript makes websites awesome."
elsif language == "HTML"
  puts "HTML is what websites are made of!"
elsif language == "CSS"
  puts "CSS makes websites pretty."
else
  puts "I don't know that language!"
end
```

Solution
```
puts "What's your favorite language?"
language = gets.chomp

case language
when "Ruby" then puts "Ruby is great for web apps!"
when "Python" then  puts "Python is great for science."
when  "JavaScript" then  puts "JavaScript makes websites awesome."
when "HTML" then  puts "HTML is what websites are made of!"
when "CSS" then puts "CSS makes websites pretty."
else puts "I don't know that language!"
end
```

## Conditional Assignment
Create a variable called favorite_animal and conditionally assign it to a string containing the name of your favorite animal.
```
favorite_animal ||= "Dog"
```

## Implicit Return
Write a method, square, that takes a number as an argument and implicitly returns the square of that number.
```
def square(num)
    num * num
end
```

## 'For' Shame!
All right! Last one: let's do something about the decidedly un-Ruby for loop in the editor.
```
10.times do
  puts "Knock knock."
  puts "Who's there?"
end
```

Instructions
Let's finish up by refactoring the for loop on the right to use .times instead.
```
for i in (1..3)
  puts "I'm a refactoring master!"
end
```

Solution
```
3.times do
    puts "I'm a refactoring master!"
end
```

