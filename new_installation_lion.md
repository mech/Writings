## New Installation for Lion

1. Install Growl first. Take Mono.growlStyle.
2. Install XCode with iPhone SDK. The free one has iOS 4.3. Usually with git installed, but older version.
3. Install Homebrew, see its wiki, but looks like this
/usr/bin/ruby -e "$(curl -fsSL https://raw.github.com/gist/323731)"
4. brew doctor - this will solve psql problem
5. brew install wget/ghostscript/sphinx/mysql/postgres

If you encounter ASCII error on installing cucumber, do this first:

export LC_CTYPE=en_US.UTF-8


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

