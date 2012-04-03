[![Build Status](https://secure.travis-ci.org/denniskuczynski/beanstalkd_view.png?branch=master)](http://travis-ci.org/denniskuczynski/beanstalkd_view)

Beanstalkd View
===============
A Sinatra app to view/manage beanstalkd queues that can be embedded in a Rails app similar to what's available in Resque.

Configuration
-------------

To use in a Rails app, include the gem in your Gemfile:

``` ruby
gem 'beanstalk-client', :git => 'https://github.com/kr/beanstalk-client-ruby.git' #Use the latest, if you need the pause-tube command
gem beanstalkd_view
```

Otherwise, gem install beanstalkd_view


Use the following environment variable to specify the location of the beanstalk server:

``` ruby
ENV['BEANSTALK_URL'] = 'beanstalk://localhost/'
```

Embedding in a Rails app
------------------------

Add the following to your routes.rb file:

``` ruby
mount BeanstalkdView::Server, :at => "/beanstalkd"
```

(NOTE: You may mount the server at any path, not just /beanstalkd)

You can then browse to your application path to view information about your beanstalkd tubes, i.e.
http://127.0.0.1:3000/beanstalkd

Running from the command line
------------------------

Run the beanstalkd_view executable, e.g.

beanstalkd_view

or from a Rails app:

bundle exec beanstalkd_view


(This will use the vegas gem to launch the Sinatra app on an available port.)


![Screenshot](http://s9.postimage.org/tpfksm5kv/beanstalkd_view.png)

