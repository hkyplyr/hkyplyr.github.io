---
layout: post
title:  "Setting up this blog"
date:   2020-04-15 20:35:00 -0600
categories: intro stack portfolio
---
Welcome to the first post of my blog. Honestly not sure what I'm planning on writing here, but for starters I figured I'd walk through the steps involved in setting this page up. 

### 1. Finding the theme
I searched all over for some good, free jekyll themes to use for this page. I wanted something with a home page, but also the ability to host a blog on it as well. I clicked through many of the demoes and then finally came across [jekyll-theme-prologue](http://jekyllthemes.org/themes/jekyll-theme-prologue/) created by [Chris Bobbe](https://github.com/chrisbobbe).

### 2. Setting up Ruby, Jekyll, and Bundler
Given I'm developing on a Mac, `Ruby` already comes installed on the latest versions of MacOS. The problem is its outdated and I'm not even sure how to update it. So I ended up following the instructions on the official [Jekyll docs](https://jekyllrb.com/docs/installation/).

**Install Ruby**
``` bash
# Install ruby
$ brew install ruby

# Put the newly installed ruby on your PATH
$ echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.bash_profile

# Ensure the version you installed is latest
$ ruby -v
ruby 2.7.1p83 (2020-03-31 revision a0c7c23c9c)
```

**Install Jekyll & Bundler**
``` bash
# Install bundler and jekyll for the local user
$ gem install --user-install bundler jekyll

# Add the new ruby gem directory to your PATH
$ echo 'export PATH="$HOME/.gem/ruby/2.7.0/bin:$PATH"' >> ~/.bash_profile
```

### 3. Create and serve your site using Jekyll
This information can be found directly on the Jekyll docs main page [here](https://jekyllrb.com/docs/) and this inforamation can be ignored if you already have a jekyll site up and running.

``` bash
# Create a new site in the directory ./myblog
$ jekyll new myblog

# Enter the new directory
$ cd myblog

#Build the site to be accessed locally.
$ bundle exec jekyll serve
```
Your local site can now be accessed at http://localhost:4000


### 4. Install the theme
This step involves modifying the Gemfile in the main directory of your jekyll site. If you followed the previous step, that Gemfile can be found in the `myblog/` directory.

**Update the Gemfile theme**  
In your Gemfile you'll see two lines that look something like this:
``` bash
# This is the default theme for new Jekyll sites. You may change this to anything you like.
gem "minima", "~> 2.5.0"
```
You'll want to update the name and version of the them like so:
``` bash
gem "jekyll-theme-prologue", "~> 0.3.3"
```
**Install the theme**  
Next you want ruby/jekyll to actually download the gem needed for your theme.
``` bash
$ bundle install
```

**Update the _config.yml file**  
The theme comes with a working `_config.yml` file located in the gems. This will likely be found at `/usr/local/lib/ruby/gems/2.7.0/gems/jekyll-theme-prologue-0.3.3`. So you'll want to navigate to that path and copy the `_config.yml` file to your `myblog/` directory and overwrite the existing file.

### 5. Re-serve your site
Once you serve your site for a second time, you should now see a new theme. 
``` bash
$ bundle exec jekyll serve
```

You may need to read the [documentation](https://github.com/chrisbobbe/jekyll-theme-prologue) to get it fully functional and maybe I'll add another post for that in the future.

For now though, enjoy!