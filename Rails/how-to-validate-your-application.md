# How to validate your application

> You must have scaffolding ready

This snippet validate if all textfields contain something:
```ruby
validates :title, :description, :image_url, presence: true
```

And this snippet it doesn't let you put a price below 0.01:
```ruby
validates :price, numericality: { greater_than_or_equal_to: 0.01 }
```

This valid if the title is unique:
```ruby
validates :title, uniqueness: true
```

And this big code validates if your url ends with .gif .jpg or .png
```ruby
validates :image_url, allow_blank: true, format: {
  with: %r{\.(gif|jpg|png)\z}i,
  message: 'must be a URL for GIF, JPG or PNG image.'
}
```

And this is all the code

```ruby
class Product < ApplicationRecord
  validates :title, :description, :image_url, presence: true
  validates :price, numericality: { greater_than_or_equal_to: 0.01 }
  validates :title, uniqueness: true
  validates :image_url, allow_blank: true, format: {
	with: %r{\.(gif|jpg|png)\z}i,
	message: 'must be a URL for GIF, JPG or PNG image.'
  }
end
```

