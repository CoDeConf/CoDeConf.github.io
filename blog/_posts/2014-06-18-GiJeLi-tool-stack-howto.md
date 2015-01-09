---
layout: post
title: GiJeLi setup
tags: [Gijeli, Wiki, MarkDown, Ruby]
authors: [Lars kruse]
---

__Jekyll is a Ruby gem that renders [MarkDown](https://help.github.com/articles/github-flavored-markdown) and [Liquid](http://docs.shopify.com/themes/liquid-basics) to static html pages. Jekyll is the stand-alone engine that drives GitHub pages. By installing Jekyll you can effectively have an equivalent to GitHub pages anywhere.__

GiJeLi is a word made up as a contraction of `Gi`t, `Je`kyll and `Li`quid

This post is a description on how to get the tool-stack up and running on your local machine. It's intentionally kept short. For more lecture on the subject you can visit [Jekyll home](http://jekyllrb.com/) or read the into at [Jekyllbootstrap](http://jekyllbootstrap.com/lessons/jekyll-introduction.html).

Provided that you already have git up and running what you need to do is then:

 * Install Ruby & Ruby development kit
 * Install the Jekyll Ruby Gem

__Optional__

 * Python
 * Pygments (for syntax higlightning)
 * Ruby gems kramdown, nokogir, commander

## Setting up Ruby and Jekyll on Windows

See [Jekyll on Windows](http://jekyllrb.com/docs/windows/#installation) for more details.


### Install Ruby with dev-kit
Windows users must install Ruby, if it is not installed already. Unlike Mac OS X, Ruby is not installed by default with the operating system, so most users will have to perform the following steps. Ruby can be easily installed with RubyInstaller. Download and run the latest version of the installer listed on the [RubyInstaller](http://rubyinstaller.org/downloads/) website. 

You will also need to install the latest DevKit, which is also available on the [RubyInstaller downloads page](http://rubyinstaller.org/downloads/).

Once you’ve extracted the DevKit package (i.e. to directory _c:\\rubydevkit_), use the Command Prompt to cd into the directory and run the following commands.

    ruby dk.rb init
    ruby dk.rb install

### Install Jekyll
Finally, install the Jekyll RubyGem with 

    gem install jekyll.
    
If you are behind a proxy, add the option `--http-proxy <porxy-url>` after the install command.

To be able to run _jekyll_ you need to change codepage (to UTF-8) in the command window you are running _jekyll_ from. See [Jekyll Encoding](http://jekyllrb.com/docs/windows/#encoding). In your CLI window, do the command:

    chcp 65001

Then start the _jekyll_ server with the command:

    jekyll serve

There is also a [portable Jekyll for Windows](http://www.madhur.co.in/blog/2013/07/20/buildportablejekyll.html) that might be easy to install.

### Install required RubyGems
The following Gemsn need to be installed (as of time of writing this):

* commander
* nokogiri
* kramdown
* json

Install with the command:

    gem install commander nokogori kramdown json 
 
### Install python
Get python installer from [the Python Website](http://www.pyton.org).

Run the installer and then add the python folder to the PATH in windows.


## Setting up Ruby and Jekyll on Linux

Run the following commands:

### On Ubuntu (13.10)
    sudo apt-get install curl
    curl -sSL https://get.rvm.io | bash -s stable
    source ~/.rvm/scripts/rvm
    rvm requirements
    rvm install ruby
    rvm use ruby --default
    gem install jekyll    
    

### On Fedora (20)
    sudo yum install ruby ruby-devel
    gem install jekyll
    
    
### On Centos 6

Pre-Install stuff

First we need to install the package called Development tools.

    yum groupinstall "Development tools"

Also check if make is installed by «rpm -qi make», if not execute «yum install make».
Start Installing jekyll stuff

Install Ruby & RubyGems

    sudo yum install -y ruby ruby-devel rubygems

Then install jekyll via gem

    sudo gem install jekyll

You will need rdiscount to parse markdown format file

    sudo gem install rdiscount

Install http & json dependency

    sudo gem install http
    sudo gem install json
    
## Setting up Ruby and Jekyll on a Mac OS

```
sudo xcode-select --install
curl -sSL https://get.rvm.io | bash -s stable --ruby
source ~/.rvm/scripts/rvm
rvm requirements
rvm install ruby
rvm use ruby --default
gem install jekyll
```

If you need a few more words to dig into the background read on:

__Xcode CLI tools__ needs to be installed. From the terminal you can run `xcode-select --install` or any command that requires xcode CLI tools e.g `gcc`or `make` and MacOS will simply offer to install the CLI tools.

__Ruby__ for more details read the [install instructions for Ruby](https://www.ruby-lang.org/en/downloads/). If you chose the RVM you can get more details on [rvm.io](http://rvm.io/rvm/install)


## How to run it

Basically you will need to to have a directory with some Jekyll compliant MarkDown in it, you'll most likely get this simply by cloning a git repository from somewhere.

The start the Jekyll web service - which will automatically build the HTML - and browse it:

### Test your setup by running:

    git clone https://github.com/CoDe-U/CoDe-U.github.io.git
    cd cd CoDe-U.github.io/
    jekyll serve

Open your browser on [http://localhost:4000](http://localhost:4000) and you should see the Code:U webpage.

...which you can also see at [www.codeu.eu](http://www.codeu.eu)

Every time you have change the content of the files in directory you'll have to build the HTML again simply by running:

    jekyll build
   
A neat trick it to start the jekyll web service with the `--watch` this will make the service monitor any file changes in the directory and automatically rebuild when required.

Consult the Jekyll documentation for more [tweaks](http://jekyllrb.com/docs/usage/).

## Setting up a web server running GiJeli 

Clone the git repo, cd into it and run the command `jekyll serve`. Now setup a cron job or a Jenkins CI job that periodically runs:

    git pull
    jekyll build
   
...Hmmm - that's it!
 

