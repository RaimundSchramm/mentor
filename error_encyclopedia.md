####Error Encyclopedia

Please fill me with all errors you encounter including their solution.

This is to help you quickly if you make the same error again.

---

##### Contents
- 1. [Rails-App not reachable](#1-rails-app-not-reachable)
- 2. [RVM Path Error](#2-rvm-path-error)

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

HINTS:

recent rvm message , maybe related

Warning! PATH is not properly set up, '/home/mund/.rvm/gems/ruby-2.1.5/bin' is not at first place,
         usually this is caused by shell initialization files - check them for 'PATH=...' entries,
         it might also help to re-add RVM to your dotfiles: 'rvm get stable --auto-dotfiles',
         to fix temporarily in this shell session run: 'rvm use ruby-2.1.5'.
