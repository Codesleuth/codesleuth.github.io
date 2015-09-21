source 'https://rubygems.org'

require 'json'
require 'open-uri'
versions = JSON.parse(open('https://pages.github.com/versions.json').read)

gem 'github-pages', versions['github-pages']
gem 'jekyll-redirect-from', '~> 0.8.0'
gem 'kramdown', versions['kramdown']
gem 'wdm', '~> 0.1.0' if Gem.win_platform?
gem 'jekyll-sitemap', versions['jekyll-sitemap']