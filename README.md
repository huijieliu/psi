# psi [![Dependency Status](https://david-dm.org/addyosmani/psi.svg)](https://david-dm.org/addyosmani/psi) [![devDependency Status](https://david-dm.org/addyosmani/psi/dev-status.svg)](https://david-dm.org/addyosmani/psi#info=devDependencies) [![Build Status](https://travis-ci.org/addyosmani/psi.svg?branch=master)](https://travis-ci.org/addyosmani/psi)

> PageSpeed Insights With Reporting

![](screenshot.png)

Run mobile and desktop performance tests for your deployed site using [Google PageSpeed Insights](https://developers.google.com/speed/docs/insights/v1/getting_started) with tidy reporting for your build process. A sample [Gulpfile](https://github.com/addyosmani/psi-gulp-sample) demonstrating use is also available.


## Install

```sh
$ npm install --save psi
```


## Usage

When using this module for a production-level build process, registering for an API key from the [Google Developer Console](https://developers.google.com/speed/docs/insights/v1/getting_started#auth) is recommended.

```js
var psi = require('psi');

psi({
	// key: '...', optional
	url: 'http://html5rocks.com',
	paths: '',           // optional
	locale: 'en_GB',     // optional
	strategy: 'mobile',  // optional
	threshold: 80        // optional
});
```

Optionally, a callback is also available with access to the response:

```js
psi(options, function (err, data) {
	console.log(data.score);
	console.log(data.pageStats);
});
```

### Options

#### url

*Required*  
Type: `string`

URL of the page for which the PageSpeed Insights API should generate results.

#### locale

Type: `string`  
Default: `en_US`

The locale that results should be generated in (e.g 'en_GB').

#### strategy

Type: `string`  
Default: `mobile`
Values: `mobile`, `desktop`

The strategy to use when analyzing the page.

#### threshold

Type: `number`  
Default: `70`

Threshold score that is needed to pass the pagespeed test

#### paths

Type: `array`

An array of URL paths that are appended to the URL

#### key

Type: `string`  
Default: `nokey`

[Google API Key](https://code.google.com/apis/console/)

Unless Specified defaults to use the free tier on PageSpeed Insights. Good for getting a feel for how well this tool works for you.

#### format

Type: `string`
Default: `cli`

The format of the report generated from the PageSpeed Insights API. Supported formats: cli, json and tap.


## CLI

```sh
$ npm install --global psi
```

You can then casually use it with your key:

```sh
$ psi http://todomvc.com --key 'YOUR_KEY_GOES_HERE'
```

Humanized URLs are also supported:

```
$ psi todomvc.com
```

The following optional flags are also supported:

```sh
$ psi <url> --key=<key> --prettyprint=<true> --userIp=<userIp> --locale=<locale> --strategy=<mobile|desktop> --format<cli|json|tap>
```

```sh
$ psi http://www.html5rocks.com --strategy=mobile
```

## Getting PSI into your build

A sample [Gulp](https://github.com/addyosmani/psi-gulp-sample) project using PSI is available.

If you use Grunt, [grunt-pagespeed](https://github.com/jrcryer/grunt-pagespeed) is a task by James Cryer that uses PSI under the hood.

For testing local project, we recommend using [ngrok](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/).


## License

Apache-2.0  
Copyright 2014 Google Inc
