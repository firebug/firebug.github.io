---
layout: post
title:  "Setup your environment"
date:   2015-04-06 18:50:30
categories: firebug guides
---
# Setup your environment

## Prerequisites

You will need to install:
  * git (or [msysgit](https://msysgit.github.io/) on Windows)
  * node + npm

### Advised option for Git

You're advised to set the `push.default` option of Git to `current` or `simple`. Prior to Git 2.0, the default option was `matching`, which is dangerous (it means you push all your local branches).

To do so, run either one of these commands (`--global` is added to let you add this option globally by default, but you can also remove it if you prefer):
{% highlight bash %}
git config push.default current
git config push.default simple
{% endhighlight %}

For more information, look at `push.default` [in this manual](http://git-scm.com/docs/git-config.html).

# Cloning the Firebug project

Once Git being installed, you can run this command in the folder of your choice to clone the Firebug.next project:

{% highlight bash %}
git clone git@github.com:firebug/firebug.next.git
{% endhighlight %}

The project will be copied in `./firebug.next`.


# Install JPM

Run this command to install jpm (Jetpack Manager):

{% highlight bash %}
npm install -g jpm
{% endhighlight %}

# Run Firebug.next

In the `firebug.next` folder, simply run:

{% highlight bash %}
jpm run
{% endhighlight %}

This will open a Firefox instance with Firebug.next intalled on it.

You can specify the path to a Firefox binary (and that may be another version of Firefox you downloaded):

{% highlight bash %}
jpm run -b /path/to/firefox
{% endhighlight %}

And you can also specify the path to one of your Firefox profile, like this:
{% highlight bash %}
jpm run -p ~/.mozilla/firefox/<uuid>.<profile name>/
{% endhighlight %}

Note that currently, this does just copy this profile to a temporary folder. In other words, any preference you change while running JPM will be lost after you close Firefox.

# Contribute

## Prepare to hack

A good practice is to pick an issue to start with. If not, you can submit one.

Then fetch the last modifications from the other developers:

{% highlight bash %}
git checkout master
git pull --rebase
{% endhighlight %}

and create a new branch on your machine (replace XXXX by the number of the issue you're about to work on):
{% highlight bash %}
git checkout -b issueXXXX master
{% endhighlight %}

Note that your branch is not submitted on Github until you push it.

## Hack

Edit files in the Firebug.next project. Note that to take your changes into account, you have to restart Firefox every time.

Also take a look at the [Debugging Tips](https://github.com/firebug/firebug.next/wiki/Debugging-Firebug-Tips-&-Tricks) to make your life much easier while hacking Firebug.

## Committing and submitting

Once your work ready to push, you have to:
* index your work (so your changes will be ready to be committed)
* commit
* push your commit to Github

Before indexing, a good practice is to look at your changes:
{% highlight bash %}
git diff
{% endhighlight %}

Then you can index your change:
{% highlight bash %}
git add /path/to/file-to-add.js
{% endhighlight %}

Tip : use the `-p` of `git add` option to index your changes chunks by chunks.

Then commit (replace XXXX by the number of your commit):
{% highlight bash %}
git commit -m "#XXXX: SOME COMMIT MESSAGE HERE"
{% endhighlight %}

If you have access to the Firebug Working Group account, you should be able to commit directly your branch:
{% highlight bash %}
git push origin issueXXXX
{% endhighlight %}