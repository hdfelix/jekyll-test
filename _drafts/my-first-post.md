---
layout: post
title:  "Test Post"
date:   2014-09-05 16:18:44
categories: general
---
##Things Reseached Today
After a session with some colleagues from BfA in Anaheim were we discussed their progress in their Rails studies and I shared with them some of the principles of Object Oriented Design that I have been reading about in Sandy Metz's book [Practical Object Oriented Design in Ruby](http://poodr.com/), I headed back to the office for a planning meeting. Finishing that, I dived into Jekyll and how to set it up properly including integration with Travis CI, Github pages, and Heroku. There's so much to read and learn that I spent the next several hours going through the process.

Here's what I have so far:
* Installed [Jekyll](http://jekyllrb.com/) - `gem install jekyll`
* Updated my [Ruby](ruby-lang.org) version by installing via [rbenv](https://github.com/sstephenson/rbenv):
  * ```
    rbenv install -l        # see available ruby versions
    rbenv install 2.1.2
    rbenv global 2.1.2      # set ruby 2.1.2 as default globally
    rbenv rehash
    ```
* Installed [bundler](bundler.io) in my new ruby environment: `gem install bundler`
* ran `bundle install`
  
###Setting up Travis:
* Install the Command Line Client: `gem install travis`
* Create .travis.yml file and enable the project: `travis init`
* Update the `.travis.yml` file with the minimal information:
  ``` YAML
  [add... ]
  ```

###Setting up Github pages:
Jekyll also offers powerful support for code snippets:

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help
