# Part 7: Create Users and Authentication with Devise

### 1. Add devise gem <a id="1-add-devise-gem"></a>

Open up your `Gemfile` and add this line

```ruby
gem 'devise'
```

and run

```text
bundle install
```

to install the gem. **Also remember to restart the Rails server**.

### 2. Add Devise your app <a id="2-set-up-devise-in-your-app"></a>

Run the following command in the terminal.

```text
rails g devise:install
```

### 3. Configure Devise <a id="3-configure-devise"></a>

Ensure you have defined default url options in your environments files. Open up `config/environments/development.rb` and add this line:

```ruby
   config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
```

before the `end` keyword.

Open up `app/views/layouts/application.html.erb` and add:

```markup
<% if notice %>
  <p class="alert alert-success"><%= notice %></p>
<% end %>
<% if alert %>
  <p class="alert alert-danger"><%= alert %></p>
<% end %>
```

right above

```ruby
   <%= yield %>
```

Open up `app/views/ideas/show.html.erb` and remove the line that says:

```markup
<p id="notice"><%= notice %></p>
```

Do the same for `app/views/comments/show.html.erb` and `app/views/ideas/show.html.erb`. These lines are not necessary as we’ve put the notice in the `app/views/layouts/application.html.erb` file.

### 4. Setup the User model <a id="4-setup-the-user-model"></a>

We’ll use a bundled generator script to create the User model.

```text
   rails g devise user
   rails db:migrate
```

Don't forget to restart your `rails server`

**Coach:** Explain what user model has been generated. What are the fields?

### 5. Create your first user <a id="5-create-your-first-user"></a>

Now that you have set everything up you can create your first user. Devise creates all the code and routes required to create accounts, log in, log out, etc.

Make sure your rails server is running, open [http://localhost:3000/users/sign\_up](http://localhost:3000/users/sign_up) and create your user account.

### 6. Add sign-up and login links <a id="6-add-sign-up-and-login-links"></a>

All we need to do now is to add appropriate links or notice about the user being logged in in the top right corner of the navigation bar.

In order to do that, edit `app/views/layouts/application.html.erb` add:

```markup
<p class="navbar-text pull-right">
<% if user_signed_in? %>
  Logged in as <strong><%= current_user.email %></strong>.
  <%= link_to 'Edit profile', edit_user_registration_path, :class => 'navbar-link' %> |
  <%= link_to "Logout", destroy_user_session_path, method: :delete, :class => 'navbar-link'  %>
<% else %>
  <%= link_to "Sign up", new_user_registration_path, :class => 'navbar-link'  %> |
  <%= link_to "Login", new_user_session_path, :class => 'navbar-link'  %>
<% end %>
</p>
```

right after

```markup
<ul class="nav navbar-nav">
  <li><a href="/ideas">Ideas</a></li>  
  <li ><%= link_to 'New Idea', new_idea_path %></li>
  <li><a href="/pages/info">Info</a></li>
</ul>
```

Finally, force the user to redirect to the login page if the user was not logged in. Open up `app/controllers/application_controller.rb`and add:

```text
  before_action :authenticate_user!
```

after `class ApplicationController < ActionController::Base`.

Open your browser and try logging in and out from your app.

**Coach:** Talk about the `user_signed_in?` and `current_user` helpers. Why are they useful?

![](.gitbook/assets/11-devise-login%20%281%29.PNG)

### What next? <a id="what-next"></a>

* Add extra fields to the User model
* Add relationships between users and ideas
* Restrict users to only be able to edit their own ideas and delete their own comments
* Expand to use roles or permissions \(use one of the popular authorization gem like CanCan\)

