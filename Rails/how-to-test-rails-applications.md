# How to test rails applications
#Rails

Here we are going to test the user interaction with the system so we go to `/test/system/main_test.rb` .  Let's write the test!

So the test we are going to write will visit the index_path and see if it has a text:
```ruby
test "visiting the index" do
  visit main_index_path
  assert_selector "h1", text: "Recent"
end
```

Now let's exercise some TDD

Let's write a test to verify  that you can't create untitled articles

```ruby
test "should not create article without content" do
  visit new_article_path
  fill_in "Title", with: @article.title
  click_on "Create Article"
  assert_text "Content can't be blank"
end
```

If we run this test it will fail, so let's write the code that our test needs.

Go to `/app/models/articles/rb`
```ruby
class Article < ApplicationRecord
  validates :title, presence: true
end
```

And it is done! Now our test pass.

[[how-to-validate-your-application]]