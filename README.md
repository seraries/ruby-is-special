# Ruby is Special!

Some general notes, gotchas, and things I love about Ruby.

## Uniquely Ruby

A few of the things that make Ruby different from other programming languages.

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

Some basics about Ruby types, syntax, etc.

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


## Rails Notes

A few Rails-specific notes/factoids.

* The distinction between the two types of embedded Ruby is that `<% ... %>` executes the code inside, while `<%= ... %>` executes the code inside *and inserts the result* into the template.

## Resources

*Lots* of amazing resources informed this reference, including the following:

[Head First Ruby](https://www.amazon.com/Head-First-Ruby-Brain-Friendly-Guide/dp/1449372651)
[Ruby on Rails Tutorial](https://www.railstutorial.org/book)
