---
layout: post
title: "[git] 心得(1) Submodule, Bitbucket"
date: 2012-02-15 23:32
comments: true
categories: github 
---

# Bitbucker
偶然間發現這個github的競爭者[Bitbucket](http://bitbucket.com)推出了無限免費私有倉庫+無限硬碟空間，
=======
title: "[git] 心得(1) Submodule, Bitbucker"
date: 2012-02-15 23:32
comments: true
categories: git,github 
---

# Bitbucker
偶然間發現這個github的競爭者[Bitbucker](http://bitbucker.com)推出了無限免費私有倉庫+無限硬碟空間，
>>>>>>> origin/master
於是有了一個想法：把不能說得project放到bitbucker，把好玩的open source放在github，兩者透過submodule互通！
畢竟工作上要用到大量的open source project，每次更新都要cp實在很累人。
在大部分專案都在github，而且他的介面也真的很好用的狀況下，在github上開repo還是有必要得！
而且還要能夠隨時跟原作者的repo同步！

# Git submodule
要達成這個目的還是得先了解一下submodule的用法，
以下是學到的事情。

## 本地端起submodule

	cd my_existing_repo
	git add submodule git@github.com:alivedise/lab.git
	git submodule init #啟動submodule
	git submodule update #把submodule內容抓回本地端
	git commit -a -m 'commited with submodule lab added!' #commit submodule的設定回自己的git remote


## 別人更新他的repo時

	git submodule update
	#確認是你想要得內容
	git commit -a -m 'commited with submodule lab updated.' #commit submodule新的版本號回去自己的git remote


## 問題來了，如果別人的repo你自己會作修改該怎麼辦？
我的作法：直接fork回自己的repo，將submodule重新指向自己的repo，自己來維護這份repo。

## 別人跟自己同時都有更新repo時
很簡單，利用add remote->fetch->merge->commit

	cd my_forked_submodule
	git add remote upstream git@github.com:alivedise/lab.git
	git fetch upstream
	git merge origin master


# Reference
* [Git Submodule 介紹與使用](http://blog.wu-boy.com/2011/09/introduction-to-git-submodule/)
* [slideshare](http://www.slideshare.net/littlebtc/git-5528339)
* [Developer Guide: Get the Source Code from GitHub and Keep It Updated](https://github.com/ginatrapani/ThinkUp/wiki/Developer-Guide%3A-Get-the-Source-Code-from-GitHub-and-Keep-It-Updated) 推薦！


