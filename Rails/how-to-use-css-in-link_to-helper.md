# How to use ccs in link_to helper
#Rails

If you are using bootstrap, and want to create a button using classes you can try this:

```html
<a class="btn btn-primary btn-lg" href="#" role="button">Coins</a>
```

But if you are using link_to helper to create the links you can do this:

```erb 
<%= link_to 'Coins', coins_path, class:"btn btn-primary btn-lg, role:"button" %>  
```

You just need to change `=` to `:` turning the class into a hash.