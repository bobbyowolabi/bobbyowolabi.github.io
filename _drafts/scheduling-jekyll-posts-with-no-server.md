---
title: Schedule Jekyll Posts With GitHub
description: 
comments: true
published: false
---

Create a workflow file in directory .github/workflows/jekyll.yml


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




https://alxmjo.com/2017/05/30/how-to-schedule-posts-with-jekyll/
http://www.petecorey.com/blog/2014/12/29/scheduling-posts-with-jekyll-github-pages-and-zapier/?from=east5th.co
