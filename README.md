# Nani

---

Nani is pre-alpha level software.  It doesn't work yet.

---

Nani is a modern replacement for the venerable [annotate](https://github.com/ctran/annotate_models)
gem.  Nani is highly customizable and decoupled from ActiveRecord: if you can connect to a database
and retrieve the schema, Nani can annotate your models for you.

## Installation

Install Nani globally with rubygems:

```
$ gem install -g nani
```

## Usage

### Annotating



### Configuration

You configure Nani through the file `.nani.rb` in your project.  With this file, you tell Nani how
to connect to your database, which table maps to which file, what form of comments to use, etc.

For example, this configuration works for most Rails applications:

```ruby
require 'nani/rails'

Nani.configure do |config|
  config.database = Nani::ConnectionAdapter::ActiveRecordAdapter.database
end

annotate(%r{app/models/([^/]+).rb}) { |match| match[1].pluralize }
annotate(%r{spec/models/([^/]+)_spec.rb}) { |match| match[1].pluralize }
annotate(%r{app/controllers/([^/]+).rb}) { |match| match[1].pluralize }
annotate(%r{app/models/([^/]+).rb}) { |match| match[1].pluralize }
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/nani.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
