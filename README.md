## All

Using <http://ruby.taobao.org/> source

## On Windows 8

2.1 Using railsinstaller-2.1.0 

2.2 Using node-v0.8.14-x86

2.3 Use `ruby script/rails s` to start server

## On Ubuntu 12.10

3.1 Using rvm

3.2 Using nodejs

## Deploy Development

4.1 `bundle install`

4.2 `rake db:migrate`

4.3 `rake db:seed`

4.4 Add a Admin User

	rails console
	User.create(name: 'dave', password: 'secret', password_confirmation: 'secret')

## Deploy Production

5.1 `bundle install`

5.2 `rake db:setup RAILS_ENV="production"`

5.3 Add a Admin User

	rails console production
	User.create(name: 'dave', password: 'secret', password_confirmation: 'secret')

5.4 `bundle exec rake assets:precompile`

5.5 If you are precompiling your assets locally, you can use bundle install --without assets on the server to avoid installing the assets gems (the gems in the assets group in the Gemfile).

## Deploy on Apache

6.1 Using passenger

	passenger-install-apache2-module
 
6.2 /etc/apache2/apache2.conf

	<VirtualHost *:80>
	  ServerName depot.elff1.com
	  # !!! Be sure to point DocumentRoot to 'public'!
	  DocumentRoot /home/elf/program/ruby/depot/public/
	  <Directory /home/elf/program/ruby/depot/public>
	    # This relaxes Apache security settings.
	    AllowOverride all
	    # MultiViews must be turned off.
	    Options -MultiViews
	    Order allow,deny
	    Allow from all
	    # RailsEnv development
	  </Directory>
	</VirtualHost>

6.3 /etc/hosts

	127.0.0.1  depot.elff1.com

6.4 Restart application

	touch tmp/restart.txt