# How to use I18n
#Rails

If you want to internationalize your application you will need the gem I18n.

First you add the gem to your gemfile:
```ruby
gem 'rails-i18n', '~> 7.0.0' # For 7.0.0
```
or
```bash
gem install rails-i18n -v '~> 7.0.0' # For 7.0.0
```

Now you can create the `locale.rb` file in the ``/config/initializers`` directory and write this:
```ruby
# Permitted locales available for the application  
I18n.available_locales = [:en, 'pt-BR']  
	  
# Set default locale to something other than :en  
I18n.default_locale = :en
```

If you want to check the language, you can create a helper like this:
```ruby
module ApplicationHelper  
  def locale  
	if I18n.locale == :en  
	  "English"  
	else I18n.locale == 'pt-BR'  
	  "Brazilian Portuguese"  
	end  
  end  
end
```

Now put this in a view and you're done.
```erb
<p>The language used in the application is: <%= locale %></p>
```
