# How to create a rake task to setup your development environment with devise
In this example we are going to use two gems, a devise and tty-spinner. 

The tty-spinner for greater responsiveness and Devise and for an example of login with user and admin. 

So, first we install the gems like this: 

```ruby
# Devise is a flexible authentication solution for Rails based on Warden  
gem 'devise'  
  
# A terminal spinner for tasks that have non-deterministic time frame.  
gem 'tty-spinner'

```

and run `bundle install`. After that you must configure the gem devise following the [documentation](https://github.com/heartcombo/devise).


Now with everything configured let's create the task like this:
```shell
> rails g task dev setup
```

Go to `/lib/tasks/dev.rake` and  put this to call the tty-spinner gem:
```ruby
#it should be at the bottom of the code

private
 def show_spinner(msg_start, msg_end = "Completed!")  
   spinner = TTY::Spinner.new("[:spinner] #{msg_start}")  
   spinner.auto_spin  
   yield  
   spinner.success("(#{msg_end})")  
 end  
end
```

Now let's set the default password and what our code should do

```ruby
namespace :dev do  
  
 DEFAULT_PASSWORD = 123456  
  
 desc "set development environment"  
 task setup: :environment do  
   if Rails.env.development?  
	 show_spinner("Deleting BD...") { %x(rails db:drop) }  
	 show_spinner("Creating BD...") { %x(rails db:create) }  
	 show_spinner("Migrating BD...") { %x(rails db:migrate) }  
	 show_spinner("Registering default admin...") { %x(rails dev:add_default_admin) }  
	 show_spinner("Registering default user...") { %x(rails dev:add_default_user) }  
   else  
	 puts %x'You are not in development environment'  
   end  
 end
```

After that we will create the code that we mentioned above add_default_admin and add_default_user

```ruby
desc 'Add default admin'  
task add_default_admin: :environment do  
 Admin.create!(  
   email: 'admin@admin.com',  
   password: DEFAULT_PASSWORD,  
   password_confirmation: DEFAULT_PASSWORD  
 )
end
```

```ruby 
desc 'Add default user'  
task add_default_user: :environment do  
 User.create!(  
   email: 'user@user.com',  
   password: DEFAULT_PASSWORD,  
   password_confirmation: DEFAULT_PASSWORD  
 )
end
```

And the whole code will look like this:
```ruby

namespace :dev do  
  
 DEFAULT_PASSWORD = 123456  
  
 desc "set development environment"  
 task setup: :environment do  
   if Rails.env.development?  
	 show_spinner("Deleting BD...") { %x(rails db:drop) }  
	 show_spinner("Creating BD...") { %x(rails db:create) }  
	 show_spinner("Migrating BD...") { %x(rails db:migrate) }  
	 show_spinner("Registering default admin...") { %x(rails dev:add_default_admin) }  
	 show_spinner("Registering default user...") { %x(rails dev:add_default_user) }  
   else  
	 puts %x'You are not in development environment'  
   end  
 end

  desc 'Add default admin'  
  task add_default_admin: :environment do  
	Admin.create!(  
	  email: 'admin@admin.com',  
	  password: DEFAULT_PASSWORD,  
	  password_confirmation: DEFAULT_PASSWORD  
	)
  end

  desc 'Add default user'  
  task add_default_user: :environment do  
	User.create!(  
	  email: 'user@user.com',  
	  password: DEFAULT_PASSWORD,  
	  password_confirmation: DEFAULT_PASSWORD  
	)
  end

  private

  def show_spinner(msg_start, msg_end = "Completed!")  
    spinner = TTY::Spinner.new("[:spinner] #{msg_start}")  
	spinner.auto_spin  
	yield  
	spinner.success("(#{msg_end})")  
  end  
end
```

Now you can run `rails dev:setup` in your shell and the result will be this:
```bash
❯ rails dev:setup
[✔] Deleting BD... (Completed!)
[✔] Creating BD... (Completed!)
[✔] Migrating BD... (Completed!)
[✔] Registering default admin... (Completed!)
[✔] Registering default user... (Completed!)
```