---
title: Schedule Jekyll Posts With GitHub
bigimg: /img/pexels-mat-brown-552598.jpeg
description: 
comments: true
published: true
---

tldr; *You can effectively schedule your jekyll posts on Github Pages via a GitHub Action to build your site at a regular scheduled time and future date your posts.  [[Skip to Steps]](#steps)*

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
This option is really what makes this setup work.  We can accomplish this by updating the `future` value to false in the `_config.yml` file in the root of your repository.

    ```yaml
    future: false
    ```

1. **Create a GitHub Token** <br/>
The GitHub action will need a token in order to authenticate and execute actions on your repository.

    1. *Navigate to Your GitHub Profile Settings* <br/>
    `Profile Icon -> Settings -> Developer Settings -> Personal access tokens -> New personal access token`

    1. *Povide a Name, Expiration and Access Scopes & Generate Token* <br/>
    The full `repo` access should suffice (Includes access to both public & private repositories).  The GitHub action will need to read and write to the repository.

    1. *Copy The Access Token For Later Use*
  
1. **Add GitHub Token As a Secret to Your Repository**
The GitHub Action will access your token through this secret value.

    * **Navigate to Your Repository Setting** <br/>
    `Settings -> Secrets -> New repository secret` 

        Give it a name (i.e. `GH_ACTIONS_TOKEN`) and enter in the token value created in the previous step above and click add "Add Secret".

1. **Create the GitHub Actions Workflow File** <br/>
Create a new file in your repository (i.e. `jekyll.yml`), in the directory `.github/workflows` 

1. **Configure the `jeffreytse/jekyll-deploy-action` GitHub Action to Build & Deploy Your Site** <sup>[[b]](#jekyll-github-action-options)</sup> <br/>
    
    **File**: `.github/workflows/jekyll.yml`:
    <!--- Add an image of the source with a download link -->
    ```yaml
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
    ```

    *Some Configuration Notes*:
    * Figure out how often you would like the site to build using https://crontab.guru/.  Put this value in the cron value above.
    * The `workflow_dispatch` value is optional.  It provides you with the ability to run your workflow on demand by providing an icon in the Actions tab of your repository.  This is helpful for troubleshooting versus trying to update the cron schedule value.
    * If you do not use a custom domain, the cname property is not necessary.
    * The actions/cache action is also optional, but should speed up deploy time by caching the site dependencies.


1. Update page settings for published code to point to correct branch

    Update Github Custom domain Property 
    Likely will need to update this again if you change the branch.  It will add a CNAME file in the new branch.


1. Test it out by clicking the run button



### Notes

[<a name="jekyll-scheduling-research">a</a>] Some resources that I have come across over the years:
* [How to Schedule Jekyll Posts on Github Pages](https://alxmjo.com/2017/05/30/how-to-schedule-posts-with-jekyll/)
* [Scheduling Posts with Jekyll, Github Pages & Zapier](http://www.petecorey.com/blog/2014/12/29/scheduling-posts-with-jekyll-github-pages-and-zapier)

[<a name="jekyll-github-action-options">b</a>] Initially I started using the helaili/jekyll-action.  It worked but it does not support custom domains by creating the CNAME file ... <To finish>


[<a name="series-photo">\*</a>] [*Photo by Mat Brown from Pexels*][post-photo]

### Reference
https://github.com/jeffreytse/jekyll-deploy-action

https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages#publishing-sources-for-github-pages-sites

https://jekyllrb.com/docs/continuous-integration/github-actions/

https://github.com/helaili/jekyll-action#jekyll-action


[jamstack]: https://jamstack.org/what-is-jamstack/
[jekyll-jamstack]: https://jamstack.org/generators/jekyll/
[post-photo]: https://www.pexels.com/photo/round-silver-colored-chronograph-watch-552598/
