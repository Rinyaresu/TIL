# Attr_acessor
#Ruby

Let's say you have a class `Person`.

```ruby
class Person
end

person = Person.new
person.name # => no method error
```

Obviously we never defined method `name`. Let's do that.

```ruby
class Person
  def name
    @name # simply returning an instance variable @name
  end
end

person = Person.new
person.name # => nil
person.name = "Dennis" # => no method error
```

Aha, we can read the name, but that doesn't mean we can assign the name. Those are two different methods. The former is called _reader_ and latter is called _writer_. We didn't create the writer yet so let's do that.

```ruby
class Person
  def name
    @name
  end

  def name=(str)
    @name = str
  end
end

person = Person.new
person.name = 'Dennis'
person.name # => "Dennis"
```

Awesome. Now we can write and read instance variable `@name` using reader and writer methods. Except, this is done so frequently, why waste time writing these methods every time? We can do it easier.

```ruby
class Person
  attr_reader :name
  attr_writer :name
end
```

Even this can get repetitive. When you want both reader and writer just use accessor!

```ruby
class Person
  attr_accessor :name
end

person = Person.new
person.name = "Dennis"
person.name # => "Dennis"
```

Works the same way! And guess what: the instance variable `@name` in our person object will be set just like when we did it manually, so you can use it in other methods.

```ruby
class Person
  attr_accessor :name

  def greeting
    "Hello #{@name}"
  end
end

person = Person.new
person.name = "Dennis"
person.greeting # => "Hello Dennis"
```

That's it.

[source](https://stackoverflow.com/questions/4370960/what-is-attr-accessor-in-ruby)
