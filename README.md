 # Description About This Repository
 
[![Build Status](https://travis-ci.org/dotzero/node-url-shortener.svg?branch=master)](https://travis-ci.org/dotzero/node-url-shortener)
[![GitHub tag](https://img.shields.io/github/tag/dotzero/node-url-shortener.svg)](https://github.com/dotzero/node-url-shortener)
[![Dependency Status](https://david-dm.org/dotzero/node-url-shortener.svg)](https://david-dm.org/dotzero/node-url-shortener)
 
 ## Url Shortening WebApp

> A modern, minimalist, and lightweight URL shortener.

## Using

* [NodeJs](http://nodejs.org)
* [ExpressJs](http://expressjs.com/)
* [Redis](http://redis.io)

## Quick Start

```bash
$ git clone git@github.com:DevelopByTarun/Url-Shortening-WebApp.git
$ cd nus
$ npm install
$ node app
```

## Command Line Options

```bash
$ node app -h

Usage: app [options]

Options:
  -u, --url     Application URL               [default: "http://127.0.0.1:3000"]
  -p, --port    Port number for the Express application          [default: 3000]
  --redis-host  Redis Server hostname                     [default: "localhost"]
  --redis-port  Redis Server port number                         [default: 6379]
  --redis-pass  Redis Server password                           [default: false]
  --redis-db    Redis DB index                                      [default: 0]
  -h, --help    Show help                                              [boolean]
```

## Installation on production

```bash
$ git clone git@github.com:DevelopByTarun/Url-Shortening-WebApp.git nus
$ cd nus
$ npm install --production
$ NODE_ENV=production node app --url "http://example.com"
```

# RESTful API

`POST /api/v1/shorten` with form data `long_url=http://google.com`,
`start_date=""`, `end_date=""`, `c_new=false`.

NOTE: You can send the post requests without the date and c_new params

`POST /api/v1/shorten` with form data `long_url=http://google.com`, `start_date`="2019/08/21", `end_date`="2019/08/22", `c_new`=true

The c_new paramter is do that it creates a new short url if one already exists for the url

```json
{
  "hash": "rnRu",
  "long_url": "http://google.com",
  "short_url": "http://127.0.0.1:3000/rnRu",
  "status_code": 200,
  "status_txt": "OK"
}
```

`GET /api/v1/expand/:hash` with query `rnRu`

```json
{
    "start_date": "undefined",
    "end_date": "undefined",
    "hash": "rnRu",
    "long_url": "http://127.0.0.1:3000/rnRu",
    "clicks": "0",
    "status_code": 200,
    "status_txt": "OK"
}
```

OR  if dates are set

```json
{
    "start_date": "2019/08/21",
    "end_date": "2019/08/22",
    "hash": "rnRu",
    "long_url": "http://127.0.0.1:3000/rnRu",
    "clicks": "0",
    "status_code": 200,
    "status_txt": "OK"
}
```

## Tests

To run the test suite, first install the dependencies, then run `npm test`:

```bash
$ npm install
$ npm test
```

## Future Plans

````bash
Better code splitting
````

````bash
Connected another database like Mysql, Mongodb, Oracle
````

````bash
Custom hashes
````

````bash
User registration and associate shortened URLs
````

## License

Released under [the MIT license](LICENSE)
