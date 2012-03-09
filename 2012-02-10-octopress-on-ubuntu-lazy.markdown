---
layout: post
title: "[Octopress] 重來懶人包"
date: 2012-02-10 15:36
comments: true
categories: octopress ubuntu 
---

在ubuntu上架設octopress環境的懶人包：

# Git 
略過

# rvm/ruby系列
## 事前準備

	apt-get install libssl-dev
	apt-get install libtool
	sudo apt-get install libyaml-0-2 libyaml-dev

## 開始
bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)
echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm" # Load RVM function' >> ~/.bash_profile
source ~/.bash_profile
rvm pkg install openssl
rvm pkg install iconv
rvm install 1.9.2 -C --with-openssl-dir=$HOME/.rvm/usr,--with-iconv-dir=$HOME/.rvm/usr
rvm rubygems latest
rvm use 1.9.2 --default
rvm reload
gem install bundler

# Octopress
git clone git://github.com/imathis/octopress.git octopress
cd octopress
yes
bundle install
rake setup_github_pages
git@github.com:alivedise/alivedise.github.com.git
git pull

完成！

#讓vim支援octopress語法
##安裝pathogen
(https://github.com/tpope/vim-pathogen)

##安裝vim-octopress
(https://github.com/vim-scripts/vim-octopress)

