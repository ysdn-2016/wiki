# Off-site Development Guide

**PLEASE NOTE:** If you're not on the back-end team, don't follow this guide just yet. Things may change between now and when front-end development starts, so wait until this document is a little further along.

Contents:
* [Setup](#setup)
* [Running the server](#running-the-server)
* [Writing Code](#writing-code)
* [Committing Code](#committing-code)

## Environment Setup

For a quick-and-easy setup, just open Terminal and paste in the command below.

```bash
bash -c "$(wget -qO- https://raw.githubusercontent.com/ysdn-2016/site/master/bin/bootstrap)"
```

#### Install Github for Mac

Git is a tool to make it easier to collaboratively work on code. Normally git is a command-line tool, but Github makes [Github for Mac](https://desktop.github.com/) so you don't need to use the command line.

Don't know how to use Git? Post in the Slack! Someone will be able to give you a run-down.

#### Install Node

The site runs on [Node](http://nodejs.org), a tool for writing web server code in Javascript (as opposed to PHP or Ruby). In order to develop locally, you'll need to have Node installed.

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

Now, if you run

```bash
node -v
```

It should spit out a string like `v4.2.1` or higher. Ask for help if it doesn't.

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

This will start the local server at http://localhost:8080. It will automatically restart the server if you change any files in the current directory.

#### Changes between modules

By default, if you make changes in a module (eg. `@ysdn/api`), it doesn't automatically update in other modules. This is because, by default, dependencies are being downloaded from [npm](http://npmjs.com). Many modules won't be changing very often (eg. `@ysdn/koa`, `@ysdn/api`), and snapshotting them like this makes working on Github easier.
If you'll be working on a module like `@ysdn/koa` or `@ysdn/api`, and want changes in one to automatically show up in the other,  To automatically link changes, you can [`npm link`](https://docs.npmjs.com/cli/link) them.

```bash
cd ysdn-2016-api
npm link
cd ../ysdn-2016-site
npm link @ysdn/api
```

This will symlink between repositories so changes auto-update.

#### Module scripts

Each module has a few helpful scripts you can run.

* `npm start`: starts the webserver
* `npm run watch`: starts the webserver with auto-reloading (use this for development)
* `npm lint`: runs the linter to identify code style issues
* `npm test`: runs any available tests
* `npm run publish`: publishes the module to npm

## Writing code


##### Front-end

TODO: Add some guides for writing css and js.

##### Back-end

* Tutorial: [Intro to npm](https://www.youtube.com/watch?v=_O-ETvNqHI4)
* Tutorial: [Intro to koa](https://www.youtube.com/watch?v=Div1km7DQrI)
* Tutorial: [Getting Started with Mocha](http://mochajs.org/#getting-started) (testing framework)

If you're writing backend code, be sure to add tests to let us know if something breaks. See [@ysdn/api](https://github.com/ysdn-2016/api) for an example.

## Committing code

TODO: Add some guides about git etiquette

Using git demands a bit of etiquette, because we're all working in the same space.

* Commit as you go. Don't lump all your changes into one big commit.
* Make your changes in a new branch, titled after the issue number and name. So the appropriate branch name for [#19](https://github.com/ysdn-2016/tasks/issues/19) would be `19-connect-api-to-database`
* Send changes as pull requests, link to the related issue, and tag 1-2 people to review your code.

## Deploying

Still being figured out...
