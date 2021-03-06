# Capistrano::Graphite
[![Gem Version](http://img.shields.io/gem/v/capistrano-graphite.svg)][gem]
[![Build Status](http://img.shields.io/travis/scottsuch/capistrano-graphite.svg)][travis]
[![Dependency Status](http://img.shields.io/gemnasium/scottsuch/capistrano-graphite.svg)][gemnasium]
[![Code Climate](http://img.shields.io/codeclimate/github/scottsuch/capistrano-graphite.svg)][codeclimate]
[![Coverage Status](https://img.shields.io/coveralls/scottsuch/capistrano-graphite.svg)][coveralls]


[gem]: https://rubygems.org/gems/capistrano-graphite
[travis]: http://travis-ci.org/scottsuch/capistrano-graphite
[gemnasium]: https://gemnasium.com/scottsuch/capistrano-graphite
[codeclimate]: https://codeclimate.com/github/scottsuch/capistrano-graphite
[coveralls]: https://coveralls.io/r/scottsuch/capistrano-graphite
This gem works with Capistrano v3.1.0 and above and was based off the work on [this gem](https://github.com/hellvinz/graphite-notify) which works with Capistrano v2.x.

Adding this gem to [Capistrano](https://github.com/capistrano/capistrano) extends functionality by pushing events to graphite upon deployment and rollback.
Currently events are only pushed after `deploy:updated` and `deploy:reverted`.

Some information on events can be found in [this article](http://obfuscurity.com/2014/01/Graphite-Tip-A-Better-Way-to-Store-Events).

## Installation
Install it manually:

    $ gem install capistrano-graphite

Otherwise, add this line to your application's Gemfile:

    gem 'capistrano-graphite'

And then execute:

    $ bundle

## Usage
### Setup your application
Add the following line to your `Capfile`.

    require "capistrano/graphite"

### Configurable options
Path to your graphite instance. Port and user:password are optional.

    set :graphite_url, "http://user:password@example.com:8000/events/"

Disable sending events for a particular stage by setting the following to 0.
Note that the config `graphite_enable_events` has been deprecated in favor of
the config `suppress_graphite_events` below

    set :suppress_graphite_events, "true"      # This is set to false by default


### Test that it's working
You can run the following on it's own assuming you have configured the graphite url

    $ bundle exec cap <stage> deploy:graphite_deploy

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
