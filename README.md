
pa11y
=====

pa11y is your automated accessibility testing pal. It runs [HTML CodeSniffer][sniff] from the command line for programmatic accessibility reporting.

**Note: this is an in-progress 2.0 rewrite**

[![NPM version][shield-npm]][info-npm]
[![Node.js version support][shield-node]][info-node]
[![Build status][shield-build]][info-build]
[![Dependencies][shield-dependencies]][info-dependencies]
[![GPL v3.0 licensed][shield-license]][info-license]

```sh
pa11y nature.com
```

```js
var pa11y = require('pa11y');
pa11y(options, function (error, test) {
    test('nature.com', function (error, results) {
        /* ... */
    });
});
```


Table Of Contents
-----------------

- [Requirements](#requirements)
- [Command-Line Interface](#command-line-interface)
- [JavaScript Interface](#javascript-interface)
- [Configuration](#options)
- [Contributing](#contributing)
- [License](#license)


Requirements
------------

pa11y requires [Node.js][node] 0.10+ and [PhantomJS][phantom] to run.

On a Mac, you can install these with [Homebrew][brew]:

```sh
$ brew install node
$ brew install phantomjs
```

If you're on Linux, you'll probably be able to work it out.

Windows users approach with caution – we've been able to get pa11y running (Windows 7, Node 0.10) but only after installing Visual Studio and the Windows SDK (as well as Git, Python and PhantomJS). The [Windows installation instructions for node-gyp][windows-install] are a good place to start.


Command-Line Interface
----------------------

Install pa11y globally with [npm][npm]:

```
npm install -g pa11y
```

This installs the `pa11y` command-line tool:

```
Usage: pa11y [options] <url>

  Options:

    -h, --help                 output usage information
    -V, --version              output the version number
    -s, --standard <name>      the accessibility standard to use: Section508, WCAG2A, WCAG2AA (default), WCAG2AAA
    -r, --reporter <reporter>  the reporter to use: cli (default), csv, json
    -l, --level <level>        the level of message to fail on (exit with code 2): error, warning, notice
    -c, --config <path>        a JSON config file
    -p, --port <port>          the port to run PhantomJS on
    -t, --timeout <ms>         the timeout in milliseconds
    -d, --debug                output debug messages
```

### Running Tests

Run an accessibility test against a URL:

```
pa11y nature.com
```

Run a test with CSV reporting and save to a file:

```
pa11y --reporter csv nature.com > report.csv
```

Run pa11y with the Section508 ruleset:

```
pa11y --standard Section508 nature.com
```

### Exit Codes

The command-line tool uses the following exit codes:

```
0 = pa11y ran successfully, and there are no errors
1 = pa11y failed run due to a technical fault
2 = pa11y ran successfully but there are errors in the page
```

By default, only accessibility issues with a type of `error` will exit with a code of `2`. This is configurable with the `--level` flag.

Exit on errors only, ignoring warnings and notices:

```
pa11y --level error nature.com
```

Exit on errors and warnings, ignoring notices:

```
pa11y --level warning nature.com
```

Exit on all messages:

```
pa11y --level notice nature.com
```

### Command-Line Configuration

The command-line tool can be configured with a JSON file as well as arguments. By default it will look for a `pa11y.json` file in the current directory, but you can change this with the `--config` flag:

```
pa11y --config ./path/to/config.json nature.com
```

For more information on configuring pa11y, see the [configuration documentation](#configuration).

### Reporters

The command-line tool can report test results in a few different ways using the `--reporter` flag. The built-in reporters are:

  - `cli`: output test results in a human-readable format
  - `csv`: output test results as comma-separated values
  - `json`: output test results as a JSON array

You can also write and publish your own reporters; TODO.


JavaScript Interface
--------------------

TODO


Configuration
-------------

TODO


Contributing
------------

To contribute to pa11y, clone this repo locally and commit your code on a separate branch.

Please write unit tests for your code, and check that everything works by running the following before opening a pull-request:

```sh
make lint test
```


License
-------

Copyright 2013 Nature Publishing Group.  
pa11y is licensed under the [GNU General Public License 3.0][info-license].



[brew]: http://mxcl.github.com/homebrew/
[node]: http://nodejs.org/
[npm]: https://www.npmjs.com/
[phantom]: http://phantomjs.org/
[sniff]: http://squizlabs.github.com/HTML_CodeSniffer/
[windows-install]: https://github.com/TooTallNate/node-gyp#installation

[info-dependencies]: https://gemnasium.com/nature/pa11y
[info-license]: LICENSE
[info-node]: package.json
[info-npm]: https://www.npmjs.com/package/pa11y
[info-build]: https://travis-ci.org/nature/pa11y
[shield-dependencies]: https://img.shields.io/gemnasium/nature/pa11y.svg
[shield-license]: https://img.shields.io/badge/license-MIT-blue.svg
[shield-node]: https://img.shields.io/node/v/pa11y.svg?label=node.js%20support
[shield-npm]: https://img.shields.io/npm/v/pa11y.svg
[shield-build]: https://img.shields.io/travis/nature/pa11y/master.svg
