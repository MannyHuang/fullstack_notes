// ruby version manager

# list all available versions:
$ rbenv install -l

# install a Ruby version:
$ rbenv install 2.5.0

// ruby package manager

gem install bundler



```ruby
#!/usr/bin/env ruby

=begin
indentation does not matter
function parenthesis is optional
everything is an object (including integer and strings)
  no primitives
dynamically typed
Basic Types
  Numeric
    Fixnum
    Integer
    Float
  String
  Array
  Hash
  Object
  Symbol
  Range
  RegExp
=end
# calling method on objects
4.even?

1.next.next
['rock','paper','scissors'].index('paper')

a = 1
b = 4
puts "The number #{a} is less than #{b}"

puts 'Hello'.upcase
puts 'Hello'.downcase

# replace everything that is in cap
'RubyMonk Is Pretty Brilliant'.gsub(/[A-Z]/,'0')

# execute system commands
puts `ls -lrt`


def hello1(name)
  'Hello ' + name
end
puts(hello1('satish'))


```