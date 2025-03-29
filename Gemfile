source 'https://rubygems.org'
ruby '3.4.1'

require 'json'
require 'open-uri'

gem 'jekyll', '4.4.1'

group :jekyll_plugins do
    # jekyll-livereload is incompatible with Jekyll 4.x, removed
    # Keeping this version pinned as specified in the original Gemfile
    gem 'jekyll-pwa-plugin', "= 2.2.3"
end

group :development do
    gem 'foreman'
    # octopress-autoprefixer might also be incompatible with Jekyll 4.x
    # gem 'octopress-autoprefixer'
    # Use standard autoprefixer instead
    gem 'autoprefixer-rails'
end

group :test do
    gem 'rake', '~> 13.0'
    gem 'html-proofer', '~> 5.0'
end
