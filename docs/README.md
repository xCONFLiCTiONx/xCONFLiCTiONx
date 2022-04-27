# Business Website
<a href="https://github.com/Huxpro/huxpro.github.io">Hux Blog Jekyll Theme</a>

[![Foo](https://github.com/xCONFLiCTiONx/xCONFLiCTiONx.github.io/raw/master/img/Screenshot.jpg)](https://xconflictionx.github.io/)


<a href="https://xconflictionx.github.io/">https://xconflictionx.github.io/</a>

### Getting Started

1. You will need [Ruby](https://www.ruby-lang.org/en/) and [Bundler](https://bundler.io/) to use [Jekyll](https://jekyllrb.com/). Following [Using Jekyll with Bundler](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/) to fullfill the enviromental requirement.

2. Installed dependencies in the `Gemfile`:

```sh
$ bundle install 
```

3. Serve the website (`localhost:4000` by default):

```sh
$ bundle exec jekyll serve
```

### Jekyll Sitemap Generator Plugin

*Jekyll plugin to silently generate a sitemaps.org compliant sitemap for your Jekyll site*

[![Build Status](https://travis-ci.org/jekyll/jekyll-sitemap.svg?branch=master)](https://travis-ci.org/jekyll/jekyll-sitemap)

## Usage

1. Add `gem 'jekyll-sitemap'` to your site's Gemfile and run `bundle`
2. Add the following to your site's `_config.yml`:

```yml
url: "https://example.com" # the base hostname & protocol for your site
plugins:
  - jekyll-sitemap
```
