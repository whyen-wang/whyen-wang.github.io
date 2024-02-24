---
layout: post
title: "How to setup GitHub Pages using Jekyll"
categories: GitHub Pages
---
## Prerequisites
1. [Install Git](https://git-scm.com/downloads)
2. [Install Ruby](https://www.ruby-lang.org/en/documentation/installation/)
3. [Install Bundler](https://bundler.io/)

## Create a new public repository
### Name the repository
* For user or organization site named "**username**.github.io".
* For project site named in accordance with naming conventions.

Example:

| user name or project | repository name      |
| -------------------- | -------------------- |
| whyen-wang           | whyen-wang.github.io |
| Nonie                | Nonie                |

## Creating your site
{% highlight console %}
git clone https://github.com/username/username.github.io
# or
git clone https://github.com/username/project.git

cd username.github.io
# or
cd project

mkdir docs
# creates a new folder called docs
cd docs

# create a new Jekyll site
jekyll new --skip-bundle .
{% endhighlight %}

## Modify the configuration
* Go to Gemfile
{% highlight ruby %}
# Add "#" to the beginning of the line that starts with gem "jekyll"
# gem "jekyll" ... <- comment out this line

# Edit the line that starts with # gem "github-pages"
gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins
# gem "github-pages"
{% endhighlight %}
Replace GITHUB-PAGES-VERSION with the latest supported version of the github-pages gem.
You can find this version here: "[Dependency versions](https://pages.github.com/versions/)."
ex. 231
Save and close the Gemfile.

* Go to _config.yml

{% highlight yaml %}
domain: my-site.github.io  # ex.whyen-wang.github.io
url: https://my-site.github.io  # ex. https://whyen-wang.github.io
baseurl: /REPOSITORY-NAME/  # ex. leave "" for user site and project name for project site ex. /Nonie/
{% endhighlight %}

## Testing your GitHub Pages site locally with Jekyll

* Install dependencies
{% highlight console %}
bundle install
{% endhighlight %}

* Run your Jekyll site locally.
{% highlight console %}
Run your Jekyll site locally.
{% endhighlight %}

go to http://127.0.0.1:4000/ to preview your site.

## Add, commit and push your work
{% highlight console %}
git add .
git commit -m 'Initial GitHub pages site with Jekyll'
git push
{% endhighlight %}

## Configure your publishing source.
1. Go to repository settings
2. Go to "Code and automation" > "Pages" > "Branch"
3. Select the branch you pushed and select folder "/docs" and save

## Deploy the site
1. Go to repository actions
2. Wait for the workflow run finished
3. Once the workflow finished, go to "Settings" > "Code and automation" > "Pages" > "GitHub Pages" > "Visit site"
4. Done!

## References
[GitHub Docs - GitHub Pages](https://docs.github.com/en/pages)