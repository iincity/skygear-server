Welcome to the Oursky Deployment Project

[![Build Status](https://magnum.travis-ci.com/oursky/ourd.svg?token=TS65G314JpxpG31zryWn)](https://magnum.travis-ci.com/oursky/ourd)

Dependencies
============
1. go v1.4
2. https://github.com/tools/godep is used for managing go lib
3. PostgreSQL if you are using pq implementation of oddb:
   * Minimum version: 9.3
   * Recommended version: 9.4


Development
===========
$ `go generate github.com/oursky/ourd/oddb/...`
$ `go build && ./ourd development.ini`

config.ini can be provided in args or os ENV `OD_CONFIG`.

Suggested to use [fresh](https://github.com/pilu/fresh) for local development

$ `OD_CONFIG=development.ini fresh`

Test
====
You may refer to .travis.yml

#### Prepare the testing DB
1. Create test DB `ourd_test` on local PostgreSQL
1. Test case assume the 127.0.0.1 have access to ourd_test, please add following to pg_hba.conf

> host    all             all             127.0.0.1/32            trust

run `go test github.com/oursky/ourd/...`

For local development, you are suggested to open GoConvey to keep track of testing status.

refs: https://github.com/smartystreets/goconvey

Deploy to heroku
================
On `.ini`,
  - [http]host should left empty for using $PORT on heroku deployment
  - [db]option should left empty for usign $DATABASE_URL on heroku deployment
