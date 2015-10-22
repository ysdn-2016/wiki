# Off-site Development Guide

**PLEASE NOTE:** If you're not on the back-end team, don't follow this guide just yet. Things may change between now and when front-end development starts, so wait until this document is a little further along.

**Also**, Ryan and Nate, please provide feedback on this doc. Other people are going to be following this process soon, and the simpler it is, the better.

If you don't care how any of this works and just want to get things rolling, in the near future there will be a bootstrap script you can run to set things up automatically.

Contents:
* [Setup](#setup)
* [Running the server](#running-the-server)
* [Writing Code](#writing-code)
* [Committing Code](#committing-code)

## Setup

#### Install Github for Mac

Our team will be operating over Github, it's important you know how to use git. Git is a tool to make it easier to collaboratively work on code. Normally git is a command-line tool, but Github puts out a nice little tool called [Github for Mac](https://desktop.github.com/) so you don't need to use the command line.

#### Install Node

If you don't already have [Node](http://nodejs.org) installed, you'll want to run the following commands to do so.

First, install [Homebrew](http://brew.sh) if you don't already have it. Open up terminal and type

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Next up, install [Node](http://nodejs.org) and [n](http://github.com/tj/n)

```bash
brew install node
npm install -g n
n latest
```

Nice! Now, if you run

```bash
node -v
```

It should spit out a string like `v4.2.1` or higher. If not, ping Ross. Otherwise, nice! You've got Node installed.

#### Clone the codebase

The site is structured into a bunch of modules to make developing easier and more contained. Depending on what you're working on, you'll only need to clone certain repos.

Project                 | Repository
----------------------- | -------------
Primary Site            | [@ysdn/site](https://github.com/ysdn-2016/site)
Admin Interface         | [@ysdn/admin](https://github.com/ysdn-2016/admin)
API                     | [@ysdn/api](https://github.com/ysdn-2016/api)

Clone the ones you'll be making changes to. So if you'll be working on both the site and the API, run

```bash
git clone git@github.com:ysdn-2016/site.git ysdn-2016-site
git clone git@github.com:ysdn-2016/api.git ysdn-2016-api
```

## Running the server

To run a module, do the following:

```bash
cd ysdn-2016-site
npm install
npm run watch
```

This will start the local server at http://localhost:8080, and restart the server if you change any files.

#### Changes between modules

By default, if you make changes in a module (eg. `@ysdn/api`), it doesn't automatically update in other modules. This is because dependencies go through npm initially. Many modules won't be changing very often (eg. `@ysdn/koa`, `@ysdn/api`), and snapshotting them like this makes working on Github easier. To automatically link changes, you can [`npm link`](https://docs.npmjs.com/cli/link) them.

```bash
cd ysdn-api
npm link
cd ../ysdn-site
npm link @ysdn/api
```

This will create a symlink to the folder and make it so changes auto-update.

#### Module scripts

Each module has a few helpful scripts you can run. `npm start` starts the webserver, `npm test` runs any available tests, and `npm run publish` publishes the module to npm. If you're doing a lot of development, `npm run watch` will watch the files for changes and auto-reload the server.

(In case it's not clear, [npm](https://npmjs.org) is a package manager, like [pip](https://pip.readthedocs.org/en/stable/) for Python or [RubyGems](https://rubygems.org/) for Ruby)

## Writing code

TODO: Add some guides for writing css and js.

If you're writing backend code, be sure to add tests to make sure nothing breaks. See [@ysdn/api](https://github.com/ysdn-2016/api) for an example.

## Committing code

TODO: Add some guides about git etiquette

Using git demands a bit of etiquette, because we're all working in the same space.

* Make your changes in a new branch, titled after the issue number and name. So the appropriate branch name for [#19](https://github.com/ysdn-2016/tasks/issues/19) would be `19-connect-api-to-database`
* Send changes as pull requests, link to the related issue, and tag 1-2 people to review your code.
