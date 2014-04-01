# Create your own Ruby server with Debian 7.0

Simple guide, how to create your own Ruby server with Debian 7, RVM, Nginx, Passenger 4 and ISPConfig 3.

Have you just finished our first Ruby application and needs you to deploy it? Or you want to switch from Heroku to your own server? It's not too hard to run your custom server on Debian with ISPConfig control panel, to easy create new websites, databases, Nginx and Passenger as webserver, RVM to manage your Ruby versions and gemsets.

This tutorial doesn't contains how to install, configure or run nameserver and mysql server, it include only necessary steps to run only your Ruby application.

## Debian
First of all, you need server running Debian 7, they are plenty of tutorials, how to install debian on your server, or you can rent virtual server with Debian already installed.

Install required dependencies.

	apt-get install mysql-client mysql-server sudo php-pear php5-mysql curl fail2ban

MySQL client, server, PHP and PHP mysql is required by ISPConfig and curl is need to install RVM

You need unbind mysql to localhost, co comment this line

	editor /etc/mysql/my.cnf
	# bind-address           = 127.0.0.1

And restart MySQL Server

	service mysql restart

If you want run ISPConfig admin interface on this server, you need to install PHP processor otherwise skip this step.

	apt-get install php5-fpm

 
## Nginx and Passenger

You can find more informations on [Phusion blog](http://blog.phusion.nl/2013/09/11/debian-and-ubuntu-packages-for-phusion-passenger/)

	Add key to your server
	gpg --keyserver keyserver.ubuntu.com --recv-keys 561F9B9CAC40B2F7
	gpg --armor --export 561F9B9CAC40B2F7 | sudo apt-key add -

Install dependencies

	sudo apt-get install apt-transport-https

Add Passenger source to source list, we're running on Debian 7 Wheezy, if you have another distribution, you need source to you distribution

	editor /etc/apt/sources.list.d/passenger.list

Add following line and save it

	deb https://oss-binaries.phusionpassenger.com/apt/passenger wheezy main

Set user and refresh source

	sudo chown root: /etc/apt/sources.list.d/passenger.list
	sudo chmod 600 /etc/apt/sources.list.d/passenger.list
	sudo apt-get update

Now you can install Nginx with already implemented Passenger

	sudo apt-get install nginx-full passenger

## ISPConfig

Install ISPConfig, it helps you create new website very easy and accessible from admin interface.

Download latest ISPConfig to your temp

	cd /tmp && wget http://www.ispconfig.org/downloads/ISPConfig-3-stable.tar.gz

Unpack it

	tar xfz ISPConfig-3-stable.tar.gz

And install

	cd ispconfig3_install/install/ && php -q install.php

**Follow given instructions**
If you already have ISPConfig admin interface on another machine, you need to install it too, and connect it to main server

## Configure Nginx
You need uncomment 2 lines in Nginx config

	editor /etc/nginx/nginx.conf

	passenger_root /usr/lib/ruby/vendor_ruby/phusion_passenger/locations.ini;
	passenger_ruby /usr/bin/ruby;

## Configure virtual host created by ISPConfig

	cp /usr/local/ispconfig/server/conf/nginx_vhost.conf.master /usr/local/ispconfig/server/conf-custom/nginx_vhost.conf.master

	editor /usr/local/ispconfig/server/conf-custom/nginx_vhost.conf.master

Remove root; index index.html
Enable Passenger (optional, you can enable passenger individual on each website)

	passenger_enabled on;

## Create new user
After restart create new user called "deployer" or whatever you want

	adduser deployer --ingroup www-data

## RVM (non-system wide) and Ruby

RVM can be installed automatically with Capistrano and `rvm/capistrano` gem (but not with 3.0 yet). You can use `rvm1/capistrano3` gem, we use it too. It seems to much better than `capistrano/rvm`

Install RVM

	\curl -L https://get.rvm.io | bash -s stable

Reload RVM

	source /home/deployer/.rvm/scripts/rvm

User needs to be sudo, to install requirements and install requirenments

	adduser deployer sudo
	rvm requirements

Load RVM function

	echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm"
	source ~/.bashrc

And test if is RVM function

	type rvm | head -n 1

Install Ruby

	rvm install 2.0.0
	rvm alias create default 2.0.0
	rvm use 2.0.0

## Pair your mac with server

Generate your ssh key

	ssh-keygen -t rsa -C "your.name@domain.tld"

Add this key to your server

	cat ~/.ssh/id_rsa.pub | ssh deployer@domain.tld 'cat - >> ~/.ssh/authorized_keys'
	chmod 600 ~/.ssh/authorized_keys
	exit

If you're deploying with git and you're using BitBucket/GitLab, you need enable deployment SSH key

	ssh deployer@domain.tld
	su deployer
	ssh-keygen -t rsa -C "your.name@your.server.tld"
	cat ~/.ssh/id_rsa.pub

And paste this key to BitBucket/GitLab deployment keys

## Application requirements

Are you deploying with git?

	sudo apt-get install git

Are you using MySQL?

	sudo apt-get install libmysql-ruby libmysqlclient-dev

Are you using Redis, FFMpeg or ImageMagick?

	sudo apt-get install redis-server imagemagick ffmpeg

## Use Uglifier to compile CoffeeScript

Install Node.js, Uglifier can use it instead TheRubyRacer to CoffeeScript translator
Node.js is not available in repository, so we need to install it manually.

Install dependencies

	sudo apt-get install python g++ make checkinstall

Download latest Node.js

	mkdir ~/src && cd $_
	wget -N http://nodejs.org/dist/node-latest.tar.gz

Unzip and prepare to install

	tar xzvf node-latest.tar.gz && cd node-v*

Remove the "v" in front of the version number in the dialog in the next step

	./configure
	checkinstall
	sudo dpkg -i node_*

## Restart

I think it's good idea to restart the server, but maybe necessary.

Now you are able to run your Ruby (on Rails) applications on your server using Debian & Nginx & Passenger & ISPConfig & RVM

How to deploy Rails application I will show you in the next post.

> [Jiri Kolarik](http://jirikolarik.com) @ [We're in s.r.o.](http://werein.cz)