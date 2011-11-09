# Jenkins

The default Mac OS X installation put Jenkins Launch Agent at /Library/LaunchAgents/org.jenkins-ci.plist with a "daemon" username and group!

This is fine except that the home directory for "daemon" is /var/root, the same as "root" user.

See http://colonelpanic.net/2011/06/jenkins-on-mac-os-x-git-w-ssh-public-key/

http://mattonrails.wordpress.com/2011/06/08/jenkins-homebrew-mac-daemo/

# Ubuntu installation

Use .bash_profile, not .bash_rc, or .bashrc also can.

Install Jenkins first, so that we have the "jenkins" user.

sudo -Hiu jenkins

https://rvm.beginrescueend.com/integration/hudson/


For mysql, see
http://itshouldbeuseful.wordpress.com/2011/05/04/setting-up-ubuntu-11-04-for-rails-development/

sudo apt-get install mysql-server libmysqlclient-dev libmysql-ruby mysql-admin


# Configure Jenkins
#!/bin/bash -e
source "$HOME/.rvm/scripts/rvm"
rvm use "ruby-1.9.2-p180@jenkins"
rake db:migrate
rake db:test:prepare
bundle install
rake
rake spec:rcov

# Vagrant and Jenkins
http://morethanseven.net/2011/03/20/A-continuous-deployment-example-setup.html

http://www.vagrantbox.es


rvm --gems remove ruby-1.9.2-p180

# PostgreSQL
http://xtremekforever.blogspot.com/2011/05/setup-rails-project-with-postgresql-on.html

http://7enn.com/2011/03/29/fix-posgresql-ident-authentication-failures-for-user-postgres-on-ubuntu/

I am using "root" username:

sudo -u postgres createuser --superuser root

Socket is at /var/run/postgresql

Basically, Ubuntu will have "postgres" as the user account and we have to use other and change their password.

**md5** for /etc/postgresql/8.4/main/pg_hba.conf

# Database administrative login by UNIX sockets
local		all		postgres		md5
local 	all	   root			md5


1. gem install vagrant
2. Go to http://www.vagrantbox.es and get the Ubuntu 11.04 Server 64-bit
3. Go and install cookbook for apt, openssl, java
4. vagrant ssh install VIM and MySQL (Cookbook does not work here)

sudo apt-get update

sudo apt-get install mysql-server libmysqlclient-dev libmysql-ruby mysql-admin

sudo apt-get install vim
5. Go to http://pkg.jenkins-ci.org/debian/ and follow the instruction to install Jenkins to Ubuntu.
6. After installing Jenkins, we just follow this page and install some dependencies (https://rvm.beginrescueend.com/integration/hudson/):

sudo apt-get install curl bison build-essential zlib1g-dev libssl-dev libreadline5-dev libxml2-dev git-core

7. Login to "jenkins" via:

sudo -Hiu hudson

8. touch .bash_profile
9. Make default RVM
rvm --default use 1.9.2
10. Add these to .rvmrc
rvm_install_on_use_flag=1
rvm_project_rvmrc=1
rvm_gemset_create_on_use_flag=1
11. Install bundler
gem install bundler --no-ri --no-rdoc
12. For Nokogiri
sudo apt-get install libxslt-dev libxml2-dev

13. Do port forwarding
config.vm.forward_port "http", 8080, 8765

14. Install Jenkins plugins:
- Greenball
- Github
- Rake
- Ruby metric

15. SSH
ssh-keygen -t rsa -C "mech@me.com"

16. Add id_rsa.pub to github

17. Some gitconfig

git config --global user.name "mech"
git config --global user.email "mech@me.com"
git config --global alias.co checkout
git config --global alias.st status
git config --global alias.br branch
git config --global apply.whitespace nowarn
git config --global color.branch auto
git config --global color.diff auto
git config --global color.interactive auto
git config --global color.status auto


http://jasonseifer.com/2010/04/06/rake-tutorial


## cruisecontrol.rb

./cruise add [project-name] -r git://xxx -s git

export RAILS_ENV=production && ./cruise start

http://www.barinek.com/post/1467412484/rails-3-with-rvm-and-cruise-control



### CC and Apache
http://elwoodicious.com/2009/03/20/continuous-integration-testing-cruisecontrolrb-github-apache-and-you/


### using build_command?
http://groups.google.com/group/cruisecontrolrb-rubyforge-mailing-list/browse_thread/thread/5fbea38d1b6eafa9

http://jerrett.net/entries/general/enforcing-spec-coverage-with-cruisecontrol-rcov-and-rspec
