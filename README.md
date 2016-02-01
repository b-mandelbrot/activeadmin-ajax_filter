# Activeadmin::AjaxFilter

This gem extends ActiveAdmin so that your can use filters with AJAX-powered input.

## Prerequisites

This extension assumes that you're using [Active Admin](https://github.com/activeadmin/activeadmin) with [Ransack](https://github.com/activerecord-hackery/ransack)

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'activeadmin-ajax_filter'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install activeadmin-ajax_filter

## Usage

Include this line in your JavaScript code (active_admin.js.coffee)

    #= require activeadmin-ajax_filter

Include this line in your CSS code (active_admin.scss)

    @import "activeadmin-ajax_filter";

Include `ActiveAdmin::AjaxFilter` module to the ActiveAdmin relation resource for which you want to support filtering and add `ajax_select` filter to main resource. For example:

    # Relation-resource
    ActiveAdmin.register User do
        include ActiveAdmin::AjaxFilter
    ...

    # Main resource
    ActiveAdmin.register Invoice do
        filter :user, as: :ajax_select, data: { search_fields: [:email, :customer_uid], limit: 7 }

You can use next parameters in `data` hash:

* limit - count of the items which will be requested by AJAX, by default `5`
* value_field - value field for html select element, by default `id`
* search_fields - fields by which AJAX search will be performed, required parameter 
* ransack - ransack query which will be applied, by default it's builded from `search_fields` with `or` and `contains` clauses, e.g.: `email_or_customer_uid_cont`

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake false` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/[USERNAME]/activeadmin-ajax_filter. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](contributor-covenant.org) code of conduct.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
