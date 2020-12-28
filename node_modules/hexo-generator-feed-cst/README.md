# hexo-generator-feed-cst

[![Build Status](https://travis-ci.org/hexojs/hexo-generator-feed.svg?branch=master)](https://travis-ci.org/hexojs/hexo-generator-feed)  [![NPM version](https://badge.fury.io/js/hexo-generator-feed.svg)](http://badge.fury.io/js/hexo-generator-feed) [![Coverage Status](https://img.shields.io/coveralls/hexojs/hexo-generator-feed.svg)](https://coveralls.io/r/hexojs/hexo-generator-feed?branch=master)

Generate Atom 1.0 or RSS 2.0 feed.

# 重要说明

由于`nunjucks`模板引擎不兼容emberjs的`{{}}`标签，所以修改了`nunjucks`模板引擎的标签占位符。

| nunjucks默认占位符 | 修改后的占位符 |
| ---------------- | ------------- |
|       `{{`       |      `{$`      |
|        `}}`      |     `$}`      |
|        `{#`      |      `{@`     |
|        `#}`      |      `@}`     |


修改后使用`nunjucks`模板引擎解析的hexo插件会解析失败，所以需要同步修改依赖`nunjucks`模板引擎的hexo插件。

之所以这么做是因为[hexo](http://hexo.io)使用`nunjucks`解析生成静态HTML。然后我的主站[xcoding](http://xcoding.tech)使用了GitHub+hexo搭建。然后博客主要用于记录[EmberJS](http://emberjs.com)相关文章，EmberJS很多标签都是使用`{{}}`，与模板引擎的占位符冲突。

冲突出现的问题如下：
```js
http://hexo.io/docs/troubleshooting.html
Template render error: (unknown path) [Line 37, Column 81]
  expected variable end


Unhandled rejection Template render error: (unknown path) [Line 10, Column 95]
  unexpected token: #
```

当然也有其他解决方案，但是自定义模板占位符是比较好的方法，详细可以看如下博客：
[如何从根本解决hexo不兼容{{}}标签问题](http://xcoding.tech/2018/08/08/hexo/%E5%A6%82%E4%BD%95%E4%BB%8E%E6%A0%B9%E6%9C%AC%E8%A7%A3%E5%86%B3hexo%E4%B8%8D%E5%85%BC%E5%AE%B9%7B%7B%7D%7D%E6%A0%87%E7%AD%BE%E9%97%AE%E9%A2%98/)

## Install

``` bash
$ npm install hexo-generator-feed-cst --save
```

- Hexo 3: 1.x
- Hexo 2: 0.x

## Use

In the [front-matter](https://hexo.io/docs/front-matter.html) of your post, you can optionally add a `description`, `intro` or `excerpt` setting to write a summary for the post. Otherwise the summary will default to the excerpt or the first 140 characters of the post.

## Options

You can configure this plugin in `_config.yml`.

``` yaml
feed:
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
```

- **type** - Feed type. (atom/rss2)
- **path** - Feed path. (Default: atom.xml/rss2.xml)
- **limit** - Maximum number of posts in the feed (Use `0` or `false` to show all posts)
- **hub** - URL of the PubSubHubbub hubs (Leave it empty if you don't use it)
- **content** - (optional) set to 'true' to include the contents of the entire post in the feed.
- **content_limit** - (optional) Default length of post content used in summary. Only used, if **content** setting is false and no custom post description present.
- **content_limit_delim** - (optional) If **content_limit** is used to shorten post contents, only cut at the last occurrence of this delimiter before reaching the character limit. Not used by default.
