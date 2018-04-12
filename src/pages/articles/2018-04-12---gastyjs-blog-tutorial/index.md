---
title: 'How to write a Gatsby based blog'
date: "2018-04-12"
draft: false
layout: post
tags:
- blog
---

Gatsby 是 React + GraphQL based的網站/blog生成器. 可以用 React方式修改UI.  

### 參考:

1. https://www.gatsbyjs.org/tutorial/, 建議 `tutorial`看完, 走完就有一個可以寫Markdown file的blog,  但沒什麼UI, `/doc`部份需要時再看
2. https://github.com/alxshelepenok/gatsby-starter-lumen
3. https://github.com/grimmer0125/gatsby-blog, 目前使用的的, 修改自lumen. 改的:

    1. 增加留言功能: `disqusShortname: 'grimmer'`
    2. 修改readme.md, package.json
    3. side menu 修改部份項目 (可查我的 commit log)
    3. add favicon. (使用 `gatsby-plugin-favicon`, 在`gatsby-config.js`裡設定)
    4. 刪掉default的文章 (在src/pages/articles裡)
    4. comment catalog頁面的UI以防止若文章無Catalog資訊時會exception
    5. 其它
4. [非必要]也可以學習一下 [GraphQL](https://graphql.org/learn/)


###  Gatsby Notes:

1. 跟一般React不一樣, 進入點非index.html, Gatsby則是 `layouts/index.jsx` 跟 `pages/index.jsx`, 參考 [https://www.gatsbyjs.org/tutorial/part-three/#our-first-layout-component](https://www.gatsbyjs.org/tutorial/part-three/#our-first-layout-component), Gatsby使用了 [`react-router`](https://github.com/ReactTraining/react-router)
2. Gatsby建議global style是用[typography](https://www.gatsbyjs.org/tutorial/part-two/#typographyjs), 它也可以搭其他的 css modules.  
3. Markdown的部份的流程是, `gatsby develop` 會使用到 `gatsby-node.js`, 而在其中可以設定讓它使用gatsby的外掛把 Markdown files的資料轉成 GraphQL query data source (也可在`gatsby-node.js`插入一些資料). 而進而使用 `React High order component`的方式把資料傳到 `page-template.jsx`的React元件的props. 參考 [https://www.gatsbyjs.org/tutorial/part-six/](https://www.gatsbyjs.org/tutorial/part-six/).
4. 一般在React裡使用GraphQL會看到如 https://github.com/apollographql/react-apollo 的 `export default graphql(gql` query content`)(TodoApp);` 這樣的`high order component`設定, 但`Gatsby`則省略了 `)(TodoApp);`, `gatsby develop` 會自動在runtime時補上.
5. `Gatsby`是使用到Webpack, 故改完文章頁面會自動更新.
6. `Gatsby` local dev時, 有起一個 GraphQL server, 故可使用 `GraphiQL` 去測試 每個頁面使用到 GraphQL query部份. ref:  https://www.gatsbyjs.org/tutorial/part-five/#introducing-graphiql,
7. deploy時則會先把 GraphQL的資料 bundle到static site裡, 無 GraphQL server.

### Prepare Steps:

1. clone https://github.com/grimmer0125/gatsby-blog 或是 照 https://github.com/alxshelepenok/gatsby-starter-lumen#getting-started 輸入 `gatsby new lumen https://github.com/alxshelepenok/gatsby-starter-lumen`
2. `npm install`

### 寫文章Steps:

1. 在 `pages/articles/` 下新增新文章的folder. folder檔名需要是`日期---folderName`, 無`---`的話 `gatsby-node.js`會parse exception.
2. 新增 markdown 語法的blog文章檔案. 及其會用到的assets在同一個folder.
3. Markdown文章需包含以下等 `Metadata`, title, date, layout. tags 則不確定, 待check,
4. 至少要有一篇文章要有 category, description(不確定,待check), draft 這些 `Metadata`. e.g. `category: "Objective-C"`, `description: ""description`, `draft: false`. 不然會 parse exception.

### Todo:
1. Fix Catagories頁面跟相關bugs.
2. 增進寫文章的rule, e.g. 拿掉上面的 `4.`及改善`3`, 有些可自動判斷.

### Local Dev Run:

1. `gatsby develop`

### Deploy 到 Netlify設定 (參考lumen):

1. 在GitHub上建一個repo.
2. https://app.netlify.com/start/deploy?repository=https://github.com/你的帳號/repoName
3. 可在Netlify更改預設的domain name.

### Deploy:

1. push到GitHub就好. 可至Netlify看deploy進度.
2. [注意] [Netlify](https://www.netlify.com/) 對檔名有較嚴格限制,  有時local Run是沒問題的.
