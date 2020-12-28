# hexo-generator-search-cst

[![npm](https://img.shields.io/npm/v/hexo-generator-search.svg)](https://www.npmjs.com/package/hexo-generator-search)
[![npm](https://img.shields.io/npm/dm/hexo-generator-search.svg)](https://www.npmjs.com/package/hexo-generator-search)

Generate search data for Hexo 3.0. This plugin is used for generating a search index file, which contains all the neccessary data of your articles that you can use to write a local search engine for your blog. Supports both XML and JSON format output.

- [Demo](http://www.hahack.com/hexo-theme-freemind-blog/) - try out the search engine in this site.
- [Demo JSON output](https://github.com/PaicHyperionDev/hexo-generator-search/blob/master/demo_output/search.json)
- [Demo XML output](https://github.com/PaicHyperionDev/hexo-generator-search/blob/master/demo_output/search.xml)


# 重要说明

由于`nunjucks`模板引擎不兼容emberjs的`{{}}`标签，所以修改了`nunjucks`模板引擎的标签占位符。

| nunjucks默认占位符 | 修改后的占位符 |
| ---------------- | ------------- |
|       `{{`        |      `{$`      |
|        `}}`        |     `$}`      |
|        `{#`        |      `{@`     |
|        `#}`        |      `@}`     |


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
$ npm install hexo-generator-search-cst --save
```

## Options

You can configure this plugin in your root `_config.yml`.

``` yaml
search:
  path: search.xml
  field: post
```

- **path** - file path. By default is `search.xml` . If the file extension is `.json`, the output format will be JSON. Otherwise XML format file will be exported.
- **field** - the search scope you want to search, you can chose:
  * **post** (Default) - will only covers all the posts of your blog.
  * **page** - will only covers all the pages of your blog.
  * **all** - will covers all the posts and pages of your blog.

## FAQ

### What's this plugin supposed to do? 

This plugin is used for generating a xml / json file from your Hexo blog that provides data for searching.

### Where's this file saved to?

After executing `hexo g` you will get the generated result at your public folder.

### How to use this plugin in my Hexo blog?

You have two choices:

* you don't want to write search engine by yourself. There are many themes that take use this plugin for local searching that works out of box. 
* you are familiar with Ajax and jQuery and would like to write your own search engine. You can implement one by yourself according to the example theme I give. Read the [source code](https://github.com/wzpan/hexo-theme-freemind) of this theme. Generally there are 3 steps:
  1. write a [search view](https://github.com/wzpan/hexo-theme-freemind/blob/master/layout/_widget/search.ejs#L8). This is the place for displaying a search form and search results ;
  2. write a [search script](https://github.com/wzpan/hexo-theme-freemind/blob/master/source/js/search.js). This script tells the browser how to grab search data and filter out contents what we're searching;
  3. tell hexo to [connect the above two part](https://github.com/wzpan/hexo-theme-freemind/blob/master/layout/_partial/after_footer.ejs#L22).
