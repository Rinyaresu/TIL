# render another page to not pollute application.html.erb

 [[Ruby on Rails]]

Instead of writing the html in application.html.erb like this

`views/layout/application.html.erb`

```html
<body>
 <nav class="navbar navbar-expand-lg navbar-light bg-light">
   <div class="container-fluid">
     <a class="navbar-brand" href="#">Navbar w/ text</a>
     <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarText" aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">
       <span class="navbar-toggler-icon"></span>
     </button>
     <div class="collapse navbar-collapse" id="navbarText">
       <ul class="navbar-nav me-auto mb-2 mb-lg-0">
         <li class="nav-item">
           <a class="nav-link active" aria-current="page" href="#">Home</a>
         </li>
         <li class="nav-item">
           <a class="nav-link" href="#">Features</a>
         </li>
         <li class="nav-item">
           <a class="nav-link" href="#">Pricing</a>
         </li>
       </ul>
       <span class="navbar-text">
         Navbar text with an inline element
       </span>
     </div>
   </div>
 </nav>
</body>
```

you can create a shared directory and the file like this

```bash
mkdir views/shared
touch _navigation.html.erb
```

now we copy code from `application.html.erb` to `_navigation.html.erb`
</br>
the final step is to change the application.html.erb
`application.html.erb`

```erb
 <body>
 <%= render "shared/navigation" %>
 <%= yield %>
 </body>
```
