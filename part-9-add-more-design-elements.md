# Part 9: Add more Design Elements

### 1. Design your header <a id="1-design-your-header"></a>

In `application.html` change  

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

Now refresh the page and check the changes. You can try change the color or font of the header. You can check the color reference from [https://pinetools.com/image-color-picker](https://pinetools.com/image-color-picker), or even the google search result for 'color picker' has one built in.

Then put these lines at the bottom to style the link colors; pick your own colors to compliment your header color：

```css
.navbar-custom a { font-size: 18px; }
.navbar-custom a:hover { 
  color: #4a4a54; 
  background-color: transparent; 
  text-decoration: none;
}
```

**Coach:** explain the 4 states of a link

### 2. Design your table <a id="2-design-your-table"></a>

We simply use the twitter [Bootstrap](http://getbootstrap.com/) to polish our table. Find this line from app/views/ideas/index.html.erb and replace:

```text
<table>
```

with

```text
<table class="table">
```

Modify size of the picture using the following lines

```text
<%= image_tag(idea.picture_url, :width => 600) if idea.picture.present? %>
```

try to change the width and see what’s gonna happen

add the following lines to the bottom of file app/assets/stylesheets/ideas.css.scss:

```text
.container a:hover {
  color: #f55e55;
  text-decoration: none;
  background-color: rgba(255, 255, 255, 0);
}
```

try add some background style with property `background-image`, reference to [http://subtlepatterns.com/](http://subtlepatterns.com/) for some patterns.

### 3. __Add style to footer <a id="3-add-style-to-footer"></a>

add the lines to bottom of app/assets/stylesheets/application.css:

```text
footer {
  background-color: #ebebeb;
  padding: 30px 0;
}
```

try put more things into `footer`, then adjust it’s position.

### 4. Add style to button <a id="4-add-style-to-button"></a>

open [http://localhost:3000/ideas/new](http://localhost:3000/ideas/new) and find the `Create Idea` button.

add these lines to app/assets/stylesheets/ideas.css.scss

```text
.container input[type="submit"] {
  height: 30px;
  font-size: 13px;
  background-color: #f55e55;
  border: none;
  color: #fff;
}
```

**Coach:** explain how to use `border` in css, try modify the style of button like round the corner, add shadow or color etc.

