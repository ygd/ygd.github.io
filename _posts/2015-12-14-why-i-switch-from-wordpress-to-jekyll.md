---
layout: post
date:   2015-12-14
title:  "Why I switch from WordPress to Jekyll on GitHub-Pages"
img: "/assets/img/switch-from-wordpress-to-jekyll.jpg"
img-alt: "Switch from WordPress to Jekyll"
categories: Webdesign
tags:
- Jekyll
- GitHub-Pages
- WordPress
- Ruby
---

First things first, this is not a [WordPress][wp] bashing or [Jekyll][jekyll] hype post. I will just list some reasons why I moved from WordPress to Jekyll. You can do a lot of stuff with WordPress easily. It brings a lot of functionality out of the box and there are tons of free plugins and free themes which you can use easily and do a lot of complex stuff without writing any line of code.

Writing no code means that you don't have full control about every detail. You have to touch the code here and there to tweak details and get things right. If you write code it is recommended to use a version control system, like [git][git]. No problems so far. But things are getting complex if you want to automate your build and deployment process.

## Automated deployment with WordPress is painful

Most WordPress developers/users are bringing their code changes to production via ftp: save file, commit changes if using version control, drag and drop it on your server and refresh the browser. WordPress updates or plugin updates has to be done manually and twice because of your local setup. All of this is getting weird with version control systems and when you want to automate your deployment.

If you have the luxury of a [continuos deployment][continuous-deployment] at work you feel poor when you are working on your private WordPress projects. It is really smooth just to say git push on your master branch and see the changes after a couple of seconds or minutes on your test/production environment.

I never get up and running a continuos deployment listening to [GitHub][github] or [Bitbucket][bitbucket] repositories of my WordPress projects. It was too complex, hard to achieve and I have no time for that.

### WordPress tends you to work like a “cowboy-programmer”

The facts above are leading somebody to work without version control and pushes to drag and drop files directly via ftp to production. At least this is what happened to me while working with WordPress since a few years.

## Automated deployment with Jekyll and GitHub-Pages is smooth

With Jekyll and [GitHub-Pages][github-pages] automated deployment is a no brainer. Basically you just need to set up a Jekyll project and a repository with a specific name on GitHub. Boom, an automatically deployed blog.

It is very basic, a [MVP][mvp] if you want. No individual theme, no archive pages, no comments and a bunch of other stuff is (maybe) missing which comes out of the box with WordPress. But hey, you got automated deployment. So, extending your blog will be much more fun and you have control on everything. And your workflow is clean, professional and fun.

### Synchronous local and production setup with Jekyll

As mentioned before, there is redundant work for updating WordPress plugins twice, for local and production. But there are also plugin settings which you have to setup or configure twice every time you do some changes.

There are also contents which takes effort to keep everything synchronized between your local and production WordPress installation. By the way, this is the same for all websites or blogs with a database.

Maybe it is a nice to have all contents synched because dummy content is doing the job as well. But then with Jekyll you have something nice, because your website is looking the same on all environments.

## Ruby is more fun then PHP

When we speak about fun and clean, I think the [Ruby][ruby] language is more fun and more clean then PHP. This will be quickly clear when you look at the syntax.

I have also the feeling of a young and dynamic Ruby community. PHP makes me feel like 80’S, old and dusty.

Ruby is also preinstalled on Macs. So it is easier to get started when you are using a mac.

## WordPress is full-blown

WordPress has a lot of features, out of the box. But do you need all of these? All these urls for the same post or page, build-in versioning, commenting functionality which you probably going to replace with a plugin?

### The WordPress plugin jungle

Oh, yes, the plugins. After a while, your WordPress installation becomes a plugin jungle. It is getting harder and harder to manage all plugins from time to time. Your website gets really slow, then you use performance plugins e.g. to cache static pages to speed up your front-end but the WordPress admin area becomes even slower. Not to forgot, you have to update them, locally and on production.

Be careful, Plugins can break your layout or conflict with other plugins. I promise, suddenly you will notice your infinite scroll is no more working properly, your special custom widget is broken or another problem will appear.


