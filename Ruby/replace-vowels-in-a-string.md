# Replace vowels in a string
[[Ruby]]

In Ruby, the **`gusb` method** replaces all occurrences of a pattern with a given replacement and returns the copy of the string. If you want to replace all the vowels in a string with asterisks, the result will be as follows:

```ruby
puts 'Fuck'.gsub(/[u]/, '*')
=> 'F*ck'
```