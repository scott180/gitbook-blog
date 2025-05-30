# git平台docsify布署markdown文件

<br />

`网址` &ensp; [blog]( https://scott180.github.io/reco-blog ) &ensp; [blog]( https://github.com/scott180/docsify-blog )

## 本地安装

```js
docsify 可以快速帮你生成文档网站。不同于GitBook、Hexo的地方是它不会生成静态的 .html 文件，所有转换工作都是在运行时。

// 首先安装node
https://gitlab.com/xuyq123/mynotes/-/blob/master/%E8%B5%84%E6%96%99/nodejs%E4%B8%8Enpm%E7%AC%94%E8%AE%B0.md

// 安装docsify
npm i docsify-cli -g   

docsify --version

// 初始化docsify项目
docsify init ./test

// 运行
docsify serve docs

http://localhost:3000
 
教程
https://docsify.js.org/#/zh-cn/quickstart
https://www.jianshu.com/p/4883e95aa903
https://marked.js.org/demo/


修改主题
index.html  
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/vue.css">
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/buble.css">
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/dark.css">
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/pure.css">
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify/themes/dolphin.css">


```


```html
给每个页面的末尾加上 footer
window.$docsify = {
  plugins: [
    function(hook) {
      var footer = [
        '<hr/>',
        '<footer>',
        '<span><a href="https://github.com/QingWei-Li">cinwell</a> &copy;2017.</span>',
        '<span>Proudly published with <a href="https://github.com/docsifyjs/docsify" target="_blank">docsify</a>.</span>',
        '</footer>'
      ].join('');

      hook.afterEach(function(html) {
        return html + footer;
      });
    }
  ]
};

```

```java
cdn 连不上或者网速较慢
  <link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/lib/themes/vue.css">
  <script src="//cdn.jsdelivr.net/npm/docsify@4"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>

  可换成本地加载文件
  <link rel="stylesheet" href="docsify/vue.css">
  <script src="docsify/docsify.js"></script>
  <script src="docsify/search.min.js"></script>

  或其他cdn
  https://cdnjs.com/libraries/docsify    https://cdnjs.cloudflare.com/ajax/libs/docsify/4.12.2/docsify.min.js
  https://www.bootcdn.cn                 https://cdn.bootcdn.net/ajax/libs/docsify/4.12.2/docsify.js
  
```

---

## gitlab布署docsify

```c
1、创建 .gitlab-ci.yml
2、创建docs目录，将markdown文件放在此处。推送文件。
3、推送文件。

可参考此项目  
https://gitlab.com/xuyq123/plain-docsify   
https://xuyq123.gitlab.io/plain-docsify 

多级页面可参考  
https://gitlab.com/xuyq123/myblog-docsify   
https://xuyq123.gitlab.io/myblog-docsify 

```


> .gitlab-ci.yml

```sh
image: ruby:alpine

stages:
- deploy

pages:
  stage: deploy
  script:
  - cp -r docs/. public
  - echo "deploying to pages for note"
  environment:
    name: note
    url: https://xuyq123.gitlab.io/plain-docsify
  artifacts:
    paths:
    - public
  only:
  - master

```

---

## github布署docsify

```js
1、本地生成 docsify项目

// 初始化docsify项目
docsify init ./test

// 运行
docsify serve docs

2、推送文件。

3、开启github pages 
位置：Setting - GitHub Pages - Save  
选择对应目录。

后期更新文件，只需推送即可。

可参考此项目 
https://github.com/scott180/myblog-docsify/   
https://scott180.github.io/myblog-docsify/

```

---

## gitee布署docsify

```
在对应的 Gitee 仓库服务中选择 Gitee Pages，选择您要部署的分支，填写您要部署的分支上的目录，
例如docs，填写完成之后点击启动即可。
```

---

## 示例

| 名称       | 仓库                                                			        |  备注            |
| ---------  | -------------------------------------------------------------        |  ----------      |
| plain-docsify    | gitlab [plain-docsify]( https://gitlab.com/xuyq123/plain-docsify )&ensp; [**网页**](  https://xuyq123.gitlab.io/plain-docsify/ ) <br/>github [plain-docsify]( https://github.com/scott180/plain-docsify )&ensp; [网页](  https://scott180.github.io/plain-docsify/ ) |  笔记docsify                        |
| myblog-docsify   | gitlab [myblog-docsify]( https://gitlab.com/xuyq123/myblog-docsify )&ensp; [**网页**](  https://xuyq123.gitlab.io/myblog-docsify/ ) <br/>github [docsify-blog]( https://github.com/scott180/myblog-docsify )&ensp; [网页](  https://scott180.github.io/docsify-blog ) |  笔记与博客docsify                  |

