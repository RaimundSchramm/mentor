#### Deployment Style Guide

fill me with workflows, tips and best practices about

Capistrano and co., host-setup, release-management, continuous integration

-

##### Contents

- 1. [Semantic Versioning](#1-semantic-versioning)
- 2. [Host Setup](#2-host-setup)

-

##### 1. Semantic Versioning

[Semantic Versioning](http://semver.org/) is a method of adding a consistent and constant release to your software.

Things to improve in my code / release management:

- more documentation for public API
- correct version number, e.g. for git tags
  - x.y.z-alpha (x-major, y-minor, z-patch)
  - z only for bugfixes

further resources:

- [discussion about pros and cons](https://gist.github.com/jashkenas/cbd2b088e20279ae2c8e)
- [good example](http://blog.versioneye.com/2014/01/16/semantic-versioning/)
- [interesting alternative for non-library-projects](https://davehall.com.au/blog/dave/2016/01/19/internal-applications-when-semantic-versioning-doesnt-make-sense)

-

##### 2. Host Setup

For now I keep Thin. Have to read more and do some benchmarking to see differences of alternatives nowadays (Puma, Unicorn, etc.)

resources:

- [engineyard](https://www.engineyard.com/articles/rails-server)
- [some benchmarks](http://www.madebymarket.com/blog/dev/ruby-web-benchmark-report.html)
- [some gist](https://gist.github.com/pbyrne/5218411)

-
