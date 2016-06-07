# A Night at the Movies

## What You'll Be Building
Keeping track of all the parts of our digital lives is a pain. Now that you know how to write Ruby, however, you can make things easy for yourself! Let's start by creating a program that will keep track of our movie ratings.

It'll do one of four things: add a new movie to a hash, update the rating for an existing movie, display the movies and ratings that are already in the hash, or delete a movie from the hash. If it doesn't receive one of those four commands, the program will output some kind of error message.

This project will give you a lot of room for creativity, but we know sometimes it can be a little disorienting to not have strict instructions. If you ever feel lost, don't hesitate to check out the example code in this exercise to help you along!

Instructions
Click Save & Submit Code to test drive our movie rating program and to start building your own.
```
movies = {
  Memento: 3,
  Primer: 4,
  Ishtar: 1
}

puts "What would you like to do?"
puts "-- Type 'add' to add a movie."
puts "-- Type 'update' to update a movie."
puts "-- Type 'display' to display all movies."
puts "-- Type 'delete' to delete a movie."

choice = gets.chomp.downcase
case choice
when 'add'
  puts "What movie do you want to add?"
  title = gets.chomp
  if movies[title.to_sym].nil?
    puts "What's the rating? (Type a number 0 to 4.)"
    rating = gets.chomp
    movies[title.to_sym] = rating.to_i
    puts "#{title} has been added with a rating of #{rating}."
  else
    puts "That movie already exists! Its rating is #{movies[title.to_sym]}."
  end
when 'update'
  puts "What movie do you want to update?"
  title = gets.chomp
  if movies[title.to_sym].nil?
    puts "Movie not found!"
  else
    puts "What's the new rating? (Type a number 0 to 4.)"
    rating = gets.chomp
    movies[title.to_sym] = rating.to_i
    puts "#{title} has been updated with new rating of #{rating}."
  end
when 'display'
  movies.each do |movie, rating|
    puts "#{movie}: #{rating}"
  end
when 'delete'
  puts "What movie do you want to delete?"
  title = gets.chomp
  if movies[title.to_sym].nil?
    puts "Movie not found!"
  else
    movies.delete(title.to_sym)
    puts "#{title} has been removed."
  end
else
  puts "Sorry, I didn't understand you."
end
```

## Setting Up
First things first: let's create a hash to hold our movies and their ratings, and let's prompt the user for input so we can eventually store movie/ratings pairs in our hash.

favorite_foods = {
    'vegetable' => 'brocolli'
}
puts "Do you like coding in Ruby?"
answer = gets.chomp
A Hash is a way of storing data by a specifiable key, as opposed to an array which can only use numbers. It is created like { } above.
puts asks a question on the command line, here we ask if you like coding in Ruby.
In order to get the user input, we have to call .chomp on gets

Solution
```
movies={:Inception=> 4}

puts "What movie do you like?"
choice = gets.chomp
```

## The Case Statement
Good work! Now we'll want to create the main body of our program: the case statement, which will decide what actions to take based on what the user types in.

if and else are powerful, but we can get bogged down in ifs and elsifs if we have a lot of conditions to check. Thankfully, Ruby provides us with a concise alternative: the case statement. The syntax looks like this:

Below your existing code, create a case statement for the choice variable with the following when conditions:

when "add", please puts "Added!"
when "update", please puts "Updated!"
when "display", please puts "Movies!"
when "delete", please puts "Deleted!"
Otherwise (i.e. else), please puts "Error!"
Don't forget the end statement after your case/when lines.

Solution
```
movies={"Inception" => 4}

puts "What would you like to do?"
choice = gets.chomp

case choice
when "add" then puts "Added!"
when "update" then puts "Updated!"
when "display" then puts "Movies!"
when "delete" then puts "Deleted!"
else  puts "Error!"
end
```

## Prompting: Redux!
Great! Let's build out each part of the case, one step at a time. We'll start with the add branch.

Instructions
Inside your when "add" block, remove the puts "Added!" statement.
In its place, prompt the user for a movie title. Save the result in a new variable called title. (*Your code already has an example of how to do this!)
Next, prompt the user for the rating of the movie. Save that in a new variable called rating.
Add that movie/rating pair to the movies hash and puts a message indicating the pair was added. (No need for to_sym or to_i just yet!)
Check the hint if you need help!

Solution
```
movies={"Inception" => 4}

puts "What would you like to do?"
choice = gets.chomp

case choice
when "add"  
    puts "What movie do you like?"
    title = gets.chomp
    puts "What's the rating? (Type a number 0 to 4.)"
    rating = gets.chomp
    movies[title] = rating
    puts "Movie #{title} has added!"
when "update" then puts "Updated!"
when "display" then puts "Movies!"
when "delete" then puts "Deleted!"
else  puts "Error!"
end
```

## Not My Type
Perfect! Our program is really coming along.

You might have wondered how we're going to get our movies and ratings from the user—which come in as strings—into the hash where we want our movies to be symbols and our ratings to be integers. Built-in Ruby magic to the rescue!

Ruby's .to_sym method can convert a string to a symbol, and .to_i will convert a string to an integer.

Instructions
Call .to_sym on your title and .to_i on your rating so that your movie titles are stored as symbols in the hash and the associated ratings are stored as integers.

