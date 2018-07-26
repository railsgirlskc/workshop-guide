---
description: 'Created by Miha Filej, @mfilej, Edited by Nicole Maneth'
---

# Part 6: Create Thumbnails with CarrierWave

**Coach**: Explain what specifying the image width in HTML at the end of Step 4 does and how it differs from resizing images on the server.

### _1._Installing ImageMagick {#1-installing-imagemagick}

* OS X: run `brew install imagemagick`. If you don’t have the brew command, you can [install Homebrew here](https://brew.sh/).
* Windows: download and run the [ImageMagick installer](http://www.imagemagick.org/script/download.php#windows) \(use the first _download_ link\). In the installation wizard, make sure you check the checkbox to install legacy binaries.
* Linux: On Ubuntu and Debian, run `sudo apt-get install imagemagick`. Use the appropriate package manager instead of `apt-get` for other distributions.

**Coach**: What is ImageMagick and how is it different from libraries/gems we used before?

Open `Gemfile` in the project and add

```text
gem 'mini_magick', '4.8.0'
```

under the line

```text
gem 'carrierwave'
```

In the Terminal run:

```text
bundle
```

### _2._Telling our app to create thumbnails when an image is uploaded {#2-telling-our-app-to-create-thumbnails-when-an-image-is-uploaded}

Open `app/uploaders/picture_uploader.rb` and find the line that looks like this:

```text
  # include CarrierWave::MiniMagick
```

Remove the `#` sign.

**Coach**: Explain the concept of comments in code.

Below the line you just changed, add:

```text
version :thumb do
  process :resize_to_fill => [50, 50]
end
```

The images uploaded from now on should be resized, but the ones we already have weren’t affected. So edit one of the existing ideas and re-add a picture.

### _3._Displaying the thumbnails {#3-displaying-the-thumbnails}

To see if the uploaded picture was resized open `app/views/ideas/index.html.erb`. Change the line

```text
<%= image_tag idea.picture_url, width: '100%' if idea.picture.present? %>
```

to

```text
<%= image_tag idea.picture_url(:thumb) if idea.picture.present? %>
```

Take a look at the list of ideas in the browser to see if the thumbnail is there.

