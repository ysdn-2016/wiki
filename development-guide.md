# Off-site Development Guide

**NOTE:** Don't follow this guide yet, unless you've been instructed to do so. This document is still in development.

* [Environment Setup](#environment-setup)
* [Writing Code](#writing-code)
* [Committing Code](#committing-code)

## Environment Setup

To set up your computer, open a Terminal window and run the following command:

```bash
bash -c "$(wget -qO- https://raw.githubusercontent.com/ysdn-2016/site/master/bin/bootstrap)"
```

<sup>Errors? Post in [#off-site-backend](https://ysdn-2016.slack.com/messages/off-site-backend/) and someone can help you out.</sup>

#### Install Github for Mac

Git is a tool to make it easier to work on code in a collaborative way. Normally git is a command-line tool, but Github makes [Github for Mac](https://desktop.github.com/) so you don't need to use the command line. [Download it here](https://desktop.github.com/).

Never used git before? Github has some extensive documentation

#### Clone the site

The site is broken into a bunch of pieces ("modules") to make development easier. This means you only have to run the parts that are relevant to you. All the modules come together to make the end site.

Depending on what you're working on, you'll only need to clone certain repos.

Project                 | Repository                                        | URL
----------------------- | ------------------------------------------------- | -----
Primary Site            | [@ysdn/site](https://github.com/ysdn-2016/site)   | http://ysdn2016.com/
Admin Interface         | [@ysdn/admin](https://github.com/ysdn-2016/admin) | http://ysdn2016.com/admin/
API                     | [@ysdn/api](https://github.com/ysdn-2016/api)     | http://ysdn2016.com/api/

Clone the ones you'll be making changes to. So if you'll be working on both the [site](https://github.com/ysdn-2016/site) and the [API](https://github.com/ysdn-2016/api), go to each repo and hit the ["Clone in Desktop" button](https://github-images.s3.amazonaws.com/enterprise/11.10.340/user/assets/images/help/repository/clone_in_mac.jpg) in the sidebar.

## Writing code

Open up your cloned repo in your favourite text editor.

To start the web server, change into the cloned repo folder

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

The way we're working is based on [this workflow](https://guides.github.com/introduction/flow/):

1. Create a new branch for the task you're working on. Title it using the issue number and name. For example, the appropriate branch name for [#19](https://github.com/ysdn-2016/tasks/issues/19) would be `19-connect-api-to-database`
2. Make your changes. Be sure to commit as you go, and try not to lump all your changes into one big commit. If you're coding a gallery page, maybe commit once you have the basic HTML structure done, then the basic CSS, and then for each subsequent refinement.
3. Once you're happy with the changes, push the branch to Github and open a Pull Request. In the pull request text, link to the related issue, and tag 1-2 people to review your code. For a good example, [check out this PR](https://github.com/ysdn-2016/api/pull/1).

## Deploying

Still being figured out...
