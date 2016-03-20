#### Rails Style Guide

##### Contents

- Testing
  - [Acceptance Testing](#acceptance-testing)
  - [Shared Behaviour](#shared-behaviour)

---

##### Logging
- [offical doc](http://guides.rubyonrails.org/debugging_rails_applications.html#log-levels)
- [more comprehensive blogpost](http://www.sitepoint.com/rubyists-love-logging/)
- [another blogpost](http://rubyjunky.com/cleaning-up-rails-4-production-logging.html)
- [maybe it's just ruby?!](http://ruby-doc.org/stdlib-2.1.0/libdoc/logger/rdoc/Logger.html)

##### Testing
###### Routes
Basicially I write a Routing Test for every route my apps provide.

When it comes to testing these routes I usually seperate the tests into sections of
- RESTful
- not RESTful
- not used default REST routes

[As mentioned here](http://stackoverflow.com/questions/4803469/how-can-i-assert-that-no-route-matches-in-a-rails-integration-test) a test for a not to be used route could be written like

```ruby
  describe 'not used default REST routes' do
    it 'does not route to #new' do
      assert_raises(ActionController::RoutingError) do
        get '/lobby/new'
      end
    end
  end
```

if I want to make explicitly sure, that I have a resource in my routes.rb which uses the default notation but only a subset of its routes.

TODO:
It is exactly the error I don't want to see as a User if I request a non-existent route. Add some info about standard error pages and -handling for failing requests.

##### Shared Behaviour

Convenience methods that are usable in tests can be placed into a `test/support` directory.

For example I use logging in a User multiple times in my Integration Tests. So I have this in place:

test/support/features.rb
```ruby
module Utilities
  module Features
    def login(user)
      get '/'
      get '/log_in'
      post '/log_in', session: { name: user.name, password: user.password }
    end
  end
end
```

To make this available inside any test I update my test/test_helper.rb as follows:

test/test_helper.rb
```ruby
# looks up every file inside the support directory
Dir[Rails.root.join('test/support/**/*.rb')].each {|f| require f} <---

class ActiveSupport::TestCase
  # Add more helper methods to be used by all tests here...
  # looks up exactly the desired Module hierarchy
  include Utilities::Features  <---
end
```

[Thanks for help](http://schock.net/articles/2015/01/21/modules-with-rails-tests-share-behavior-minitest/)

--

##### Acceptance Testing

This section provides info about High-Level-Testing. As a Product Owner you want to make sure that an app is providing some functionality/feature. So basically what this means is that a User clicks on links or fills out and submits forms in some bigger app-specific/domain-specific context. So the High-Level means a certain Use Case / Scenario in which the User interacts with the app to reach a certain goal. Under the hood of the Web Stack the tests touch everything from the View- to the Database-Layer. And this is what I want to test by Acceptance Testing/Integration Testing.

There is a certain redundancy with other tests because these Integration Tests assert things that will be tested somewhere else, too. But the important benefit is, that only on this level everything needed for a Use Case is tested. So the sum is bigger than its parts.

Currently I try several stacks...to be continued

[Capybara's method for dealing with alert-boxes](http://www.rubydoc.info/github/jnicklas/capybara/Capybara/Session:accept_alert)
