# hammer-jruby
This is the repo used for building JRuby binaries for the [heroku ruby buildpack](https://github.com/heroku/heroku-buildpack-ruby).

## Building a Ruby
This tool uses [hammer](https://github.com/hone/hammer) for building binaries on heroku. You'll need to install the hammer gem first.

```sh
$ gem install hammer --pre
```

Now clone this repo:

```sh
git clone git://github.com/hone/hammer-jruby.git
```

You'll need to be in the hammer-jruby directory in order to build. After, you can build the binary. For instance JRuby 1.7.8 in Ruby 1.9.3 mode.

```sh
$ cd hammer-jruby
$ hammer build --env VERSION:1.7.8 RUBY_VERSION:1.9.3
```

This puts a `*.tgz` binary in the `builds/` folder.

NOTE: This only works for JRuby 1.7.5 in higher since they switched from ant to maven for building.

### Enviroment Variables
hammer supports passing build options as environment variables as we saw above for specifying the JRuby version with `VERSION`.

NOTE: hammer uses a `:` instead of a `=` for setting the options.

* `VERSION` - This specifies the JRuby version used. This is in the format: `"#{MAJOR}.#{MINOR}.#{TEENY}"`. This option is required.
* `RUBY_VERSION` - JRuby supports multiple Ruby versions in the 1.7.x series. This sets the default Ruby version to use. It's specificed in the format: `"#{MAJOR}.#{MINOR}.#{TEENY}"`.
