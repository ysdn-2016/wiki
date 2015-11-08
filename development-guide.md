# Off-site Development Guide

**NOTE:** Don't follow this guide yet, unless you've been instructed to do so. This document is still in development.

* [Environment Setup](#environment-setup)
* [Writing Code](#writing-code)
* [Committing Code](#committing-code)

## Environment Setup

To set up your computer, open a Terminal window and run the following command:

```bash
bash -c "$(curl -s https://raw.githubusercontent.com/ysdn-2016/site/master/bin/bootstrap)"
```

<sup>Errors? Post in [#off-site-backend](https://ysdn-2016.slack.com/messages/off-site-backend/) and someone can help you out.</sup>

#### Install Github for Mac

Git is a tool to make it easier to work on code in a collaborative way. Normally git is a command-line tool, but Github makes [Github for Mac](https://desktop.github.com/) so you don't need to use the command line. [Download it here](https://desktop.github.com/).

Never used git before? Github has some guides for [getting started](https://help.github.com/desktop/guides/getting-started/), and [for contributing code](https://help.github.com/desktop/guides/contributing/). And if you have questions, ask in [the Slack](https://ysdn-2016.slack.com/messages/). A bunch of people have experience with git and will be able to help you out.

#### Clone the site

The site is contained in the [ysdn-2016/ysdn-2016.github.io](https://github.com/ysdn-2016/ysdn-2016.github.io) repo. Head there and clone the repo via the command line, or, if you're using [Github for Mac](https://desktop.github.com), hit the ["Clone in Desktop" button](https://github-images.s3.amazonaws.com/enterprise/11.10.340/user/assets/images/help/repository/clone_in_mac.jpg) in the sidebar.

## Writing code

Open up your cloned repo in your favourite text editor.

To start the web server, change into the cloned repo folder

```bash
make watch
```

This will start the local server at [http://localhost:8080](http://localhost:8080), and will automatically rebuild the site when changes are made.

## Writing code


##### Front-end

TODO: Add some guides for writing css and js.

## Committing code

The way we're working is based on [this workflow](https://guides.github.com/introduction/flow/).

1. Create [a new branch](https://help.github.com/desktop/guides/contributing/creating-a-branch-for-your-work/) for the task you're working on. The name you give it should be based on the issue number and name. For example, the appropriate branch name for [#19](https://github.com/ysdn-2016/tasks/issues/19) would be `19-connect-api-to-database`
2. Make your changes. Be sure to commit as you go, and try not to lump all your changes into one big commit. If you're coding a gallery page, maybe commit once you have the basic HTML structure done, then the CSS, and then each subsequent refinement.
3. Once you're happy with the changes, push the branch to Github and open a Pull Request. In the pull request text, link to the related issue, and tag a few people to review your code. For a good example, [check out this PR](https://github.com/ysdn-2016/api/pull/1). The PR will automatically create a review server to make it easier to check out your work. Send it to a few people if you'd like to share.

A few other nits:
* When writing a commit message, use present tense, not past tense. Write "Fix sidebar position bug" rather than "Fixed sidebar position bug."

## Deploying

Deployments are still being figured out. For now, when you'd like to push code to the live site, just ping Ross on Slack.
