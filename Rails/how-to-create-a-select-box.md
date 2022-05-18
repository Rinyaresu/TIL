# How to create a select box
[[Ruby on Rails]]

If you want to create a basic select box, you can use:
```erb
  <%= form.label :mining_type_id %>  
  <%= form.select("mining_type_id", @mining_type_options ) %>  
```
But you should use a controller according to MVC architecture like this:
```ruby
  def set_mining_type_options  
    @mining_type_options = MiningType.all.pluck(:description, :id)  
  end
```
[source](https://www.pablocantero.com/blog/2010/07/26/utilizando-o-rails-form-select/)