## Full control with Jekyll

Knowing what happens under the hood is much easier in a slim system like Jekyll then in a mothership like WordPress. So getting full control on everything is easy as well. And this is good.

Keep your system basic or add features you want to have one by one. Coding features on your own gives you full control about scope, look and behavior. So you can keep things lean and maintainable.

### How I got full control with Jekyll on GitHub-Pages

After setting up a new Jekyll blog I cleaned up the markup, removed every class and id from DOM elements and deleted all the css files. This is a clean base to start working with a clean mind.

## Static vs dynamic

Jekyll is robust and secure. No database, no logins, no backend. Everything on the servers are ready to render files. This is also the reason why it is so fast. If you are a bit techy you will love static websites.

You have to see how you handle contact forms, comment functionality and other things which is coming obviously out of the box with WordPress. But there are a couple of ways to solve this problems.

I am a fan of simplicity. I try to get rid of things which are not really necessary. This helps me to keep things clean and reduce complexity. I never thought about the need of a contact form on my website. It was always a part of the website. But Jekyll made me think of it. At the end I came to the conclusion that I don’t need it necessarily. Zack. One element less on the website.

### Comparing Jekyll and WordPress performance

There are no big differences between Jekyll and WordPress regarding performance when you use page caching. 

Most WordPress plugins update the cache for a page if you publish changes on that page or if the page is affected by new publications. So you will loose some cool things which comes along with dynamic websites. This won’t hurt most of the people. 

E.g. dynamic parts of your WordPress content like “popular posts” will not tell the truth or look different on each page.

## Workflow of writing Blog-posts

WordPress has its own WYSWYG editor where you can type directly your post. As known, WYSWYG editors can interpret your typings some times different and put some additional HTML-tags etc. in your blog post. But you can handle this smoothly with the built-in HTML editor.

Everything happens in your editor when you use Jekyll. You code and write blog posts in your editor. There are two file types for blog posts, Markdown and HTML. I prefer Markdown at the moment. But I would do an experiment when HAML is supported by GitHub-Pages. Currently it is not supported because Jekyll plugins are not allowed.

I use [vim][vim] as my standard editor in my terminal. Mainly for writing code. First I tried to write my posts as well. But then quickly noticed that this is not what I wanted. Then I remembered the beautiful editor [iA Writer][ia-writer] from the [Information Architects][ia]. It supports Markdown and provides a perfect environment for writing blog posts. I really recommend it.

## Conclusion

At the end I think Jekyll is a more techy solution of a blog then WordPress. Some host providers have a 1-click-install option for WordPress and there are tons of WordPress tutorials. By the way, both of the blog engines are well documented.

Not everyone is using Git or version control at all. they just want a website with as low as possible effort. Clean code, version control and a smooth workflow (code wise) have low priority. For those people WordPress is fine. For the rest I would recommend to try out Jekyll.

Anyhow, I think I will still use WordPress here and there. But I am very lucky to have now this Jekyll blog.

Feel free to drop your opinion …

[wp]: https://wordpress.org/ 'WordPress website'
[jekyll]: https://jekyllrb.com/ 'Jekyll website'
[git]: https://git-scm.com/ 'Git website'
[continuous-deployment]: http://www.startuplessonslearned.com/2010/01/case-study-continuous-deployment-makes.html 'Eric Ries post about a continuous deployment case study'
[github]: https://github.com/ 'Github website'
[bitbucket]: https://bitbucket.org/ 'Bitbucket website'
[mvp]: http://www.startuplessonslearned.com/2009/08/minimum-viable-product-guide.html 'Eric Ries post about Minimum Viable Product'
[github-pages]: https://pages.github.com/ 'Github-Pages website'
[ruby]: https://www.ruby-lang.org/ 'Ruby programming language website'
[vim]: http://www.vim.org/about.php 'About Vi Improved'
[ia-writer]: https://ia.net/writer/ 'iA Writer website'
[ia]: https://ia.net/ 'Information Architects website'


