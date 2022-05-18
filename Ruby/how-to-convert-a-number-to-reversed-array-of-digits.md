# How to convert a number to reversed array of digits
[[Ruby]]

This was the way i figured out how to convert a number into a reverse array of digits:

```ruby
puts 12345.to_s.chars.reverse.map(&:to_i) 
```