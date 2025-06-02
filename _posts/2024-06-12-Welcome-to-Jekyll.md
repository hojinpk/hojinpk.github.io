---
layout: single
title: "Welcome to Jekyll!"
categories: coding
tag: [python, blog, jekyll]
author_profile: false
sidebar:
    nav: "docs"
---
**[Notice]** [Open my personal blog in GitHub](https://hojinpk.github.io/)
{: .notice--primary}
# My Nest
I have decided to use GitHub Pages as my first blog from now on because it supports markdown grammar basically. The following video clip is for a sort of hello world that a newbie is looking for when they start to learn something; [https://www.youtube.com/watch?v=ACzFIAOsfpM](https://www.youtube.com/watch?v=ACzFIAOsfpM)

`minimal-mistakes` that I have chose in [https://github.com/topics/jekyll-theme](https://github.com/topics/jekyll-theme) is my theme of the blog. As for the basic grammar of Jekyll, you can refer to the web site [https://jekyllrb.com/docs/posts/](https://jekyllrb.com/docs/posts/)
## Local Hosting Blog
Whenever there is changes in the blog, we can see the latest one after submitting changes in local to master in the public GitHub repository. It's tedious job for me at least. There is an alternative way to check it by installing Jekyll and its bundlers. 

```bat
gem install jekyll
gem install bundler
cd \hojinpk.github.io\
bundle install
bundle exec jekyll serve
```
Refer to [https://jekyllrb.com/docs/](https://jekyllrb.com/docs/) or [https://www.youtube.com/watch?v=0TeHUqSAb6Q](https://www.youtube.com/watch?v=0TeHUqSAb6Q) for  details.
## Troubleshooting
I came across an error message whenever Jekyll server restarts and the installation environment is Windows 11, Ruby devkit-3.3.2-1-x64. 

```bat
C:\hojinpk.github.io>bundle exec jekyll serve --trace --verbose

[!] There was an error while loading `minimal-mistakes-jekyll.gemspec`: No such file or directory @ rb_sysopen - package.json. Bundler cannot continue.

 #  from C:/Work/hojinpk.github.io/_site/minimal-mistakes-jekyll.gemspec:3
 #  -------------------------------------------
 #    spec.add_development_dependency "rake", ">= 12.3.3"
 >  end
 #  require "json"
 #  -------------------------------------------

C:\hojinpk.github.io>ridk enable
```

In that case, follow the the instructions.
- Change `gemspec` to `gemspecs` in Gemfile
- Add `gem "minimal-mistakes-jekyll"` in Gemfile
- Execute `bundle` in command window
- Execute `bundle exec jekyll serve`
