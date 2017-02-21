# map.wikihouse.cc

The community map for [WikiHouse](https://wikihouse.cc)

## Development setup

Prerequisites:

* Ruby 2.4.0
* PostgreSQL
* Heroku credentials

Then run `bin/setup`. This script is idempotent, so it can be re-run if
something fails.

## Copying production database locally

```
$ dropdb wikihouse-map_development
$ heroku pg:backups:download
$ pg_restore --verbose --clean --jobs=4 --disable-triggers --no-acl --no-owner -h localhost -d wikihouse-map latest.dump
$ rm latest.dump
```

## Day-to-day development

Run `rails s` to start the web server. You can now visit the site at [http://localhost:3000](http://localhost:3000).

Run `rspec` to run the tests.

## Deploying

The github master branch is auto-linked to heroku, so a simple `git push` will put your code on github and heroku at the same time.

## DNS

Managed by CloudFlare

## Monitoring

The site is periodically pinged by uptimerobot.
