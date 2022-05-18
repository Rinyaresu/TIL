# Freezing objects
[[Ruby]]

If, by chance, we explicitly want an object not to be modified, we can use the freeze method, which will raise a FrozenError exception if we try to change the object in any way:

```ruby
nick = "rinyaresu"
=> "rinyaresu"
nick.freeze
=> "rinyaresu"
nick[0] = "L"
FrozenError (can't modify frozen String: "rinyaresu")
```

We don't have an unfreeze method, but we can generate a copy of our frozen object with dup, and thus make modifications to that new copy:

```ruby
nick = "rinyaresu"
=> "rinyaresu" 

nick.freeze
=> "rinyaresu" 

new_nick = nick.dup 
=> "rinyaresu" 

new_nick[0] = "l"
=> "linyaresu"
```

It is important to note that a table of frozen Strings is created, so every frozen String will be the same object:

```ruby
s1 = "rinyaresu".freeze
=> "rinyaresu"
s1.object_id
=> 1307440
s2 = "rinyaresu".freeze
=> "rinyaresu"
s2.object_id
=> 1307440
```