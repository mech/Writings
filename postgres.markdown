# Postgres

To restart, either
1. pg_ctl stop
2. sudo /etc/init.d/postgresql stop

or on a RedHat, /etc/rc.d/init.d/postgresql stop

## Special Database User Account
The account should only be used to store and own data. No executables owned by this user should be allowed.

"postgres" is a common name to used.

Ubuntu package will usually use the "postgres" user account.
You can log into it by:

sudo -u postgres psql <db_name>

First you must create Unix user account with limited priviledge by using useradd or adduser. Because Mac OS X uses Open Directory yo manage user accounts, there will be no useradd/adduser command.

For Homebrew, it will launch postgre for the `whoami` by default.

dropdb postgres_demo_development
dropdb postgres_demo_test

gem "foo" "~> 2.3" means ">= 2.3" and "< 3.0"



### dscl
1. Find an unused group ID and an unused user ID. Type these to find out:

sudo dscl . -list /Groups PrimaryGroupID
sudo dscl . -list /Users UniqueID

Or if you want it sorted

sudo dscl . -list /Users UniqueID |awk '{print $2 "\t" $1}' |sort -b -g
sudo dscl . -list /Groups PrimaryGroupID |awk '{print $2 "\t" $1}' |sort -b -g



### Ruby interpreter Error

When rake db:create, encountered error

createdb -Opostgres -Eutf8 -T template0 postgres_demo_test


### Command

psql -U postgres

\c [DBNAME]		connect to database
\l 				list all database
\du				list roles
\dt				list tables



dropdb postgres_demo_development
dropuser postgres



http://groups.google.com/group/rubyversionmanager/browse_thread/thread/5a33959ef7b8b013/3e13035183f4fd99?lnk=raot

http://blog.elizabrock.com/post/7213861688/rails-3-1-rake-aborted-dont-know-how-to-build-task

https://rspec.lighthouseapp.com/projects/16211/tickets/704-cucumber-exits-with-status-1-when-pending-steps-exist




