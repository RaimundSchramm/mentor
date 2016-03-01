####Error Encyclopedia

Please fill me with all errors you encounter including their solution.

This is to help you quickly if you make the same error again.


###### Rails-App not reachable

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
