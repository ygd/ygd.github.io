---
layout: post
date:   2016-12-12
title:  "Continuously deploy a jekyll project with circleci for free"
img-alt: "Switch from WordPress to Jekyll"
categories: Deployment
tags:
- Jekyll
- Circle CI
- Bitbucket
---
Jekyll and Github Pages is quite cool. But sometimes you don't want your websites source code public. And sometimes you need some more plugins or custom code eg. for generating index pages of front matter itmes. There are some tools like [aerobatic][aerobatic] providing continous deployment [there are also free plans]. But I will show you my totally free auto test and deployment setup with [Bitbucket][bitbucket] and [circleci][circleci] to my private server.

## All you need for deploying you static site automatically via git push

- Your Jekyll project has to be on Bitbucker or Github. I am using Bitbucket in this case because there are private repos included in the free plan. I think there is no need to go into detail.
- From there we will use circleci to checkout our repo for changes, test our static html files and deploy them to our private servers. circleci is a continous delivery platform with a free plan which is totally enough for our purpose.
- Finally you need a server and a domain. We are not going into details for this part as well. But your server should be accessible via ssh as we are going to move files via rsync to your servers.

## The idea

 1. Grab your changes from Bitbucket with circleci.
 2. Let circleci build your site and test the static html files with [html-proofer][html-proofer].
 3. Move your site to your private server via ssh.

## Preparing for circleci

Before we start configuring circleci let's set up a Rakefile which is building and testing our jekyll site. If you do not have [html-proofer][html-proofer] installed yet add `gem 'html-proofer'` to your Gemfile and run `bundle install`. Run `htmlproofer _site` in your jekyll project to test your HTML files and be sure there are no failures.

### Rakefile to build and run HTML tests

Now add a file named `Rakefile` to your repositories root. It will build our Jekyll site and test the outcoming html files with html-proofer. Copy the following into the Rakefile:

{% highlight sh %}
require 'html-proofer'

desc 'Runs html-proofer'
task :test do
  HTMLProofer.check_directory('./_site').run
end

desc 'Builds Jekyll site with all posts'
task :build do
  exit 1 unless system "jekyll build"
end

task :default => [:build, :test]
{% endhighlight %}

### Deployment steps on circleci

It is time to configure your repositories circleci build setup. Add a circle.yml file in your repositories root and copy the following:

{% highlight yaml %}
general:
  branches:
    only:
      - master
test:
  override:
    - bundle exec rake
deployment:
  push_to_server:
    branch: master
      commands:
        - rsync -avz -e "ssh" _site/ YourUser@YouServer.com:YourJekyllFolder
{% endhighlight %}

The first block is checking out only the master branch. You can leave it if you want to check all commits or configure however you want.

The second block is executing the ship method in our Rakefile.

The last block is moving the `_site` folder to your server. Please enter your username on your server, your server address and the final directory. And do not forgot the colon `:` between server and path.

### SSH key on your server

Connect to your server on the command line with `ssh YourUser@Yourserver.com` and your password. Now generate a ssh key with `ssh-keygen`. This will add a hidden folder `.ssh` with the public key `id_rsa.pub` and the private key `id_rsa`. We will dublicate the public key to file called `authorized_keys` with `cp .ssh/id_rsa.pub .ssh/authorized_keys`. Next we will copy the private key and remove the file from the server for security reasons. Run `cat .ssh/id_rsa` and copy the outcome into your clipboard. Remove the file with `rm .ssh/id_rsa`. Add a backup file for you private key on you local machine. Next we will use the private key to authenticate circleci on your server.

### Authorize circleci on your server

Signup to circleci with your Bitbucket account if you do not have already. Now you should see your jekyll project repository on circleci. Click the build project button to create a project and skip the first build. Go to project settings and find the SSH permissions section and create there a new ssh key. Copy you private key to the textarea and save it.

## First build

Now run the first build and check if it is green and your jekyll site is on your server. If you have trouble drop a comment and I'll try help you. Good Luck.

[aerobatic]: https://www.aerobatic.com/ 'aerobatic webiste'
[bitbucket]: https://www.bitbucket.com/ 'Bitbucket website'
[circleci]: https://www.circleci.com/ 'circleci website'
[git]: https://git-scm.com/ 'Git website'
[html-proofer]: https://github.com/gjtorikian/html-proofer 'html-proofer github repositorie'
