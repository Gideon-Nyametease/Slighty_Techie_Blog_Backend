# README

This README documents the steps necessary to get the
application up and running.

Things you need to know:

* Ruby version - ruby 3.2.2

* Gemfile 
    gem 'devise'
    gem 'devise-jwt'
    gem 'rack-cors'

* Database creation - postgresql (rails db:create)

* Configuration -
    rails generate devise:install
    rails generate devise user
    rails db:mimgrate

* Add this to devise.rb
    config.jwt do |jwt|
        jwt.secret = ENV['DEVISE_JWT_SECRET_KEY']
        jwt.dispatch_requests = [
            ['POST',%r{^/signin$}],
        ]
        jwt.revocation_requests = [
            ['DELETE',%r{^/signout$}],
        ]
        jwt.expiration_time = 14.days.to_i
        # use default aud header
        jwt.aud_header = 'JWT_AUD'
    end

* How to run the test suite - 
    gem 'rspec-rails'
    gen 'rexml'
    gem 'spring-command-rspec'
    gem 'parallel-tests'

* Services (job queues, cache servers, search engines, etc.) - 

* Deployment instructions
