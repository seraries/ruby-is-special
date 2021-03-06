# Ruby is Special!  
Some general notes, gotchas, and things I love about Ruby. Note that this is a work in progress. I'll add to it as I get time, and as Ruby continues to unveil her mysterious wonders...

## Uniquely Ruby

A few of the things that make Ruby different from other programming languages.

### Everything is an Object

That includes numbers; therefore numbers have methods associated with them. For instance, the methods `.times` and `.even?` as demonstrated below.

```ruby
3.times {print "Hola!"} # prints Hola!Hola!Hola!
puts 12.even? # prints true
```

### Symbols

### Blocks

### Inline if

Instead of using a simple `if` block, Ruby lets you write a statement that is only evaluated if the statement following it is true. So instead of this:

```ruby
if !x.empty?
  puts "x is not empty"
end
```

You can write this:

```ruby
puts "x is not empty" if !x.empty?
```

### Unless

Ruby also allows you to use `unless` instead of `if !`. You can use it in block form:

```ruby
unless x.empty?
  puts "x is not empty"
end
```

Or in inline form like the `if` statement above:

```ruby
  puts "x is not empty" unless x.empty?
```

## General Notes

Some basics about Ruby types, syntax, conventions, etc.

### Typing

Ruby is a dynamically-typed language so you do not need to declare a type for each variable, and the same variable can hold different types throughout its lifetime.

```ruby
x = "Hello World"
x = 44
x = ["Hiya", "Hola", "Bonjour"]
```
### Conventions

#### Naming

* Variables should be named using snake_case: `new_variable`.
* Methods should be named using snake_case as well: `def new_method(input_value)`
* Methods that return a boolean value should end in a `?`: `def is_cool?(temp)`
* Setter methods should end in a `=`: `def name=(input_value)`
* Class and module names follow CapWords (or CamelCase) convention: `class NewClass`
* File names follow snake_case: `new_file.rb`

#### Methods

If a method doesn't take an argument, it is conventional to leave off the `()` at the end of both the method call and the method definition.

```ruby
def say_hello
  puts "Hello!"
end

say_hello  # prints Hello!
```

### Ternary Operator

Ruby, like Java and many other languages, allows you to write a succinct "if/else" conditional statement using the ternary operator, like so:

```ruby
params[:session][:remember_me] == '1' ? remember(user) : forget(user)
```

An expression that uses the ternary operator consists of the following parts:

```
boolean? ? do_one_thing : do_something_else
```

If the boolean expression evaluates to true, do the thing listed immediately following the `?`; if it evaluates to false, do the thing listed after the `:`. 

In Ruby, there are a couple other cool things you can do with the ternary operator. You can use it in an assignment:

```ruby
var = boolean? ? foo : bar
```

And you can use it as a function's return value:

```ruby
def foo
  do_stuff
  boolean? ? "bar" : "baz"
end
```

Since Ruby implicitly returns the value of the last expression in a function, here the `foo` method returns "bar" or "baz" depending on whether boolean? is true or false.

## Gotcha!

Unexpected things about Ruby. Good to know these things to avoid bugs/logical errors.

### Truthy and Falsey

Everything **except _nil_ and _false_** is truthy in a boolean context in Ruby.

### Single-quoted Strings

* Unlike with double-quoted strings, Ruby won’t interpolate into single-quoted strings.

```ruby
name = "Thom"
puts "#{name} Paine"  # prints Thom Paine
puts '#{name} Paine'  # prints #{name} Paine
```

* Single-quoted strings are often useful because they are truly literal, containing *exactly* the characters you type. E.g.,

```ruby
name = 'Thom Paine \n'
print name  # prints Thom Paine \n
name = "Thom Paine \n"
print name  # prints Thom Paine and then a newline
```

### Array Methods

The built-in array methods do not change the array, but rather return a modified copy of the array.

```ruby
a = [8, 23, 15]
puts a.sort  # prints [8, 15, 23]
puts a  # prints [8, 23, 15]
```

If you want to mutate the array, add a bang (`!`) to the end of the method:

```ruby
a = [8, 23, 15]
puts a.sort!  # prints [8, 15, 23]
puts a  # prints [8, 15, 23]
```

### Assignment in a boolean clause

Let's look at a potentially confusing statement:

```ruby
if (user_id = session[:user_id])
```

Note that this is not a comparison (which would use == instead of a single equals sign), but rather this means "If session of user id exists (while setting user id to session of user id)..."

## Rails Notes

A few Rails-specific notes/factoids.

* The distinction between the two types of embedded Ruby is that `<% ... %>` executes the code inside, while `<%= ... %>` executes the code inside *and inserts the result* into the template.

## Resources

*Lots* of amazing resources informed this reference, including the following:

[Head First Ruby](https://www.amazon.com/Head-First-Ruby-Brain-Friendly-Guide/dp/1449372651)

[Ruby on Rails Tutorial](https://www.railstutorial.org/book)
