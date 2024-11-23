---
title: ✨五分钟从零搭建自己的图床
date: 2024-07-07 16:35
tags: 
- PicX
- 洛谷
- Github
- 图床
- 教程
- 视频教程
comments: true
categories: 科技·工程
Katex: false
mathjax: true
---

### 前言
在洛谷，拥有洛谷图床。但是，洛谷图床有些时候对用户名颜色、文件大小等有要求。于是，小编今天教你**不用代码**，五分钟搭建一个属于自己的个人图床。

### PicX
?️ PicX 是一款基于 GitHub API 开发的图床工具，提供图片上传托管、生成图片链接和常用图片工具箱服务。

? 建议将本站添加到浏览器收藏夹，方便下次使用。 快捷键：Ctrl + D

? 作者：@[XPoet](https://xpoet.cn/)

? 仓库：<https://github.com/XPoet/picx>

? 文档：<https://picx-docs.xpoet.cn>

### 前置要求
- 拥有一个 Github 账号，没有可以[注册](https://docs.github.com/zh/get-started/start-your-journey/creating-an-account-on-github)。


### 新建存储库
1. 打开[个人存储库](https://github.com/zhao2022-Ux?tab=repositories)，点击 $\tt{\color{green} New}$，转到新建页面。
2. 创建一个新项目，如下图所示：
![](https://cdn.zhaohonghao-qwq.com/img/img无标1题.1hs3bvxs1u.png)

### 初始化 PicX
+ 使用 OAuth。
>1. 打开官网<https://picx.xpoet.cn/#/>，单击**使用 GitHub OAuth 授权登录**。
>2. 按照 Github 给出的指示一步一步下去。
>3. 进入[图床配置](https://picx.xpoet.cn/#/config) 填写用户名，项目名称，目录等，就好了。

+ 使用 Token。
>1. 打开官网<https://picx.xpoet.cn/#/>，单击**填写 GitHub Token 登录**。
>2. 打开 Github 新建 Token，见[视频](https://www.bilibili.com/video/BV1QzhUebEHi/?zw&spm_id_from=888.80996.embed_old&vd_source=6a0b71a226325dba546e5d6dd9e9c7d0)。
>+ ⚠️**Token 只会在创建后出现一次，刷新就没了，请自己截图保存。**
>3. 将 Token 输入即可绑定。

### 上传图片
+ 按照平时使用洛谷图床的步骤使用即可。
+ 点击 **复制链接** 即可获取图片链接。

## 自定义域名（可选）
有些人不喜欢 GithubUserName.github.io 这个域名，那么就自己买一个域名用来绑定图床，比如 cdn.luogu.com.cn。

### 将网站部署至 Vercel
1. 打开 [Vercel](vercel.com)，登录账号，没有可以注册。
2. 点击 $\tt{Add New}$ $\dots$，选择 Project。
3. 找到 Import Git Repository，将图床的 Github 项目名找到，点击 Import，找不到可以搜索。
4. 按照指南一步一步下去，最后完成会出现烟花界面。

### 绑定域名
1. 打开自己的域名运营商，找到域名解析控制台。
2. 添加 `CHEAM` 类型的域名解析，值为 `cname.vercel-dns.com`（在项目已经部署至 Vercel 的情况下）。
3. 打开 Vercel，找到项目，点击 Settings，找到 domain，在里面输入域名。
![](https://cdn.zhaohonghao-qwq.com/img/无标题.7ax1mek27a.webp)

最后稍等一会，域名绑定成功。

### 更改路径
1. 打开 <https://picx.xpoet.cn/#/>，右侧找到设置，下拉找到图片链接规则配置。
2. 将 GitHub Pages 的链接规则改为 `https://自定义域名/{{path}}`，出现警告，不用管它。
3. 将数据同步到云端仓库。
![](https://cdn.zhaohonghao-qwq.com/img/屏幕截图-2024-07-07-173856.2vemh5ijie.webp)
4. 完成配置，可以自己测试，剩下功能自己探索。

### 注意事项
+ **请勿使用 PicX 上传违反你当地法律的图片，所造成的一切后果与作者无关。**
+ 每次更改设置后或上传图片后，要更新至云端。
+ **Github Token 只会在创建后出现一次，刷新就没了，请自己截图保存。**
+ 有时更新失败，可能是 Github 被墙了，请稍后在尝试。