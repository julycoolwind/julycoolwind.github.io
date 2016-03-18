---
layout: post
title:  "jekyll的尝试过程"
categories: jekyll
---

* content
{:toc}   

## jekyll过程

### 第一坑   
使用jekyll第一个坑，安装gem的时候虽然本机开了一个全局代理，但是依然不能成功。最后只有使用淘宝的镜像源才算是安装成功。   

### 第二坑
安装成功之后有碰到启动失败的问题。一直报：   
     
     /Users/apple/.rvm/gems/ruby-2.0.0-p451/gems/listen-3.0.0/lib/listen/event/queue.rb:15: warning: toplevel constant Queue referenced by Thread::Queue
    /Users/apple/.rvm/gems/ruby-2.0.0-p451/gems/listen-3.0.0/lib/listen/event/loop.rb:15: warning: toplevel constant Queue referenced by Thread::Queue
    /Users/apple/.rvm/gems/ruby-2.0.0-p451/gems/listen-3.0.0/lib/listen/event/loop.rb:37: warning: toplevel constant Queue referenced by Thread::Queue
     jekyll 3.1.2 | Error:  uninitialized constant Listen::Event::Loop::Timeout   

最终通过比对**_config.yml**文件发现，添加如下的配置之后可以正常启动。
    
    gems:
        - jekyll-gist

问题解决，具体的原因等以后慢慢查明。