####Error Encyclopedia

Please fill me with all errors you encounter including their solution.

This is to help you quickly if you make the same error again.

---

##### Contents
- 1. [Rails-App not reachable](#1-rails-app-not-reachable)
- 2. [RVM Path Error](#2-rvm-path-error)
- 3. [Firefox-Error while running tests](#3-firefox-error-while-running-tests)
- 4. [WAI-error Rails has_secure_password](#4-wai-error-rails-has_secure_password)
- 5. [Error installing gems for ruby 2.2.2](#error-installing-gems-for-ruby-222)

---

###### 1. Rails-App not reachable

Use Case:
- I want to set up my Rails-App on Ubuntu inside Virtual Box inside Windows 7 host.
- I want to reach my app from my Windows 7 host.
- I want to reach my app form inside my LAN.
- I want to reach my app from outside my router.

Problem:
- App is not reachable when set up to run on binding interface 127.0.0.1.

Solution
- Assuming VirtualBox, LAN and Router are configured correctly.
- There was an update in Rails to this setting.
- It has to be 0.0.0.0 to work.
- Starting the Rails-App for example `rails server --binding 0.0.0.0` solves the problem.

---

###### 2. RVM Path Error

Use Case
- open Terminal
- cd to app (rvm is set up, so loading correct ruby and gemset off .ruby-versin and .ruby-gemset)
- everything works
- open another Terminal tab
- RVM-Path issue is still to fix, so cd .

Problem

- starting app for example results in error certain gem is missing (which it isn't)

Solution
- currently assuming gemset is not loaded this way, so explicitly loading it rvm gemset use name_of_gemset seems to work
- afaik it is works as intended because opening the dir in new tab just loads the default gemset while entering somehow loads from .ruby-gemset

HINTS:

recent rvm message , maybe related

Warning! PATH is not properly set up, '/home/mund/.rvm/gems/ruby-2.1.5/bin' is not at first place,
         usually this is caused by shell initialization files - check them for 'PATH=...' entries,
         it might also help to re-add RVM to your dotfiles: 'rvm get stable --auto-dotfiles',
         to fix temporarily in this shell session run: 'rvm use ruby-2.1.5'.

This above is something different. Make sure rvm is always the first entry in PATH variable. I accidentally had exercism in front of it.

[helpful comments](http://stackoverflow.com/questions/18276701/getting-warning-path-is-not-properly-set-up-when-doing-rvm-)use-2-0-0-defaul

-

##### 3. Firefox-Error while running tests

error was something like this: gnome.display --- Firefox-Profile not accessible or missing

seems to be associated with call of save_and_open_page inside feature spec

-

##### 4. WAI-error Rails has_secure_password

...works as intended...
Rails [has_secure_password](http://apidock.com/rails/ActiveModel/SecurePassword/ClassMethods/has_secure_password) provides you with validation on password on creation of the including model.

I encountered a confusing behaviour when after I added validations on password, for example for length, and suddenly my User was not valid anymore.

Rails has_secure_password validation together with additional validations on password triggers on update. So for me the solution is to switch off the validation on update for every update which is not a necessary update_users-action.

```ruby
def logout!
  self.logged_in = false
  save! validate: false
end
```

[explanation of has_secure_password](http://robert-reiz.com/2014/04/12/has_secure_password-with-rails-4-1/)

-

##### quick, dirty and maybe works-as-intended

I thought `assert_routing` did always work for me. Having resource-routes and additional named route for users#new-resource gives me the following error in Routing Test.

```ruby
  resources :users
  get '/signup'  => 'users#new', as: :signup
```

The generated path </users/new> did not match </signup>.
  Expected: "/signup"
    Actual: "/users/new"

The same behaviour results from using `assert_generates`.

Only assert_recognizes works correctly.

-

Hm, I think this rights-issue is because of copying it (backup) from other user (different OS, different user).
So setting rights with `chmod` for example [as explained here](http://stackoverflow.com/questions/23297832/weird-rails-error-permission-denied-bin-rails-for-old-rails-apps).

-

##### Error installing gems for ruby 2.2.2

Usecase:
- trying to bundle new gemset
- after rvm-update to version 1.27.0 (don't know if that's related)
- for ruby-version 2.2.2

Problem:
- some gems won't install ()
- sample output for json 1.8.3

gem install json -v '1.8.3'
Building native extensions.  This could take a while...
ERROR:  Error installing json:
	ERROR: Failed to build gem native extension.

    /home/mund/.rvm/rubies/ruby-2.2.2/bin/ruby -r ./siteconf20160515-13050-6fpwhc.rb extconf.rb
creating Makefile

make "DESTDIR=" clean

make "DESTDIR="
compiling generator.c
linking shared-object json/ext/generator.so
/usr/bin/ld: cannot find -lgmp
collect2: error: ld returned 1 exit status
make: *** [generator.so] Error 1

make failed, exit code 2

Gem files will remain installed in /home.../.rvm/gems/ruby-2.2.2@whatdojuniorsgetpaid/gems/json-1.8.3 for inspection.
Results logged to /home.../.rvm/gems/ruby-2.2.2@whatdojuniorsgetpaid/extensions/x86_64-linux/2.2.0/json-1.8.3/gem_make.out

Solution:
- don't understood but works for json [as recommended here](https://github.com/flori/json/issues/259)

-
