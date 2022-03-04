# frozen_string_literal: true

source "https://rubygems.org"

git_source(:github) {|repo_name| "https://github.com/#{repo_name}" }

gem "jekyll", "= 3.9.0"
gem "sprockets", "~> 3.7"
gem "kramdown-parser-gfm", "= 1.1.0"

# If you have any plugins, put them here!
group :jekyll_plugins do
  gem 'jekyll-assets', '~> 3.0', '>= 3.0.12'
  gem 'autoprefixer-rails', '~> 9.8'
  gem 'mini_magick', '~> 4.9', '>= 4.9.2'
  gem 'yui-compressor', '~> 0.12.0'
  gem 'uglifier', '~> 4.1', '>= 4.1.20'

  gem 'bootstrap-sass', '~> 3.4', '>= 3.4.1'
  gem 'font-awesome-sass', '~> 5.6', '>= 5.6.1'
  gem 'google_drive', '~> 3.0', '>= 3.0.1'
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
