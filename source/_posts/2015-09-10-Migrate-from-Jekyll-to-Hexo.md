title: 从 Jekyll 迁移到 Hexo
date: 2015-09-10 10:47:11
categories: hexo
tags: [jekyll,hexo]
---

![image](http://7xlh4f.com1.z0.glb.clouddn.com/1.png)

# 安装 Hexo

```
$ npm install hexo-cli -g
$ hexo init blog
$ cd blog
$ npm install
$ cp <md-files> source/_post
$ hexo server #preview on http://0.0.0.0:4000/
$ hexo s --debug # s short for server 
```

# 安装NexT主题
[Docs](http://theme-next.iissnan.com/)

```
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```

<!--more-->

# 修改站点 _config.yml
`_config.yml`

```
# Hexo Configuration
## Docs: http://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: 不毛次元
subtitle:
description:
author: bumaociyuan
language: zh-Hans #设置语言
timezone: America/New_York #设置时区 坑0

since: 2013 #添加 Blog 开始时间

feed: #添加 rss 需要使用 hexo-generator-feed 插件
  type: atom
  path: resources/testRss.xml
  limit: 0

getclicky_analytics: <clicky-id> #NexT 主题不支持，需要手动添加


avatar: <avatar-url>

disqus_shortname: <disqus-shortname> #添加 disqus

swiftype_key: <swiftype-key> #添加 swiftype

social: #添加 social infos
  GitHub: https://github.com/bumaociyuan
  Twitter: https://twitter.com/bumaociyuan

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://bumaociyuan.github.io
root: /
permalink: :category/:year/:month/:day/:title.html #从 jekyll 迁移，保持 url 不变
permalink_defaults:

# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :year-:month-:day-:title.md #从 jekyll 迁移，不需要修改 md 文件名
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: true
  tab_replace:

# Category & Tag
default_category: "" #设置默认 category 为空，不会显示在 url 上
category_map:
tag_map:

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

index_generator:
  per_page: 10

archive_generator: #区别 archive 的分页数量，需要安装 hexo-generator-archive
  per_page: 500 
  yearly: true
  monthly: true

tag_generator:
  per_page: 500

# Extensions
## Plugins: http://hexo.io/plugins/
## Themes: http://hexo.io/themes/
theme: next

# Deployment
## Docs: http://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: git@github.com:bumaociyuan/bumaociyuan.github.io.git
  branch: master
```

#修改模版，生成 Tags 和 About 等

## 修改模版 
`scaffolds/post.md`

```
title: {{ title }}
date: {{ date }}
categories: 
tags:
---
```

## 生成 pages
```
$ hexo new page "tags"
$ hexo new page "categories"
```

`source/tags/index.md`
```
title: Tagcloud
date: 2015-09-08 14:26:37
type: "tags"
comments: false
---
```

`source/categories/index.md`
```
title: categories
date: 2015-09-08 14:31:18
type: "categories"
comments: false
---
```

## 修改主题 _config.yml

```
menu:
  home: /
  archives: /archives
  categories: /categories
  tags: /tags
  # about: /about
  # commonweal: /404.html

highlight_theme: night
```

## 添加 404 页面
todo
---

# 三方服务

## Clicky Analytics

新增文件 `themes/next/layout/_scripts/analyticsgetclicky-analytics.swig`

```
<script type="text/javascript">
var clicky_site_ids = clicky_site_ids || [];
clicky_site_ids.push({{ theme.getclicky_analytics }});
(function() {
  var s = document.createElement('script');
  s.type = 'text/javascript';
  s.async = true;
  s.src = '//static.getclicky.com/js';
  ( document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0] ).appendChild( s );
})();
</script>
<noscript><p><img alt="Clicky" width="1" height="1" src="//in.getclicky.com/{{ theme.getclicky_analytics }}ns.gif" /></p></noscript>
```

编辑 `themes/next/layout/_scripts/analytics.swig`

```
 {% include 'analytics/google-analytics.swig' %}
 {% include 'analytics/baidu-analytics.swig' %}
+{% include 'analytics/getclicky-analytics.swig' %} ＃add this line
```

# Deployment
直接使用 hexo-deployer-git 发布会出现覆盖commit 的问题
源码如下 `node_modules/hexo-deployer-git/lib/deployer.js`

```js
  function setup(){
    // Create a placeholder for the first commit
    return fs.writeFile(pathFn.join(deployDir, 'placeholder'), '').then(function(){
      return git('init');
    }).then(function(){
      return git('add', '-A');
    }).then(function(){
      return git('commit', '-m', 'First commit');
    });
  }

  function push(repo){
    return git('add', '-A').then(function(){
      return git('commit', '-m', message).catch(function(){
        // Do nothing. It's OK if nothing to commit.
      });
    }).then(function(){
      return git('push', '-u', repo.url, 'master:' + repo.branch, '--force'); //--force 会清除 github 上的历史commit 所以hexo
    });
  }

```

 解决办法
 
 ```
 $ rm -rf .deploy_git
 $ copy -rf <bumaociyuan.github.io-path> .deploy_git
 ```