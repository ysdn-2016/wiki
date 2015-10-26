# Off-site Development Guide

**NOTE:** Don't follow this guide yet, unless you've been instructed to do so. This document is still in development.

* [Environment Setup](#environment-setup)
* [Writing Code](#writing-code)
* [Committing Code](#committing-code)

## Environment Setup

To set up your computer, open a Terminal window and run the following command:

```bash
bash -c "$(curl https://raw.githubusercontent.com/ysdn-2016/site/master/bin/bootstrap)"
```

<sup>Errors? Post in [#off-site-backend](https://ysdn-2016.slack.com/messages/off-site-backend/) and someone can help you out.</sup>

#### Install Github for Mac

Git is a tool to make it easier to work on code in a collaborative way. Normally git is a command-line tool, but Github makes [Github for Mac](https://desktop.github.com/) so you don't need to use the command line. [Download it here](https://desktop.github.com/).

Never used git before? Github has some guides for [getting started](https://help.github.com/desktop/guides/getting-started/), and [for contributing code](https://help.github.com/desktop/guides/contributing/). And if you have questions, ask in [the Slack](https://ysdn-2016.slack.com/messages/). A bunch of people have experience with git and will be able to help you out.

#### Clone the site

The site is broken into a bunch of pieces ("modules") to make development easier. This means you only have to run the parts that are relevant to you. All the modules come together to make the end site.

Depending on what you're working on, you'll only need to clone certain repos.

Project                 | Repository                                        | URL
----------------------- | ------------------------------------------------- | -----
Primary Site            | [@ysdn/site](https://github.com/ysdn-2016/site)   | http://ysdn-2016.herokuapp.com/
Admin Interface         | [@ysdn/admin](https://github.com/ysdn-2016/admin) | http://ysdn-2016.herokuapp.com/admin/
API                     | [@ysdn/api](https://github.com/ysdn-2016/api)     | http://ysdn-2016.herokuapp.com/api/

Clone the ones you'll be making changes to. So if you'll be working on both the [site](https://github.com/ysdn-2016/site) and the [API](https://github.com/ysdn-2016/api), go to each repo and hit the ["Clone in Desktop" button](https://github-images.s3.amazonaws.com/enterprise/11.10.340/user/assets/images/help/repository/clone_in_mac.jpg) in the sidebar.

## Writing code

Open up your cloned repo in your favourite text editor.

To start the web server, change into the cloned repo folder

```bash
cd ysdn-2016-site
npm install
npm run watch
```

This will start the local server at [http://localhost:8080](http://localhost:8080), and will automatically restart the server if you change any files.

#### Changes between modules

This only applies if you're working across multiple modules (`@ysdn/api` *and* `@ysdn/site`).

By default, when you make changes in a module (eg. `@ysdn/api`), it won't automatically update in other modules. This is because dependencies are being downloaded from [npm](http://npmjs.com) rather than linked on the local filesystem. This makes it easier for most people.

But if you're working on a module like `@ysdn/koa` or `@ysdn/api`, you'll want to run [`npm link`](https://docs.npmjs.com/cli/link) to force them to use the file system.

First, navigate to the module you want to link:

```bash
cd ysdn-2016-api
npm link
```

Then in the module you want to link it to:

```bash
cd ../ysdn-2016-site
npm link @ysdn/api
```

This will symlink the folders so changes are automatically synchronized.

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

1. Create [a new branch](https://help.github.com/desktop/guides/contributing/creating-a-branch-for-your-work/) for the task you're working on. The name you give it should be based on the issue number and name. For example, the appropriate branch name for [#19](https://github.com/ysdn-2016/tasks/issues/19) would be `19-connect-api-to-database`
2. Make your changes. Be sure to commit as you go, and try not to lump all your changes into one big commit. If you're coding a gallery page, maybe commit once you have the basic HTML structure done, then the basic CSS, and then for each subsequent refinement.
3. Once you're happy with the changes, push the branch to Github and open a Pull Request. In the pull request text, link to the related issue, and tag 1-2 people to review your code. For a good example, [check out this PR](https://github.com/ysdn-2016/api/pull/1).

## Deploying

Still being figured out...
