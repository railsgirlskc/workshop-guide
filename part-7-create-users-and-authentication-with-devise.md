---
description: >-
  Created by Piotr Steininger, @polishprince Updated by Ernesto Jimenez,
  @ernesto_jimenez and Nicole Maneth
---

# Part 7: Create Users and Authentication with Devise

### _1._Add devise gem {#1-add-devise-gem}

Open up your `Gemfile` and add this line

```text
gem 'devise'
```

and run

```text
bundle install
```

to install the gem. **Also remember to restart the Rails server**.

### _2._Set up devise in your app {#2-set-up-devise-in-your-app}

Run the following command in the terminal.

```text
rails g devise:install
```

### _3._Configure Devise {#3-configure-devise}

Ensure you have defined default url options in your environments files. Open up `config/environments/development.rb` and add this line:

```text
   config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
```

before the `end` keyword.

Open up `app/views/layouts/application.html.erb` and add:

```text
<% if notice %>
  <p class="alert alert-success"><%= notice %></p>
<% end %>
<% if alert %>
  <p class="alert alert-danger"><%= alert %></p>
<% end %>
```

right above

```text
   <%= yield %>
```

Open up `app/views/ideas/show.html.erb` and remove the line that says:

```text
<p id="notice"><%= notice %></p>
```

Do the same for `app/views/comments/show.html.erb`. These lines are not necessary as we’ve put the notice in the `app/views/layouts/application.html.erb` file.

### _4._Setup the User model {#4-setup-the-user-model}

We’ll use a bundled generator script to create the User model.

```text
   rails g devise user
   rails db:migrate
```

**Coach:** Explain what user model has been generated. What are the fields?

### _5._Create your first user {#5-create-your-first-user}

Now that you have set everything up you can create your first user. Devise creates all the code and routes required to create accounts, log in, log out, etc.

Make sure your rails server is running, open [http://localhost:3000/users/sign\_up](http://localhost:3000/users/sign_up) and create your user account.

### _6._Add sign-up and login links {#6-add-sign-up-and-login-links}

All we need to do now is to add appropriate links or notice about the user being logged in in the top right corner of the navigation bar.

In order to do that, edit `app/views/layouts/application.html.erb` add:

```text
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

```text
<ul class="nav">
  <li class="active"><a href="/ideas">Ideas</a></li>
</ul>
```

Finally, force the user to redirect to the login page if the user was not logged in. Open up `app/controllers/application_controller.rb`and add:

```text
  before_action :authenticate_user!
```

after `protect_from_forgery with: :exception`.

Open your browser and try logging in and out from.

**Coach:** Talk about the `user_signed_in?` and `current_user` helpers. Why are they useful?

### What next? {#what-next}

* Add extra fields to the User model
* Add relationships between users and ideas
* Restrict users to only be able to edit their own ideas and delete their own comments
* Expand to use roles or permissions \(use one of the popular authorization gem like CanCan\)

