
[String](https://rubymonk.com/learning/books/1-ruby-primer/chapters/5-strings/lessons/31-string-basics#solution2466)

def string_length_interpolater(incoming_string)
  "The string you just gave me has a length of #{incoming_string.length}"
end

## Search in a String
```
"[Luke:] I can’t believe it. [Yoda:] That is why you fail.".include?("Yoda")
```

```
"Ruby is a beautiful language".start_with?("Ruby")
```

```
"I can't work with any other language but Ruby".end_with?('Ruby')
```

**Notes**
Are you getting the hang of the Ruby API? The previous three methods all ended with a '?'. It is conventional in Ruby to have '?' at the end of the method if that method returns only boolean values. Though it is not mandated by the syntax, this practice is highly recommended as it increases the readability of code.

Try and find out the index of 'R' in the string below:
```
"I am a Rubyist".index("R")
```

## String case change
Let's start with converting a string in lower case to upper case.
```
puts 'i am in lowercase'.upcase
```

Similarly, one can convert a string to lower case as well. Ruby calls this method downcase. Convert the string below into lower case.
```
'This is Mixed CASE'.downcase
```

On a parting note, let us touch on an interesting method. When you encounter a mixed cased string, Ruby provides a way to swap the case of every character in it i.e. this method would convert "I Am MixEd" to "i aM mIXeD". Try to figure this method out and tell us if you ever come across a scenario where you find use for this. It might make a good story for a rainy night!
```
"ThiS iS A vErY ComPlEx SenTeNcE".swapcase
```

# 1.2 Advanced String Operations
[Origin URL](https://rubymonk.com/learning/books/1-ruby-primer/chapters/5-strings/lessons/8-string-advanced)

## Splitting Strings
```
'Fear is the path to the dark side'.split(' ')
```

## Concatenating Strings
```
'Ruby' + 'Monk'
```

```
"Ruby".concat("Monk")
```

Let's try a more widely used alias. You can use '<<' just like '+', but in this case the String object 'Monk' will be appended to the object represented by 'Ruby' itself. Share this on TwitterIn the first case of using '+', the original string is not modified, as a third string 'RubyMonk' is created. This can make a huge difference in your memory utilization, if you are doing really large scale string manipulations. Change the code above to use '<<' and see all the tests passing again.
```
"Ruby"<<"Monk"
```

## Replacing a substring
```
"I should look into your problem when I get time".sub('I','We')
```

The method above only replaced the first occurrence of the term we were looking for. In order to replace all occurrences we can use a method called gsub which has a global scope.
```
"I should look into your problem when I get time".gsub('I','We')
STDOUT:

We should look into your problem when We get time
```

If you haven't come across the term Regular Expression before, now is the time for introductions. Regular Expressions or RegExs are a concise and flexible means for "matching" particular characters, words, or patterns of characters. In Ruby you specify a RegEx by putting it between a pair of forward slashes (/). Now let's look at an example that replaces all the vowels with the number 1:
```
'RubyMonk'.gsub(/[aeiou]/,'1')
STDOUT:

R1byM1nk
```

Could you replace all the characters in capital case with number '0' in the following problem?
```
'RubyMonk Is Pretty Brilliant'.gsub(/[A-Z]/,'0')

STDOUT:

0uby0onk 0s 0retty 0rilliant
```

## Find a substring using RegEx
Here is how you find the characters from a String which are next to a whitespace:
```
'RubyMonk Is Pretty Brilliant'.match(/ ./)
STDOUT:

 I
```

As you can see in the output, the method just returns the first match rather than all the matches. In order to find further matches, we can pass a second argument to the match method. When the second parameter is present, it specifies the position in the string to begin the search. Let's find the second character in the string 'RubyMonk Is Pretty Brilliant' preceded by a space, which should be 'P'.
```
>> 'RubyMonk Is Pretty Brilliant'.match(/ ./, 10)                                                                      
=> #<MatchData " P">
```

# 2.0 Boolean Expressions in Ruby

Ruby also has an unless keyword that can be used in places where you want to check for a negative condition. unless x is equivalent to if !x. Here is an example:
```
age = 10
unless age >= 18
    puts "Sorry, you need to be at least eighteen to drive a car. Grow up fast!"
end
```
## The ternary operator

In english, "ternary" is an adjective meaning "composed of three items." In a programming language, a ternary operator is simply short-hand for an if-then-else construct.

In Ruby, ? and : can be used to mean "then" and "else" respectively. Here's the first example on this page re-written using a ternary operator.

def check_sign(number)
  number > 0 ? "#{number} is positive" : "#{number} is negative"
end

## Truthiness of objects in Ruby

The conditional statements if and unless can also use expressions that return an object that is not either true or false.

In such cases, the objects false and nil equates to false. Every other object like say 1, 0, "" are all evaluated to be true. Here is a demonstration:

```
if 0
  puts "Hey, 0 is considered to be a truth in Ruby" 
end
```
