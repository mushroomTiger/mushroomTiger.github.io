## 简介

GitHub Pages 是 GitHub 提供的免费静态网站托管服务，无需自建服务器，即可轻松展示开源项目、搭建个人博客或在线简历。本文以 Chirpy 模板为例，完整介绍从零开始构建个人网站的全流程，包括环境配置、本地调试、个性化定制与最终发布。

## 模板

受相关文章启发，作者也觉得Jekyll Themes中的[Chirpy](https://jekyllthemes.org)模板风格很不错，决定尝试使用。

> 参考文章：[春枫禾旭：【避坑篇】使用Github Pages搭建个人主页or博客网站【上】](https://zhuanlan.zhihu.com/p/xxx)
>
> [【快速部署+客制化】Github Pages+Jekyll Chirpy 速搭个人主页 - 知乎](https://zhuanlan.zhihu.com/p/695291923)

## 环境配置（系统+编译器）

作者使用Windows 10专业版 + WebStorm。

## 具体操作

### 1. 安装Ruby & Jekyll

参考官方文档：[Jekyll on Windows](https://jekyllrb.com/docs/installation/windows/)

- 下载最新版WITH DEVKIT的Ruby：[RubyInstaller Downloads](https://rubyinstaller.org/downloads/)(安装目录全英文)

- 安装完毕后，安装器会自动启动命令窗口，提示安装 MSYS2，输入 1 2 3 然后按回车开始安装所有组件（MSYS2 and MINGW development tool chain）

  ```bash
  # 检查Ruby版本
  ruby --version
  # 要求：Ruby >= 3.1
   
  # 检查Gem版本
  gem --version
   
  # 检查Bundler版本
  bundle --version
  ```

- 安装完Ruby后，打开新的cmd，安装Jekyll：

  ```
  gem install jekyll bundler
  ```

### 2. 配置Github

打开模板仓库：[cotes2020/chirpy-starter](https://github.com/cotes2020/chirpy-starter)。选择 `Use this template` > `Create a new repository` 命名新仓库名称为 `USERNAME.github.io`，这里面USERNAME是你的Github的用户名。在仓库中点击右上角设置后，找到pages设置，将Source修改为Github Action。这时如果修改仓库中 `_config.yml` 文件的第26行的url，改为自己的 `https://USERNAME.github.io`，随后打开浏览器进入 `USERNAME.github.io` 就能查看到基础的网站了。

### 3. 本地部署

本地部署时需要从Github上克隆出创建的仓库。使用WebStorm，打开克隆的仓库的根目录，打开根目录的Gemfile，更换清华源后打开终端，安装依赖。

```bash
# 更换清华源
source "https://gems.ruby-china.com"

# 安装依赖
bundle install
```

### 4. 本地调试

使用WebStorm，在仓库的根目录，打开终端，执行下面命令。

```bash
# 本地预览
bundle exec jekyll serve
```

访问 `http://localhost:4000` 即可查看本地预览效果。

### 5. 基础设置

_config.yml 主要配置项

```yaml
# 基础配置
title: "你的博客标题"
tagline: "博客副标题"
description: "博客描述，用于SEO"
url: "https://你的用户名.github.io"  # GitHub Pages地址
baseurl: "/仓库名"  # 如果使用项目页面

# 作者信息
social:
  name: "你的姓名"
  email: "你的邮箱@example.com"
  links:
    - "https://github.com/你的用户名"
    - "https://twitter.com/你的用户名"

# 主题设置
theme: jekyll-theme-chirpy
lang: zh-CN  # 设置中文界面
timezone: Asia/Shanghai  # 时区设置

# 功能开关
toc: true  # 启用文章目录
comments:
  provider: giscus  # 评论系统选择
```

其他细节等可以根据需要进行配置。

### 6. 个性化网站

参考官方文档：[Customize the Favicon](https://chirpy.cotes.page/posts/customize-the-favicon/)。打开网站[Favicon Generator](https://realfavicongenerator.net)，上传自己的图片Select your Favicon image，然后可以进行一些自己的选择，最后在网站的最下面生成文件，Generate your Favicons and HTML code。将下载的压缩包，解压后，在文件夹内删除 `browserconfig.xml` 和 `site.webmanifest`。打开编译器，把文件内剩余所以文件，移动到 `assets/img/favicons` 中（在assets中自己创建）。

### 7. 编写博客

发布博客只能发布markdown文件，把md文件存放在仓库根目录的 `_posts` 中即可。文件的名字必须遵守 `YYYY-MM-DD-TITLE`，扩展名为 `md` 或 `markdown`。

#### Markdown的YAML文件配置

```yaml
---
title: 文章标题
date: 2023-10-10 12:00:00 +0800  # 时间，最后为时区北京 +0800
categories: [主分类, 子分类]  # 上级文档，下级文档
tags: [标签1, 标签2]  # TAG
math: true  # 启用数学公式
---
```

#### 数学公式支持

数学公式默认是关闭的，需要在YAML文件内加入：

```yaml
math: true
```

其他更加细节的设置，请参考官方文档：[Writing a New Post](https://chirpy.cotes.page/posts/write-a-new-post/)

### 8. Github Action 发布

当你已经使用Github上传了仓库文件之后，发现网站并没有更新，可以选择手动发布。在仓库的Action中找到 `Build and Deploy` 中按下 `Run workflow` 就可以手动发布了。

---

> 本文基于Chirpy模板和Github Pages搭建，适用于快速构建个人博客或项目主页。通过以上完整的8个步骤，您可以顺利完成从环境配置到网站发布的整个过程。
