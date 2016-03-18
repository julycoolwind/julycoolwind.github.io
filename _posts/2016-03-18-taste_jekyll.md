---
layout: post
title:  "jekyll的尝试过程"
categories: jekyll
---

* content
{:toc}   

## jekyll过程

### 第一个障碍   
使用jekyll第一个坑，安装gem的时候虽然本机开了一个全局代理，但是依然不能成功。最后只有使用淘宝的镜像源才算是安装成功。   

### 第二个障碍
安装成功之后有碰到启动失败的问题。一直报：   
     
     /Users/apple/.rvm/gems/ruby-2.0.0-p451/gems/listen-3.0.0/lib/listen/event/queue.rb:15: warning: toplevel constant Queue referenced by Thread::Queue
    /Users/apple/.rvm/gems/ruby-2.0.0-p451/gems/listen-3.0.0/lib/listen/event/loop.rb:15: warning: toplevel constant Queue referenced by Thread::Queue
    /Users/apple/.rvm/gems/ruby-2.0.0-p451/gems/listen-3.0.0/lib/listen/event/loop.rb:37: warning: toplevel constant Queue referenced by Thread::Queue
     jekyll 3.1.2 | Error:  uninitialized constant Listen::Event::Loop::Timeout   
     
最终通过比对**_config.yml**文件发现，添加如下的配置之后可以正常启动。
    
    gems:
        - jekyll-gist

问题解决，具体的原因等以后慢慢查明。

### 第三个障碍   
下载了[HyG](https://github.com/Gaohaoyang/gaohaoyang.github.io)的模板，感谢作者。但是在使用的过程中发现，我自己在```_posts```目录下添加的文件在build之后，不会生成到```_sites```目录下。模板中原来的文件都可以，就是我心添加的不可以。很奇怪。进过仔细比对，没有发现什么异常。最后发现将文件名修改之后，例如```2015-02-16-sope.md```这样的文件名，修改该为2016但是生成的目录还是2015。发现文件头还有一行```date: 2015-02-16 14:34:05```尝试删除这一行，瞎猫碰到死耗子。问题解决了，具体的原因之后后边慢慢在查了。