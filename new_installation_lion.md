## New Installation for Lion

See http://blog.wyeworks.com/2012/4/13/my-osx-rails-installation-using-homebrew-and-rbenv-step-by-step

LANG="en_US.UTF-8" 
LC_COLLATE="en_US.UTF-8" 
LC_CTYPE="en_US.UTF-8" 
LC_MESSAGES="en_US.UTF-8" 
LC_MONETARY="en_US.UTF-8" 
LC_NUMERIC="en_US.UTF-8" 
LC_TIME="en_US.UTF-8" 
LC_ALL=

$ export LC_ALL=en_US.UTF-8
$ export LANG=en_US.UTF-8


1. Install Growl first. Take Mono.growlStyle.
2. Install XCode with iPhone SDK. The free one has iOS 4.3. Usually with git installed, but older version.
3. Install Homebrew, see its wiki, but looks like this
/usr/bin/ruby -e "$(curl -fsSL https://raw.github.com/gist/323731)"
4. brew doctor - this will solve psql problem
5. brew install wget/ghostscript/sphinx/mysql/postgres

If you encounter ASCII error on installing cucumber, do this first:

export LC_CTYPE=en_US.UTF-8

Success. You can now start the database server using:

    postgres -D /usr/local/var/postgres
or
    pg_ctl -D /usr/local/var/postgres -l logfile start

createuser -P postgres

See http://developer.postgresql.org/pgdocs/postgres/app-createuser.html

## Fixing problem with old CP
We need rake 0.8.7

uninitialized constant ActiveSupport::Dependencies::Mutex

We are using RubyGem 1.5.2
Force it via:

gem update --system 1.5.2

symlink sphinx bin_path/searchd_binary_name/indexer_binary_name

sudo ln -s /usr/local/bin/indexer /usr/bin/indexer

## Jobline DB migration

1. Change to /tmp/mysql.sock
2. Download latest backup, and remove scheme migration insert, remove c-stanleyp@avanade.com
3. mysql -uroot -proot jobline_dev < xxx.sql
4. Candidate.all.each {|ca| ca.email="sample_#{ca.email}"; ca.save}
5. Employer.all.each {|emp| emp.email="jlxyz_#{emp.email}"; emp.save}
6. 
