## Dev Environment Setup Guide

If you don't already have [Node](http://nodejs.org) installed, you'll want to run the following commands to do so.

First, install [Homebrew](http://brew.sh) if you don't already have it.

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

It should spit out a string like `v4.2.1`. That's it, you're all done.
