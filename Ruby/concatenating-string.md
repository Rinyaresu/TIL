# Concatenating string

To concatenate Strings, we can use the methods + or <<

```ruby
name = "Kaique"
=> "Kaique"
surname = "Linhares"
=> "Linhares"
name + surname
=> "KaiqueLinhares"
name + " " +surname
=> "Kaique Linhares"
name.object_id
=> 685520
name << " "
=> "Kaique "
name << surname
=> "Kaique Linhares"
name.object_id
=> 685520
```

The difference is that + returns us a new object, while << does a memory reallocation and works on the object where the content is being added, as demonstrated above, without generating a new object.
