# world.db.starter - Build Your Own HTTP JSON API

The worlddb web service starter sample lets you build your own HTTP JSON API
using the
[`world.db`](https://github.com/openmundi).  Example:

```ruby
class StarterApp < Webservice::Base

  #####################
  # Models

  include WorldDb::Models   # e.g. Continent, Country, State, City, etc.


  ##############################################
  # Controllers / Routing / Request Handlers

  get '/countries(.:format)?' do
    Country.by_key.all    # sort/order by key
  end

  get '/cities(.:format)?' do
    City.by_key.all       # sort/order by key
  end

  get '/tag/:slug(.:format)?' do   # e.g. /tag/north_america.csv
    Tag.find_by!( slug: params['slug'] ).countries
  end

  ...
end # class StarterApp
```

(Source: [`app.rb`](app.rb))



## Getting Started

Step 1: Install all libraries (Ruby gems) using bundler. Type:

    $ bundle install

Step 2: Copy an SQLite database e.g. `world.db` into your folder.

Step 3: Startup the web service (HTTP JSON API). Type:

    $ ruby ./server.rb

That's it. Open your web browser and try some services
running on your machine on port 9292 (e.g. `localhost:9292`).



## License

The `world.db.starter` scripts are dedicated to the public domain.
Use it as you please with no restrictions whatsoever.

## Questions? Comments?

Send them along to the
[Open World Database (world.db) and Friends Forum/Mailing List](http://groups.google.com/group/openmundi).
Thanks!
