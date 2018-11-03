# Part 9: Add more Design Elements

### 1. Design your header <a id="1-design-your-header"></a>

In `app/views/layouts/application.html` change  

```markup
<body>
    <nav class="navbar navbar-default navbar-fixed-top" role="navigation">
```

to 

```markup
<body>
    <nav class="navbar navbar-custom navbar-fixed-top" role="navigation">
```

now that the navbar has a new class, we can design the style ourselves.

put the following code to the bottom of `app/assets/stylesheets/application.css`:

```css
.navbar-custom {
 background-color: #BBBDDD;
 border-color: #E7E7E7;
}
```

Now refresh the page and check the changes. You can try change the color or font of the header. You can check the color reference from [https://www.w3schools.com/colors/colors\_picker.asp](https://www.w3schools.com/colors/colors_picker.asp) 

Then put these lines at the bottom to style the link colors; pick your own colors to compliment your header color：

```css
.navbar-custom a { font-size: 18px; }
.navbar-custom a:hover { 
  color: #4a4a54; 
  background-color: transparent; 
  text-decoration: none;
}
```

### 2. Design your background <a id="2-design-your-table"></a>

We simply use the twitter [Bootstrap](http://getbootstrap.com/) to polish our website. 

You can change the background color by adding this to the `application.css` file

```css
body {  background-color: rgba(200, 255, 255, 50);}
```

You can use a pattern as the background, too. Reference to [http://subtlepatterns.com/](http://subtlepatterns.com/) for some patterns.  

Put your desired image file in `app/assets/images/` and add `body { background-image:url('your_image_name.png');}` to your `application.css` file.

For the image to work on heroku, edit the `config/environments/production.rb` file and change `config.assets.compile = false` to 

```ruby
config.cache_classes = true
config.serve_static_assets = true
config.assets.compile = true
config.assets.digest = true
```

### 3. __Add style to footer <a id="3-add-style-to-footer"></a>

add the lines to bottom of `app/assets/stylesheets/application.css`:

```text
footer {
  background-color: #ebebeb;
  padding: 30px 0;
}
```

try put more things into `footer`, then adjust its position.

### 4. Add style to the buttons <a id="4-add-style-to-button"></a>

open [http://localhost:3000/ideas/new](http://localhost:3000/ideas/new) and find the `Create Idea` button.

edit the bottom of your `app/views/ideas/_form.html.erb` file and change the submit button line to:

```ruby
  <%= form.submit 'Save', :class => 'btn btn-info' %>
```

Since our app uses bootstrap, we can use built in styles to quickly improve the look of our app.  Learn more here: [http://getbootstrap.com/2.3.2/base-css.html\#buttons](http://getbootstrap.com/2.3.2/base-css.html#buttons)

Go and find the button for the comments form and update its style, too.

Let your imagination go wild, adding more style your custom website!

