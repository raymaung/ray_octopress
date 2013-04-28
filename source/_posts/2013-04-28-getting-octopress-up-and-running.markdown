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

### About GitHub pages
GitHub pages a free static web pages hosting provided by GitHub - requires GitHub account.

- Setting up GitHub pages
	- Check out GitHub on how to set up Git Hub Pages for more details.
	- create a *git* repo named `{your_git_hub_account_name_here}.github.com`
	- pushing any static html page will be accessible as web pages at `http://{your_git_hub_account_name_here}.github.io/`

{% codeblock lang:ruby %}
# setting up for github pages
# See More on 'About GitHub Pages'
# - create a forked version of octopress for the purpose of version controlling the octopres
# - Update the octopress/.git/config
#   - Ask for a git repo url for the project (not the git hub pages)
#   - rename origin to octopress
#     - the changes are not really the octopress core development, so no need for keeping origin
#   - add origin to point to the git repo url from the earlier step
rake setup_github_pages
{% endcodeblock %}
		

## Useful things to know about Octopress

- `_deploy`: where the *github pages repo* as sub module - see `_deploy/.git/config`
- `source`: where the generated content by octopress to be further process by *Jekyll*. (??)
  - `source/_post`: where the markdown files goes

## Recommended Workflow


{% codeblock lang:ruby %}

# Create new post
rake new_post["this is my first blog"]

# Edit generated initial the markdown file
vi source/_posts/20xx-12-31-this-is-my-first-blog.markdown 

# Deploy to GitHub page
# - commit and push github submodule in _deploy
rake gen_deploy

# Commit the new markdown file
git add source/*

# Push
git push

{% endcodeblock %}