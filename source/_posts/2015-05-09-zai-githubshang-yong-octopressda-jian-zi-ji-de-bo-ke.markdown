---
layout: post
title: "在github上用octopress搭建自己的博客"
date: 2015-05-09 15:37:39 *0800
comments: true
keywords: github,octopress,blog,李吉龙
description: create blog in github by octopress
categories: tech Octopress
---
* ##octopress介绍

* ##前提工具
安装git,ruby,ruby-dev等
<!--more-->
* ##搭建过程
 ****
	git clone git://github.com/imathis/octopress.git  octopress    
	cd octopress    
用vim 修改 Gemfile文件的source为 http://ruby.taobao.org   

	bundle install    
	rake install    

  ****   
  申请一个github帐号(如果没有),创建一个名为：username(你的github用户名）.github.io的Repo   
  *注意：创建的名字不能有任何不同*   
  ****    
 开始刷新自己的blog   

	rake setup_github_pages  
	rake new_post["title(blog的题目)"] #创建你想要的文章主题 编辑产生的markdown文件  
	rake generate #编译产生html文件，此处要求有JS环境，如果没有可以使用  
	sudo apt-get install nodejs #如果有忽略此处  
	rake preview #可以在本机的4000端口查看生成情况.  
	rake deploy #将你的博客上传到github pages，用http://username.github.io 查看.  

 ****
####配置自己的博客   
将_config.yml中的title,subtitle,author等修改成自己的信息。
****
####添加社交分享   
octopress 默认带有社交分享功能，如twitter,facebook这些在_config.yml中可以看见。我们可以   
添加QQ，微信，人人等社交工具。当然我们只要使用第三方库即可。如:[jiathis](http://www.jiathis.com)   
1.将social_share: true加入到_config.yml中 *注意冒号后面有空格*   
2.在source/_includes/post/sharing.html中添加:   

	{ %if site.social_share % }   
	{ % include post/social_media.html % }   
	{ % endif % }   

3.访问<http://www.jiathis.com>,复制想要的分享类型的代码，放入新建文件   
source/_includes/post/social_media.html
***   *
####使用SEO   
****   
###添加一个导航页签:如about   

	rake new_page["about"]   
这将生成一个source/about/index.markdown，在这里面输入想要的内容   
编辑 source/_includes/custom/navigation.html,添加  

	<li><a href="/about">作者</a></li>  
****   
####添加侧边栏内容:如About me   
 * 编辑文件source/_includes/custom/asides/about.html   
 * 在_config.yml中，把custom/asides/about.html添加到default_post中，中间逗号隔开   

