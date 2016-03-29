### Managing your Ruby gems

Besides having great tools like Bundler and RVM and a great supportive community the topic of managing gems in general
and dependencies in particular can be quite frustrating.

This here shall help with the process.

-

#### Contents
- 1. [Online Resources](#1-online-resources)
- 2. [Example - Upgrading Rails App](#2-upgrading-rails-app)

-

#### 1. Online Resources

official documentation:
- [rubygems](http://guides.rubygems.org/)
- [bundler](http://bundler.io/)
- [rvm](http://rvm.io/)

blogs with tips and workflows:
- [something about bundle update](http://ryanbigg.com/2011/01/why-you-should-run-bundle-update/)
- [updating Rails](http://railsapps.github.io/updating-rails.html)
- [upgrading Rails](http://www.justinweiss.com/articles/how-to-upgrade-to-rails-4-dot-2/)
- [updating a gem](http://makandracards.com/makandra/13885-how-to-update-a-single-gem-conservatively)

Rails-specific:
- [list of all Rails versions](https://rubygems.org/gems/rails/versions)
- [tool for Rails differences](http://railsdiff.org/)

-

#### 2. Upgrading Rails App
As a matter of fact I need to upgrade my app gemoria/scrunch right now. Although it is a huge construction site with lots of work to do it seems to run locally just fine.

Anyway, putting it under continuous integration with Travis CI still does not work. (Basically this was an issue with Jasminerice no longer maintained - the correct gem version was 0.1.0, but from rubygems I only got 0.0.10 which conflicted with Bundler and so with Travis -). I removed Jasminerice as it seems not necessary in current testing stack.

Besides it is time to upgrade.

-

So, my app runs locally on Rails 4.1.8. My goal is to upgrade it to use the latest version of Rails 4.2
and the latest version of each other gem.

So where do I start. I will use the approach to start with an empty gemset, add upgrade Rails at first
and follow up with each gem separately. My app will be working if
- bundler does not complain and can install everything
- the app is starting without errors using `rails s`
- there are no errors running `rake`
- the tests are running green
- the app seems to work as usual using it in the browser

So I procede one step at a time, check each item of the list above afterwards and
let me guide by the errors I get.

With my current RVM-setup I have a global gemset containing these gems.

```
bigdecimal (1.2.4)
bundler (1.7.6)
bundler-unload (1.0.2)
executable-hooks (1.3.2)
gem-wrappers (1.2.7)
io-console (0.4.2)
json (1.8.1)
minitest (4.7.5)
psych (2.0.5)
rake (10.1.0)
rdoc (4.1.0)
rubygems-bundler (1.4.4)
rvm (1.11.3.9)
test-unit (2.1.5.0)
```

- As a user of RVM at first I set up a new gemset and switch to it.
- I create backup-files of my Gemfile and my Gemfile.lock.
- I comment out ever gem in my Gemfile.

-

- 1. Preserve a gemset with a set of gems that are known to be working with my application; this will be the most recent one called ruby-2.1.5@gemoria; (If this was not the last step of an upgrade than now remove most recent gemoria-gemset and rename gemset of last upgrade to gemoria.)
  - `rvm gemset delete gemoria`
  - `rvm gemset rename last_working_gemset gemoria`
- 2. Create a new gemset for the desired upgrade version (Make sure to switch to it with rvm and that it contains the correct global gems.)
- 3. If you work with more than master branch, make sure you switch to your upgrade branch.
- 4. Now change the Rails version in your Gemfile to the desired target version. After that run `bundle update`.
- 5. Run `rake -vT` for first upgrade-test.
- 6. Use `rake rails:update` or [railsdiff](http://railsdiff.org/) to upgrade Rails configuration files step by step. Be careful to not overwite your changes. For example make a commit `git commit -m 'saves state before running rake rails:update'`. I use the commit updating my Gemfile and Gemfile.lock after running bundle update for this.
- 7. Test your app. In my case this is  `bin/rake`, `bin/rspec spec`, `bin/guard`, starting in development and production and do some manual checking.
- 8. Fix everything you want to upgrade: Deprecations, gem updates (usually to latest working version which means downgrading sometimes) and any bugs. Commit the changes and finalize in desired branch for example master.
- 9. If you use tags you can add one with a version name and info. Push everything to your remote. Delete the upgrade branch or leave it be for next time (Don't forget to merge everything new into this branch before next upgrade).

resources:

- [railsapps](http://railsapps.github.io/updating-rails.html)
- [official guides](http://guides.rubyonrails.org/upgrading_ruby_on_rails.html)
- [official guides concerning configuration](http://guides.rubyonrails.org/configuring.html#configuring-assets)
- [rails releases](http://weblog.rubyonrails.org/releases/)
- [railsdiff](http://railsdiff.org/)
- [rails versions](https://rubygems.org/gems/rails/versions)
- [useful blog](http://www.justinweiss.com/articles/how-to-upgrade-to-rails-4-dot-2/)
- [useful blog](http://ryanbigg.com/2011/01/why-you-should-run-bundle-update/)
- [useful blog](http://makandracards.com/makandra/13885-how-to-update-a-single-gem-conservatively)
