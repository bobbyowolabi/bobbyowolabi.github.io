---
title: Schedule Jekyll Posts With GitHub
bigimg: /img/pexels-mat-brown-552598.jpeg
description: 
comments: true
published: true
---

tldr; *You can effectively schedule your jekyll posts on Github Pages via a GitHub Action to build your site at a regular scheduled time and future date your posts.  [[Steps]](#steps)*

### First Scheduled Post
If all goes well, the post you are reading now will be my first post whose publication was facilitated by a github action. Specially today at 1:51 PM UTC 😀.

### Motivation
In the beginning, webpages were very basic snd static.  It was pretty much HTML and text content.  Overtime, web pages became more dynamic, requiring a backend systems to update content on the page.  Web source files became very bloated, large in size and hard to read.  Unfortunately, this is still often the case today; however, there is a push to go back to a world web where webpage source code is much simpler focusing more on content and less on functionality.  This is where [Jamstack][jamstack] comes in.

**<u>J</u>**avascript **<u>A</u>**PIs **<u>M</u>**arkup Stack

Nothing more ... nothing else.

No owned backend services.  Just a webserver to host your HTML files. 

I use Jekyll to build this blog.  [Jekyll][jekyll-jamstack] is a popular tool in the Jamstack space that allows you to focus on the content of your site while to it handles all the details of generating all of the web page source code. 

This paradigm is great; however, you loose functionality that is often available when your site and blogging framework has a back end; such as scheduling posts.  This is something I've thought about often and have thought about intricarte plans of cron jobs running on my personal machines that issue API requests trigger builds of my site <sup>[[a]](#jekyll-scheduling-research)</sup>.  With GitHub actions, these kinds of tasks are much simpler.  A GitHub action workflow file can be configured to perform a series of tasks relating to your respository on a server.  This is very powerful.  The rest of this post will be on going through how I configured a GitHub action to effectively schedule this post.

# Steps 
*Assumptions: The following steps are for a `username.github.io` repo.  Likely the steps will be similar for a project or organization site.*

1. **Tell Jekyll Not to Publish Posts Dated in the Future** <br/>
This option is really what makes this setup work.  We can accomplish this by updating the `future` value to false in the `_config.yml` file in the root of your repository. <br/><br/>
{% highlight yaml linenos %}
future: false
{% endhighlight %}


1. **Create a GitHub Token** <br/>
The GitHub action will need a token in order to authenticate and execute actions <br/><br/>
On your GitHub profile, under Developer Settings, go to the Personal Access Tokens section.
Create a token. Give it a name like “GitHub Actions” and ensure it has permissions to public_repos (or the entire repo scope for private repository) — necessary for the action to commit to the gh-pages branch.
Copy the token value.
Go to your repository’s Settings and then the Secrets tab.
Create a token named GH_ACTIONS_TOKEN (important). Give it a value using the value copied above.

1. **Create the GitHub Actions Workflow File** <br/>
Setup the Create a GitHub Actions workflow file, such as `jekyll.yml`, in a directory `.github/workflows` in the directory of your jekyll site source.


1. **Configure the `jeffreytse/jekyll-deploy-action` GitHub Action to Build** <sup>[[b]](#jekyll-github-action-options)</sup> <br/>
{% highlight yaml linenos %}
name: Build and deploy Jekyll site to GitHub Pages

on:
  schedule:
    - cron: "50 13 * * *"
  workflow_dispatch:

jobs:
  build_and_deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2

      # Use GitHub Actions' cache to cache dependencies on servers
      - uses: actions/cache@v2
        with:
          path: vendor/bundle
          key: ${{ runner.os }}-gems-${{ hashFiles('**/Gemfile.lock') }}
          restore-keys: |
            ${{ runner.os }}-gems-
      # Use GitHub Deploy Action to build and deploy to Github
      - uses: jeffreytse/jekyll-deploy-action@v0.3.1
        with:
          provider: 'github'
          token: ${{ secrets.GH_ACTIONS_TOKEN }} 
          branch: 'gh-pages'
          cname: 'www.bobbyowolabi.com'
{% endhighlight %}

*Some Configuration Notes*:
* Figure out how often you would like the site to build using https://crontab.guru/.  Put this value in the cron value.
* The `workflow_dispatch` option is optional.  It provides you with the ability to run your workflow on demand by providing an icon in the Actions tab of your repository.  This is helpful for troubleshooting versus trying to update the cron schedule value.
* If you do not use a custom domain, the cname property is not necessary.
* The actions/cache action is also option, but should speed up deploy time by caching the site dependencies.

Update page settings for published code



### Notes

[<a name="jekyll-scheduling-research">a</a>] Some resources that I have come across over the years:
* [How to Schedule Jekyll Posts on Github Pages](https://alxmjo.com/2017/05/30/how-to-schedule-posts-with-jekyll/)
* [Scheduling Posts with Jekyll, Github Pages & Zapier](http://www.petecorey.com/blog/2014/12/29/scheduling-posts-with-jekyll-github-pages-and-zapier)

[<a name="jekyll-github-action-options">b</a>] Initially I started using the helaili/jekyll-action.  It worked but it does not support custom domains by creating the CNAME file ... <To finish>



# Background
Hopefully, this background will save you some trouble I went through, in getting this all setup.

## There Are Types of Github Pages
## Source Code vs. Published Code
## The Default Publishing Source
Where Github 
## There Are Two Settings In Play
The jekyll action settings
repository pages settings

These set of settings need to be aligned.

## Check Repo Name
It is documented for a user site to be of the form username.github.io.  My user site has not been that way for years; however, it still works.  But just to be safe with this new setup, I encourage us to make sure that it is the same.

rename in github

git remote set-url origin https://github.com/bobbyowolabi/bobbyowolabi.github.io

### Using a Custom Domain

#### Make Sure to Update DNS Settings
If you change repo name, you'll need to update your DNS settings DNS provider

#### Update Github Custom domain Property 
Likely will need to update this again if you change the branch.  It will add a CNAME file in the new branch.


### References




Errors:
             Error: could not read file /github/workspace/vendor/bundle/ruby/2.7.0/gems/jekyll-3.7.4/lib/site_template/_posts/0000-00-00-welcome-to-jekyll.markdown.erb: Invalid date '<%= Time.now.strftime('%Y-%m-%d %H:%M:%S %z') %>': Document 'vendor/bundle/ruby/2.7.0/gems/jekyll-3.7.4/lib/site_template/_posts/0000-00-00-welcome-to-jekyll.markdown.erb' does not have a valid date in the YAML front matter.
             ERROR: YOUR SITE COULD NOT BE BUILT:
                    ------------------------------------
                    Invalid date '<%= Time.now.strftime('%Y-%m-%d %H:%M:%S %z') %>': Document 'vendor/bundle/ruby/2.7.0/gems/jekyll-3.7.4/lib/site_template/_posts/0000-00-00-welcome-to-jekyll.markdown.erb' does not have a valid date in the YAML front matter.

https://github.com/jekyll/jekyll/issues/5267#issuecomment-241379902
Solution: in _config.yml put exclude: [vendor]


error:
Error: Cannot publish on branch master
https://stackoverflow.com/questions/68705337/jekyll-github-action-stopped-working-and-now-fails-with-error-message-cannot-p


https://github.com/marketplace/actions/jekyll-actions

https://jekyllrb.com/docs/continuous-integration/github-actions/

https://github.com/helaili/jekyll-action



https://stackoverflow.com/questions/2432764/how-to-change-the-uri-url-for-a-remote-git-repository


It looks like https://github.com/jeffreytse/jekyll-deploy-action supports cname

https://www.cyberciti.biz/faq/create-a-file-in-linux-using-the-bash-shell-terminal/


### Notes
[<a name="series-photo">\*</a>] [*Photo by Mat Brown from Pexels*][post-photo]

### Reference




[jamstack]: https://jamstack.org/what-is-jamstack/
[jekyll-jamstack]: https://jamstack.org/generators/jekyll/

https://github.com/jeffreytse/jekyll-deploy-action

https://github.community/t/helaili-jekyll-action-v2-fail-for-error-cannot-publish-on-branch-master/179257

https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site


https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#publishing-sources-for-github-pages-sites

https://jekyllrb.com/docs/continuous-integration/github-actions/


https://github.com/helaili/jekyll-action#jekyll-action


[post-photo]: https://www.pexels.com/photo/round-silver-colored-chronograph-watch-552598/
