# Transition users who are not logged in to the login page

[[Ruby on Rails]]

> You must have devise configured

Go to `controllers/articles_controllers.rb`

```ruby

class ItemsController < ApplicationController
  before_action :move_to_signed_in, except: %i[index show]

...

private
  def move_to_signed_in
    redirect_to '/users/sign_in' unless user_signed_in?
    end
  end
```
