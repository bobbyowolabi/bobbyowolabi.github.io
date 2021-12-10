---
title: Schedule Jekyll Posts With GitHub
bigimg: /img/pexels-mat-brown-552598.jpeg
description: 
comments: true
published: true
---

tldr; *You can effectively schedule your jekyll posts on Github Pages via a GitHub Action to build your site at a regular scheduled time and future date your posts.  [[Steps]](#steps)*

# First Scheduled Post
If all goes well, the post you are reading now will be my first post whose publication was scheduled by a github action. Specially at x:Xx pm UTC 😀.

# Motivation

https://alxmjo.com/2017/05/30/how-to-schedule-posts-with-jekyll/
http://www.petecorey.com/blog/2014/12/29/scheduling-posts-with-jekyll-github-pages-and-zapier/?from=east5th.co

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

## GitHub Actions Cannot Publish In Same Directory 
When you the default branch with no directory, it looks like Github publishes your site automatically and does not save your published sources in any repo.

Likely you can push to your default repo, I suspect that you will need to update the folder that the published sources is being pushed to.

## My Reccomendation
Separate your source code and published code into two branches

pros - explicitly see your publsihed code, could help with troubleshooting.  You get a history of how your 

If you want to use your default branch, you'll likely need to update the folder it is pushed to in both your action and pages setup.

# Steps 
*Assumptions: Using `username.github.io` repo, likely steps will be similar if not the same, but have not tested.*

## Check Repo Name
It is documented for a user site to be of the form username.github.io.  My user site has not been that way for years; however, it still works.  But just to be safe with this new setup, I encourage us to make sure that it is the same.

rename in github

git remote set-url origin https://github.com/bobbyowolabi/bobbyowolabi.github.io

### Using a Custom Domain

#### Make Sure to Update DNS Settings
If you change repo name, you'll need to update your DNS settings DNS provider

#### Update Github Custom domain Property 
Likely will need to update this again if you 


## Setup Jekyll Action
1. 

1. Create a GitHub Actions workflow file, such as `jekyll.yml`, in a directory `.github/workflows` in the directory of your jekyll site source.

1. bar


Create a GitHub actions workflow file in directory .github/workflows/jekyll.yml


{% highlight yaml linenos %}
name: Build and deploy Jekyll site to GitHub Pages

on:
  schedule:
    - cron: "0 6 * * *"

jobs:
  github-pages:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: helaili/jekyll-action@v2
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
{% endhighlight %}

Figure out how often you would like the site to build using https://crontab.guru/.  Put this value in the cron value.

Create a Github Token

On your GitHub profile, under Developer Settings, go to the Personal Access Tokens section.
Create a token. Give it a name like “GitHub Actions” and ensure it has permissions to public_repos (or the entire repo scope for private repository) — necessary for the action to commit to the gh-pages branch.
Copy the token value.
Go to your repository’s Settings and then the Secrets tab.
Create a token named GH_ACTIONS_TOKEN (important). Give it a value using the value copied above.


Update config.yml not to publish posts dated for the future.

Update page settings for published code

# Troubleshooting

### Notes

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



### Notes
[<a name="series-photo">\*</a>] [*Photo by Mat Brown from Pexels*][post-photo]

### Reference
https://github.community/t/helaili-jekyll-action-v2-fail-for-error-cannot-publish-on-branch-master/179257

https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site


https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#publishing-sources-for-github-pages-sites

https://jekyllrb.com/docs/continuous-integration/github-actions/


https://github.com/helaili/jekyll-action#jekyll-action


[post-photo]: https://www.pexels.com/photo/round-silver-colored-chronograph-watch-552598/
