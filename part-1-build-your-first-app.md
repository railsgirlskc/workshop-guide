# Part 1: Build Your First App

**Make sure you have Rails installed.** [**Follow the installation guide**](https://railsgirlskc.gitbook.io/install-guide/) to get set up.

### Get to know the tools <a id="get-to-know-the-tools"></a>

####  

#### Text Editor <a id="text-editor"></a>

* [Atom](https://atom.io/), [Sublime Text](http://www.sublimetext.com/), Vim and Emacs are examples of text editors your can use for writing code and editing files.

####  

#### Terminal \(known as Command Prompt on Windows\) <a id="terminal-known-as-command-prompt-on-windows"></a>

* Where you start the rails server and run commands.
* This is a program on your computer that you can get to through your Spotlight search on Mac \(search for “Terminal”\), or by searching for the “Command Prompt” in your programs on Windows.

####  

#### Web browser <a id="web-browser"></a>

* \(Firefox, Safari, Chrome\) for viewing your application.

Throughout this guide you will see bits of code formatted like so:

```text
some code
```

This means that the highlighted text is code and it probably needs to be either executed or inserted into one of your project files. The icon next to the highlighted text will let you know which tool to use.

For example, if you see a terminal icon next to the highlight, like in the example above, you will need to copy the code and paste it into your Terminal \(Mac\) / Command Prompt \(Windows\).

Need some reminders along the way? Check out this [handy cheatsheet for Ruby, Rails, console etc.](http://www.pragtob.info/rails-beginner-cheatsheet/)

#### Important <a id="important"></a>

It is important that you select the instructions specific to your operating system - the commands you need to run on a Windows computer are slightly different to Mac or Linux. If you’re having trouble check the Operating System switcher at the bottom of the commands. In case you’re using a cloud service \(e.g. Codenvy\), you need to run the Linux commands even if you are on a Windows computer.

### 1. __Creating the application <a id="1-creating-the-application"></a>

We’re going to create a new Rails app called _railsgirls_.

First, let’s open a terminal:

* Mac OS X: Open Spotlight, type _Terminal_ and click the _Terminal_ application.
* Windows: Click Start and look for _Command Prompt_, then click _Command Prompt with Ruby and Rails_.
* Linux \(Ubuntu/Fedora\): Search for _Terminal_ on the dash and click _Terminal_.
* Cloud service \(e.g. Codenvy\): Log in to your account, start your project and switch to its IDE \(see [installation guide](http://guides.railsgirls.com/install#using-a-cloud-service) for details\). The terminal is usually at the bottom of your browser window.

The Cheat Sheet linked in the sidebar has some tips for navigating your file tree in the terminal.  

We are going to be navigating to the `Documents` folder, and adding a new `projects` folder to keep our rails projects in.

Use `pwd` to see your current directory location in the terminal.  Use `cd` to change directories.  Your coach can help you get to the `Documents` folder.

Next, type these commands in the terminal:

```text
mkdir projects
```

You can verify that a directory named `projects` was created by running the list command: `ls`. You should see the `projects` directory in the output. Now you want to change the directory you are currently in to the `projects` folder by running:

```text
cd projects
```

You can verify you are now in an empty directory or folder by again running the `ls` command. 

Now you want to create a new app called `railsgirls` by running:

```text
rails new railsgirls
```

This will create a new app in the folder `railsgirls`, so we again want to change the directory to be inside of our rails app by running:

```text
cd railsgirls
```

If you run `ls` inside of the directory you should see folders such as `app` and `config`. You can then start the rails server by running:

```text
rails server
```

Open [http://localhost:3000](http://localhost:3000/) in your browser. If you are using a cloud service \(e.g. Codenvy\), use its preview functionality instead \(see [installation guide](http://guides.railsgirls.com/install#using-a-cloud-service) for details\).

You should see a page with the Rails logo and the heading “Yay! You’re on Rails!”, which means that your Rails app is up and running.

Notice in this window the command prompt is not visible because you are now in the Rails server, the command prompt looks like this:

```text
$
```

**Tip:** Sometimes, both in this guide and other guides online, you will see commands written with the `$` symbol at the start. This is a convention that signifies the beginning of a line that needs to be entered into your Terminal / Command Prompt. You do not need to type this symbol at the start of your commands. Your particular prompt may not have a `$` symbol at the start of it.

When the command prompt is not visible you cannot execute new commands. If you try running `cd` or another command it will not work. To return to the normal command prompt:

Hit `Ctrl+C` in the terminal to quit the server.

**Coach:** Explain what each command does. What was generated? What does the server do?

### 2. Create Idea scaffold <a id="2-create-idea-scaffold"></a>

We’re going to use Rails’ scaffold functionality to generate a starting point that allows us to list, add, remove, edit, and view things; in our case ideas.

**Coach:** What is Rails scaffolding? \(Explain the command, the model name and related database table, naming conventions, attributes and types, etc.\) What are migrations and why do you need them?

Open a new tab in your terminal, if you'd like.  This'll let you keep the app running with `rails server` in one tab while adding new features in the new tab. Don't forget to navigate the file tree to get back to `Documents/projects/railsgirls` or wherever your project is located.  On Mac, you can use `⌘T` to open a new tab in the same file location as your current tab.

```text
rails generate scaffold idea name:string description:text picture:string
```

The scaffold creates new files in your project directory, but to get it to work properly we need to run a couple of other commands to update our database and restart the server.

```text
rails db:migrate
rails server
```

Open [http://localhost:3000/ideas](http://localhost:3000/ideas) in your browser. Cloud service \(e.g. Codenvy\) users need to append ‘/ideas’ to their preview url instead \(see [installation guide](http://guides.railsgirls.com/install#using-a-cloud-service)\).

Click around and test what you got by running these few command-line commands.

![](.gitbook/assets/ideas.PNG)

### 3. Design <a id="3-design"></a>

**Coach:** Talk about the relationship between HTML and Rails. What part of views is HTML and what is Embedded Ruby \(ERB\)? What is MVC and how does this relate to it? \(Models and controllers are responsible for generating the HTML views.\)

The app doesn’t look very nice yet. Let’s do something about that. We’ll use the Twitter Bootstrap project to give us nicer styling really easily.

Open `app/views/layouts/application.html.erb` in your text editor and above the line

```ruby
<%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track': 'reload' %>
```

add

```markup
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.0.3/css/bootstrap.css">
<link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.0.3/css/bootstrap-theme.css">
```

and replace

```ruby
<%= yield %>
```

with

```markup
<div class="container">
  <%= yield %>
</div>
```

Let’s also add a navigation bar and footer to the layout. In the same file, under `<body>` add

```markup
<nav class="navbar navbar-default navbar-fixed-top" role="navigation">
  <div class="container">
    <div class="navbar-header">
      <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
        <span class="sr-only">Toggle navigation</span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
        <span class="icon-bar"></span>
      </button>
      <a class="navbar-brand" href="/">The Idea app</a>
    </div>
    <div class="collapse navbar-collapse">
      <ul class="nav navbar-nav">
        <li><a href="/ideas">Ideas</a></li>
      </ul>
    </div>
  </div>
</nav>
```

and before `</body>` add

```markup
<footer>
  <div class="container">
    Rails Girls <%= Time.now.year %>
  </div>
</footer>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js"></script>
<script src="//maxcdn.bootstrapcdn.com/bootstrap/3.0.3/js/bootstrap.js"></script>
```

Now let’s also change the styling of the ideas table. Open `app/assets/stylesheets/application.css` and at the bottom add

```css
body { padding-top: 100px; }
footer { margin-top: 100px; }
table, td, th { vertical-align: middle; border: none; }
th { border-bottom: 1px solid #DDD; }
```

Now make sure you saved your files and refresh the browser to see what was changed. Nothing changed? It might be that you’re not connected to the wifi anymore. You can change the HTML & CSS further, adding to `app/assets/stylesheets/application.css`.

**Coach:** Talk a little about CSS and layouts.

### 4. Adding picture uploads <a id="4-adding-picture-uploads"></a>

We need to install a piece of software to let us upload files in Rails.

Open `Gemfile` in the project directory using your text editor and under the line

```ruby
gem 'sqlite3'
```

add

```ruby
gem 'carrierwave'
```

**Coach:** Explain what libraries are and why they are useful. Describe what open source software is.

Hit Ctrl+C in the terminal to quit the server.

In the terminal run:

```text
bundle
```

Now we can generate the code for handling uploads. In the terminal run:

```text
rails generate uploader Picture
```

If an error is shown that the uploader cannot be found also add the following line in your `Gemfile`:

```ruby
gem 'net-ssh'
```

If you added this gem, please run in your terminal again:

```text
bundle
```

Since we added new gems we'll need to restart our server so we can pick up the changes.  `Ctrl + C` and `rails server` will restart the server.

Open `app/models/idea.rb` and under the line

```ruby
class Idea < ApplicationRecord
```

add

```ruby
mount_uploader :picture, PictureUploader
```

Open `app/views/ideas/_form.html.erb` and change

```ruby
<%= form.text_field :picture %>
```

to

```ruby
<%= form.file_field :picture %>
```

In your file it might actually say `<%= f.text_field :picture %>`, just roll with it. You'll replace it with `<%= f.form_field :picture %>` 

Images might come out turned the wrong way to fix that we need to edit some code in our `app/uploaders/picture_uploader.rb`

Uncomment the line `#include CarrierWave::MiniMagick` by removing the `#` in front.  

Then add the following:

```ruby
  process :auto_orient
  def auto_orient
    manipulate! do |img|
      img = img.auto_orient
    end
  end
```

In your browser, add new idea with a picture. When you upload a picture it doesn’t look nice because it only shows a path to the file, so let’s fix that.

To show the picture in the page of the idea itself, open `app/views/ideas/show.html.erb` and change

```ruby
<%= @idea.picture %>
```

to

```ruby
<%= image_tag(@idea.picture_url, width: 600) if @idea.picture.present? %>
```

To make sure that the picture is also shown in the overview of ideas, open `app/views/ideas/index.html.erb`. Change the line

```ruby
<%= idea.picture %>
```

to

```ruby
<%= image_tag idea.picture_url, width: '100%' if idea.picture.present? %>
```

Now refresh your browser to see what changed. Note: Some people might be using a second terminal to run the rails server continuously.

![ ](.gitbook/assets/06-ideas-styled.PNG)

Try entering a new idea with a picture. See how our CSS styles it.

**Coach:** Talk a little about HTML.

### 5. Finetune the routes <a id="5-finetune-the-routes"></a>

Open [http://localhost:3000](http://localhost:3000/) \(or your preview url, if you are using a cloud service\). It still shows the “Yay! You’re on Rails!” page. Let’s make it redirect to the ideas page.

Open `config/routes.rb` and after the first line add

```ruby
root to: redirect('/ideas')
```

Test the change by opening the root path \(that is, [http://localhost:3000/](http://localhost:3000/) or your preview url\) in your browser.

**Coach:** Talk about routes, and include details on the order of routes and their relation to static files.

### 6. Create static page in your app <a id="6-create-static-page-in-your-app"></a>

Lets add a static page to our app that will hold information about the author of this application — you!

```text
rails generate controller pages info
```

This command will create you a new folder under `app/views` called `/pages` and under that a file called `info.html.erb` which will be your info page.

It also adds a new simple route to your routes.rb.

```ruby
get "pages/info"
```

Now you can open the file `app/views/pages/info.html.erb` and add information about you in HTML. To see your new info page, take your browser to [http://localhost:3000/pages/info](http://localhost:3000/pages/info) or, if you are a cloud service user, append ‘/pages/info’ to your preview url.

### 7. Add a button to your navigation bar <a id="7-add-a-button-to-your-navigation-bar"></a>

Now that we know your new static page works, let’s make sure people can visit it by creating a button for it in the navigation bar.

Open `app/views/layouts/application.html.erb` in your text editor and under the line

```markup
<li><a href="/ideas">Ideas</a></li>
```

add

```markup
<li><a href="/pages/info">Info</a></li>
```

Refresh the page in your browser and click the newly created link to see if it works!

![What you&apos;ll see on the new Info Page.  Until you add your own info of course!](.gitbook/assets/07-info.PNG)

### 8+. What’s next? <a id="8whats-next"></a>

* Add design using HTML & CSS
* Add ratings
* Use CoffeeScript \(or JavaScript\) to add interaction
* Add picture resizing to make loading the pictures faster



