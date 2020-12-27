# spree_blogs

![CI](https://github.com/MatthewKennedy/spree_blogs/workflows/CI/badge.svg)
![Standard Rb](https://github.com/MatthewKennedy/spree_blogs/workflows/Standard%20Rb/badge.svg)

Move your existing Shopify blogs over to Spree bringing all your blog posts and URL's with you.


## Features
- Manage multiple blogs (like Shopify)
- Multi-store support
- Draft editing mode
- Compatable with Rails Action Text and the TRIX rich text editor


## Installation

1. Add the following lines to your Gemfile:

    ```ruby
    gem "spree_blogs", github: "matthewkennedy/spree_blogs", branch: "main"
    ```

2. Install the gems using Bundler

    ```ruby
    bundle install
    ```

3. Copy & run migration.

    ```ruby
    bundle exec rails g spree_blogs:install
    ```

4. Restart your server

  If your server was running, restart it so that it can find the assets properly.


## Configurations

### Action Text - TRIX RTE

To use the Rails built in TRIX Rich Text Editor install and set up Action Text via the Rails guides, and then set the following config to true:

```ruby
# In initilizers/spree.rb
SpreeBlogs::Config.use_action_text = true
```

### Raw HTML Post Content

If you are not using Action Text, and wish to use raw HTML in your Blog Post content, you can set the following config:

```ruby
# In initilizers/spree.rb
SpreeBlogs::Config.use_action_text = false
SpreeBlogs::Config.use_raw_post_content = true
```

### Lazy Loading Image Ratio

Spree Blogs takes advantage of the lazy loading images javascript in Spree 4.1 and higher. If you wish to change the image ratio from the default square (1/1), you can do so by setting the config below:

```ruby
# In initilizers/spree.rb
SpreeBlogs::Config.image_ratio = "16/9" # The default is "1/1" (square).
```


## Usage

1. Set up Author's

Visit **Configurations/Roles** and add a new Role named `blogger`, then assign the new role to any user you wish to appear in the author list.


2. Create A Blog

Click **Blog Posts** from the main menu, and then click **Manage Blogs** in the contextual menu, once you are in the Manage Blogs area click **New Blog** to create your first blog and assign it to one or more of your stores.


3. Create A Post

Navigate to Blog Posts area and click the New **Post butto** to create your first blog post, assign your post to your new Blog and your done.


### Add Blogs To Your Homepage

Display blogs on your homepage by adding the following partial and setting the desired blog title and number of posts you wish to display in the locals:

```ruby
# views/spree/home/index.html.erb
<%= render partial: "spree/shared/drop_in_blog", locals: { blog: "news", post_count: 4 } %>
```
## Testing

First bundle your dependencies, then run `rake`. `rake` will default to building the dummy app if it does not exist, then it will run specs. The dummy app can be regenerated by using `rake test_app`.

```shell
bundle
bundle exec rake
```

When testing your applications integration with this extension you may use it's factories.
Simply add this require statement to your spec_helper:

```ruby
require "spree_blogs/factories"
```


## ToDo

- Add page caching
- Write tests
- Set lazyloading images to be more efficient
- Have a good tidy up
- Write more tests


## Contributing

If you'd like to contribute, please take a look at the
[instructions](CONTRIBUTING.md) for installing dependencies and crafting a good
pull request.

Copyright (c) 2020 Matthew Kennedy, released under the New BSD License
