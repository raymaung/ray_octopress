---
layout: post
title: Getting Octopress Up And Running
date: 2013-04-28 18:27
comments: true
categories: 
---

*[Octopress](http://octopress.org/)* is a framework designed for Jekyll, the static blogging engine powering Github Pages. It sits on top of [Jekyll](https://github.com/mojombo/jekyll) and generate **static** html pages from *markdown* files. It comes with a set of useful *rake tasks* to *preview*, *deploy* pages.

The best part is it comes with rake task to have `_deploy` folder set up as *git* sub module that is setup as seperate git repo - it is particular useful when pushing to git pages.

## Setting up locally

[Octopress Setup](http://octopress.org/docs/setup/)

{% codeblock lang:ruby %}

# clone octopress
git clone git://github.com/imathis/octopress.git octopress

# install gems
cd octopress
gem install bundler
bundle install

# install default octopress theme
rake install

{% endcodeblock %}

### Deploying to GitHub pages
GitHub pages a free static web pages hosting provided by GitHub - requires GitHub account.

- Setting up GitHub pages
	- Check out GitHub on how to set up Git Hub Pages for more details.
	- create a *git* repo named `{your_git_hub_account_name_here}.github.com`
	- pushing any static html page will be accessible as web pages at `http://{your_git_hub_account_name_here}.github.io/`
- Run 

{% codeblock lang:ruby %}
rake setup_github_pages
{% endcodeblock %}

## Useful things to know about Octopress

- `_deplou`
