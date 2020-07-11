# Production

## Assets Pipeline

Main feature - concatenate assets.

Fingerprinting - a technique that makes the name of a file dependent on its contents:

```ruby
config.assets.digest
```

Compiled assets are written to the location specified in config.assets.prefix \(default is the public/assets\).

```text
bundle exec rake assets:precompile RAILS_ENV=production
```

Assets compiled locally

```text
bundle install --without assets
```

to avoid installing the assets bundles.

Apache config to get the benefits of assets fingerprinting:

```text
<LocationMatch "^/assets/.*$">
  Header unset ETag
  FileETag None
  # RFC says only cache for 1 year
  ExpiresActive On
  ExpiresDefault "access plus 1 year"
</LocationMatch>
```

### Live Compilation

```ruby
config.assets.compile = true
```

and therubyracer in production environ:

```ruby
group :production do
  gem 'therubyracer'
end
```

### Pipeline compression

**CSS**

Using the yui-compressor gem:

```ruby
config.assets.css_compressor = :yui
```

**Javascript**

Possible options for JavaScript compression are :closure, :uglifier and :yui. These require the use of the closure-compiler, uglifier or yui-compressor gems, respectively.

```ruby
config.assets.js_compressor = :uglifier
```

### Command line utilities

Compiles any assets to public/assets:

```text
rake assets:precompile
```

Removes old assets from public/assets:

```text
rake assets:clean
```

Nuke public/assets and clear the Sprockets file system cache:

```text
rake assets:clobber
```

### Complementary plugins

The following plugins provide some extras for the Sprockets Asset Pipeline.

```text
coffee-rails
sass-rails
```

