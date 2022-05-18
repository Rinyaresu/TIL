# Substrings
[[Ruby]]

Substrings are parts of a String.

To get some substrings, we can treat the String as an Array:

```ruby
str = "string"
=> "string"

str[0..2]
=> "str"

str[3..4]
=> "in"

str[4..5]
=> "ng"
```

You can also use negative indices to retrieve the positions relative to the end of the String:

```ruby
str[-4..3]
=> "ri" 

str[-5..2]
=> "tr"

str[-4..-3]
=> "ri"

str[-3..-1]
=> "ing"

str[-3..]
=> "ing"

str[-1]
=> "g"

str[-2]
=> "n"
```