Solution
```
movies={"Inception" => 4}

puts "What would you like to do?"
choice = gets.chomp

case choice
when "add"  
    puts "What movie do you like?"
    title = gets.chomp
    puts "What's the rating? (Type a number 0 to 4.)"
    rating = gets.chomp
    movies[title.to_sym] = rating.to_i
    puts "Movie #{title} has added!"
when "update" then puts "Updated!"
when "display" then puts "Movies!"
when "delete" then puts "Deleted!"
else  puts "Error!"
end
```

##  Error! Error!
All right! We're nearly done with the "add" part of our case. The final thing we'll want to do is perform a check to see whether the movie to be added is already in the hash.

To do this, we'll add an if/else statement.

Instructions
Add an if/else statement to the add branch of your case. If the movie isn't already in the hash (that is, if movies[title.to_sym] is nil), it should add the movie/rating pair; otherwise, it should puts that the movie already exists and not add anything to the hash. Make sure to test it!

```
movies={"Inception" => 4}

puts "What would you like to do?"
choice = gets.chomp

case choice
when "add"  
    puts "What movie do you like?"
    title = gets.chomp
    if movies[title.to_sym].nil?
        puts "What's the rating? (Type a number 0 to 4.)"
        rating = gets.chomp
        movies[title.to_sym] = rating.to_i
        puts "Movie #{title} has added!"
    else
        puts "Moviel has already been added!"
    end
when "update" then puts "Updated!"
when "display" then puts "Movies!"
when "delete" then puts "Deleted!"
else  puts "Error!"
end
```

## Update
Perfect! Let's move on to the next branch of our case statement, which handles updating an existing movie in the hash. (This should be very similar to the work we did in the "add" branch!) We'll do this in three steps:

Instructions
Inside your when "update" block, remove the puts "Updated!" statement.
Prompt the user for a movie title. Store it in title.
if the movies[title] is nil, then the movie is not in the hash. Please puts a string telling the user of their error.
Otherwise (else), we need to update the movies hash. Prompt the user for a new rating. Set the movie's rating to that new value.
Make sure to test it out!

Solution
```
movies={"Inception" => 4}

puts "What would you like to do?"
choice = gets.chomp

case choice
when "add"  
    puts "What movie do you like?"
    title = gets.chomp
    if movies[title.to_sym].nil?
        puts "What's the rating? (Type a number 0 to 4.)"
        rating = gets.chomp
        movies[title.to_sym] = rating.to_i
        puts "Movie #{title} has added!"
    else
        puts "Moviel has already been added!"
    end
when "update"
    puts "What movie do you want to update?"
    title = gets.chomp
    if movies[title.to_sym].nil?
        puts "The movie you input is not here!"
    else
        puts "What's the rating? (Type a number 0 to 4.)"
        rating = gets.chomp
        movies[title.to_sym] = rating.to_i
        puts "Movie #{title} has been updated!"
    end
    
    
when "display" then puts "Movies!"
when "delete" then puts "Deleted!"
else  puts "Error!"
end
```

## Display

Solution
```
movies={Inception: 4}

puts "What would you like to do?"
choice = gets.chomp

case choice
when "add"  
    puts "What movie do you like?"
    title = gets.chomp
    if movies[title.to_sym].nil?
        puts "What's the rating? (Type a number 0 to 4.)"
        rating = gets.chomp
        movies[title.to_sym] = rating.to_i
        puts "Movie #{title} has added!"
    else
        puts "Moviel has already been added!"
    end
when "update"
    puts "What movie do you want to update?"
    title = gets.chomp
    if movies[title.to_sym].nil?
        puts "The movie you input is not here!"
    else
        puts "What's the rating? (Type a number 0 to 4.)"
        rating = gets.chomp
        movies[title.to_sym] = rating.to_i
        puts "Movie #{title} has been updated!"
    end
    
    
when "display"
    movies.each do |movie, rating|
        puts "#{movie}: #{rating}"
    end

when "delete" then puts "Deleted!"
else  puts "Error!"
end
```

## Delete
Almost there! Let's handle the "delete" part of our case statement, which will remove whatever key the user specifies from the hash. (This will be very similar to what we did for "add" and "update.")

Ruby makes it easy to remove a movie/rating pair from our hash: we just write movies.delete(title)!

Instructions
Go ahead and remove the puts "Deleted!" when the user types "delete".
Get the title from the user.
Include an if/else statement that puts an error if the movie's not in the hash; if it's there, use .delete to remove it as shown above.
Make sure to test it out!
```
movies={Inception: 4}

puts "What would you like to do?"
choice = gets.chomp

case choice
when "add"  
    puts "What movie do you like?"
    title = gets.chomp
    if movies[title.to_sym].nil?
        puts "What's the rating? (Type a number 0 to 4.)"
        rating = gets.chomp
        movies[title.to_sym] = rating.to_i
        puts "Movie #{title} has added!"
    else
        puts "Moviel has already been added!"
    end
when "update"
    puts "What movie do you want to update?"
    title = gets.chomp
    if movies[title.to_sym].nil?
        puts "The movie you input is not here!"
    else
        puts "What's the rating? (Type a number 0 to 4.)"
        rating = gets.chomp
        movies[title.to_sym] = rating.to_i
        puts "Movie #{title} has been updated!"
    end
    
    
when "display"
    movies.each do |movie, rating|
        puts "#{movie}: #{rating}"
    end

when "delete"
    puts "What movie do you want to delete?"
    title = gets.chomp
    if movies[title.to_sym].nil?
        puts "The movie you input is not here!"
    else
        movies.delete(title)
        "Movie #{title} has been deleted!"
    end
else  puts "Error!"
end
```

