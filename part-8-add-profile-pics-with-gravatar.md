---
description: 'Created by Catherine Jones, Updated by Nicole Maneth'
---

# Part 8: Add Profile Pics with Gravatar

This guide assumes that you have already built a Rails Girls app by following this [app development guide](http://guides.railsgirls.com/app/) and added authentication using [Devise](http://guides.railsgirls.com/devise/).

#### Important {#important}

You need to have an e-mail address registered with Gravatar for this to work. If you do not already have one you can go to [gravatar.com](http://en.gravatar.com/).

### _1._Add the Gravtastic gem {#1-add-the-gravtastic-gem}

Open up your gemfile and under your `devise` gem add

```text
gem 'gravtastic'
```

In the terminal run

```text
bundle install
```

This will install the gravtastic gem. Then remember to restart your rails server.

### _2._Set up Gravatar in your app {#2-set-up-gravatar-in-your-app}

Open `app/models/user.rb`, and add these lines

```text
include Gravtastic
gravtastic
```

right after the first line.

### _3._Configure Gravatar {#3-configure-gravatar}

Open `app/views/layouts/application.html.erb` and in the

```text
<% if user_signed_in? %>
```

section but before the

```text
<% else %>
```

add

```text
<%= image_tag current_user.gravatar_url %>
```

Now open you app in your browser and login with an e-mail address that is associated with a Gravatar. You should be able to see your Gravatar.  


