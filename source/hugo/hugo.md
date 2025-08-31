# Hugo安装及简单使用

**Hugo的Stack主题博客搭建过程**

hugo版本：0.148.1（扩展板）

时间：2025-08-23

## 安装hugo

1.下载[[hugo_extended_0.148.1_windows-amd64.zip](https://github.com/gohugoio/hugo/releases/download/v0.148.1/hugo_extended_0.148.1_windows-amd64.zip)文件,然后解压到想要安装的位置，安装完成后如下图所示：

2.然后添加环境变量便于随时使用hugo命令

3.然后可以打开cmd，查看hugo版本，验证hugo是否安装成功

```
->hugo version
->hugo v0.148.1-98ba786f2f5dca0866f47ab79f394370bcb77d2f windows/amd64 BuildDate=2025-07-11T12:56:21Z VendorInfo=gohugoio
```

4.先创建一个项目

```
hugo new site myhugo
cd myhugo
```

## 安装Stack主题

1.下载Stack主题

2.解压主题到/myhugo/themes

![image-20250829194016464](https://oss1.3139822.xyz/%E6%96%87%E4%BB%B6-250727/image-20250829194016464.png)

3.复制出示例文件和配置文件到主目录

```
cp themes/hugo-theme-stack/exampleSite/content ./
cp themes/hugo-theme-stack/hugo.yaml ./
mv hugo.toml hugo.toml.bak
```

此时，主目录的文件夹如下图

![image-20250830225658470](https://oss1.3139822.xyz/%E6%96%87%E4%BB%B6-250727/image-20250830225658470.png)

5.创建一个页面

先进入到项目目录，然后使用命令创建一个md文件作为一个页面(一个文件就是一个页面)

```
hugo new content post/2025/2025-08-29hugo博客搭建/index.md
```

所有md文件都在content/post的文件夹下，并且，下面的每个文件夹里面就是一个页面所需的文件，只需要在里面编辑index.md文件就可以了。

创建文件（页面）示例：

```
hugo new content post/2026/2026-08-29hugo博客搭建/index.md
hugo new content post/2027/2027-08-29hugo博客搭建/index.md
```

## hugo.toml配置文件

```toml
baseurl: https://example.com/ # 博客将要部署的域名
languageCode: en-us
theme: hugo-theme-stack # 主题名称（theme文件夹下）
title: Example Site # 自己可以改一下试试
copyright: Example Person # 自己可以改一下试试

# Theme i18n support
# Available values: ar, bn, ca, de, el, en, es, fr, hu, id, it, ja, ko, nl, pt-br, th, uk, zh-cn, zh-hk, zh-tw
DefaultContentLanguage: zh-cn # 默认文章语言，可改为zh-cn

# Set hasCJKLanguage to true if DefaultContentLanguage is in [zh-cn ja ko]
# This will make .Summary and .WordCount behave correctly for CJK languages.
hasCJKLanguage: true # DefaultContentLanguage若为zh-cn，则改为true

languages: # 此配置为页面的语言选项，本人只保留中文，不使用的可以删除
    en:
        languageName: English
        title: Example Site
        weight: 1
        params:
            sidebar:
                subtitle: Example description
    zh-cn:
        languageName: 中文
        title: 演示站点
        weight: 2
        params:
            sidebar:
                subtitle: 演示说明
    ar:
        languageName: عربي
        languagedirection: rtl
        title: موقع تجريبي
        weight: 3
        params:
            sidebar:
                subtitle: وصف تجريبي

services:
    # Change it to your Disqus shortname before using
    disqus:
        shortname: "hugo-theme-stack"
    # GA Tracking ID
    googleAnalytics:
        id:

pagination:
    pagerSize: 3 # 每页最大文章数量，自行更改。

permalinks:
    post: /p/:slug/
    page: /:slug/

params:
    mainSections:
        - post
    featuredImageField: image
    rssFullContent: true
    favicon: # e.g.: favicon placed in `static/favicon.ico` of your site folder, then set this field to `/favicon.ico` (`/` is necessary) # 页面标签页的小图标，位置：static/favicon.ico（主文件夹下的static）

    footer:
        since: 2020
        customText: 自定义文本 # 自己可以改一下试试

    dateFormat: # 文章中的日期显示格式
        published: 2006-01-02 # Jan 02, 2006
        lastUpdated: 2006-01-02 # Jan 02, 2006 15:04 MST

    sidebar: # 侧边栏设置
        emoji: 🍥 # 可自定义更改
        subtitle: Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        avatar:
            enabled: true
            local: true
            src: img/avatar.png # 文件位置 assets/img/avatar.png

    article:
        math: false
        toc: true
        readingTime: true # 阅读时长，false
        license: # 文章协议
            enabled: true
            default: Licensed under CC BY-NC-SA 4.0

    comments: # 评论系统，本人不开通评论系统，将enabled改为false
        enabled: false
        provider: disqus

        disqusjs:
            shortname:
            apiUrl:
            apiKey:
            admin:
            adminLabel:

        utterances:
            repo:
            issueTerm: pathname
            label:

        beaudar:
            repo:
            issueTerm: pathname
            label:
            theme:

        remark42:
            host:
            site:
            locale:

        vssue:
            platform:
            owner:
            repo:
            clientId:
            clientSecret:
            autoCreateIssue: false

        # Waline client configuration see: https://waline.js.org/en/reference/component.html
        waline:
            serverURL:
            lang:
            pageview:
            emoji:
                - https://unpkg.com/@waline/emojis@1.0.1/weibo
            requiredMeta:
                - name
                - email
                - url
            locale:
                admin: Admin
                placeholder:

        twikoo:
            envId:
            region:
            path:
            lang:

        # See https://cactus.chat/docs/reference/web-client/#configuration for description of the various options
        cactus:
            defaultHomeserverUrl: "https://matrix.cactus.chat:8448"
            serverName: "cactus.chat"
            siteName: "" # You must insert a unique identifier here matching the one you registered (See https://cactus.chat/docs/getting-started/quick-start/#register-your-site)

        giscus:
            repo:
            repoID:
            category:
            categoryID:
            mapping:
            lightTheme:
            darkTheme:
            reactionsEnabled: 1
            emitMetadata: 0

        gitalk:
            owner:
            admin:
            repo:
            clientID:
            clientSecret:
            proxy:

        cusdis:
            host:
            id:
    widgets:
        homepage:
            - type: search
            - type: archives
              params:
                  limit: 5
            - type: categories
              params:
                  limit: 10
            - type: tag-cloud
              params:
                  limit: 10
        page:
            - type: toc

    opengraph:
        twitter:
            # Your Twitter username
            site:

            # Available values: summary, summary_large_image
            card: summary_large_image

    defaultImage:
        opengraph:
            enabled: false
            local: false
            src:

    colorScheme:
        # Display toggle
        toggle: true

        # Available values: auto, light, dark
        default: auto

    imageProcessing:
        cover:
            enabled: true
        content:
            enabled: true

### Custom menu
### See https://stack.jimmycai.com/config/menu
### To remove about, archive and search page menu item, remove `menu` field from their FrontMatter
menu:
    main: []

    social: # 侧边栏社交配置
        - identifier: github
          name: GitHub
          url: https://github.com/CaiJimmy/hugo-theme-stack
          params:
              icon: brand-github # 推荐icon：https://tabler.io/icons

        - identifier: twitter
          name: Twitter
          url: https://twitter.com
          params:
              icon: brand-twitter

related:
    includeNewer: true
    threshold: 60
    toLower: false
    indices:
        - name: tags
          weight: 100

        - name: categories
          weight: 200

markup:
    goldmark:
        extensions:
            passthrough:
                enable: true
                delimiters:
                    block:
                        - - \[
                          - \]
                        - - $$
                          - $$
                    inline:
                        - - \(
                          - \)
        renderer:
            ## Set to true if you have HTML content inside Markdown
            unsafe: true
    tableOfContents:
        endLevel: 4
        ordered: true
        startLevel: 2
    highlight:
        noClasses: false
        codeFences: true
        guessSyntax: true
        lineNoStart: 1
        lineNos: true
        lineNumbersInTable: true
        tabWidth: 4

```















