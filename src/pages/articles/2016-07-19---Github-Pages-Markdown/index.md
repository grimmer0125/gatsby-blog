---
title: '在GitHub Pages上撰寫Markdown文章的注意事項'
date: "2016-07-19"
layout: post
tags:
- Markdown
---

## 總共有3大種Markdown語法, 以下1~3跟GitHub相關

1. GitHub Flavored Markdown (修改於 kramdown) + fenced code blocks + Syntax Highlight(<-不知那一個套件). *GitHub uses what we're calling "GitHub Flavored Markdown" (GFM) for messages, issues, and comments.*. GFM使用說明:[https://guides.github.com/features/mastering-markdown/](https://guides.github.com/features/mastering-markdown/).
2. GitHub 的線上看到的Readme.md及其Preview，部份的GitHub Flavored Markdown.
3. Github Pages 用的： [kramdown](https://guides.github.com/features/mastering-markdown/) + fenced code blocks and 部份的syntax highlighting of GitHub Flavored Markdown.
4. 第三大種: 其他非 kmarkdown 的 標準Markdown. 大部份網頁版 Markdown , Markdown軟體 或是Atom等Markdown外掛皆為這種. 這三種(1,3,4)皆有大小不等的差異。

## Front Matter
GitHub Page使用的Jekyll有所謂的[Front Matter](https://jekyllrb.com/docs/frontmatter/)，可以在文章裡面加上如下的Yaml設定, 客製化文章一些資料, 比如說 layout, title, tag, date 等. 如果不指定則像是文章名稱會預設用檔名(字首大寫). E.g. 2016-01-01-文章名.md. posts資料夾裡的文章檔名一定要帶有時間，

    ---
    title: "It is a cat."
    ---

    正文開始，最好與上面的Yaml空一行，不然有時排版會亂掉.


## 需要注意的
1. 若要測試寫好的.md/.markdown檔，若要100%確定效果，可以
    1. 在本地端跑 Jekyll
    2. 用 [https://kramdown.herokuapp.com/](https://kramdown.herokuapp.com/) 或是 [http://trykramdown.herokuapp.com/](http://trykramdown.herokuapp.com/) 來測效果，此兩者皆是用Ruby寫的 kramdown.
    3. 使用 Atom的 Package, [https://atom.io/packages/markdown-preview-kramdown](https://atom.io/packages/markdown-preview-kramdown)
3. 換一個段落的方法
     1. 空一行
     2. 第一行結尾留兩個空白

4. inline code block:使用兩個*前導字元*包起來,e.g.

    ```` `test`  ````

5. multiple line code block, 可使用四個空白 或是```(Fenced code blocks)的做法, 參考[https://help.github.com/articles/creating-and-highlighting-code-blocks/](https://help.github.com/articles/creating-and-highlighting-code-blocks/)

6. 語法高亮度的清單(不確定正確): [https://github.com/jneen/rouge/wiki/List-of-supported-languages-and-lexers](https://github.com/jneen/rouge/wiki/List-of-supported-languages-and-lexers), [https://github.com/github/linguist/blob/master/lib/linguist/languages.yml](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml), 有人說別的Blog(e.g. [Hexo](https://hexo.io))所使用的Markdown沒有支持Github用的```jascript這種

7. [https://kramdown.herokuapp.com/](https://kramdown.herokuapp.com/) 沒有支援ES6的語法高亮度.

8. 在 code block or inline code 中打出 ` 符號的方法. [http://stackoverflow.com/questions/33224686/how-to-render-triple-backticks-as-inline-code-block-in-markdown](http://stackoverflow.com/questions/33224686/how-to-render-triple-backticks-as-inline-code-block-in-markdown), *So I've found that using 4 backticks as opening and closing deliminators does the trick:*

## About Fenced code block
1. [Syntax highlighting of GitHub Flavored Markdown ](https://help.github.com/articles/creating-and-highlighting-code-blocks/). It uses ```
2. [Fenced code block of Kramdown](http://kramdown.gettalong.org/syntax.html#fenced-code-blocks). It uses ~~~.

GitHub Pages and some/all markdown files on GitHub can accept these two types and show correctly. But this atom package only handles Kramdown type(~~~). Please keep in mind, and my opinion is to use ~~~. Also They both support non-fenced standard code block (4 indent) and single line code span.  

## List相關:
1. list要視為新的段落，所以要空一行等動作.
2. 多層list(Sub list). 要用四個空格來縮排
3. number後面要加文字才行, 不能直接換行接sub list
4. GitHub page 不支援 code block的 語法高亮度在 list中
5. list裡面有多行code , 一定要用四個空格
6. list裡面包multiple code block, 一定要空一行
