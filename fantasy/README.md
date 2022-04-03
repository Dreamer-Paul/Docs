# 信息

- 最新版本：1.8.5
- 上次更新：2022.4.2
- 上次修订：2022.4.3

文档国内（备用）链接：https://dreamer-paul.gitee.io/docs/fantasy

# 安装

推荐使用 Typecho 的最新正式版本安装本主题，并采用 PHP 7.x 作为生产环境。如果你喜欢本项目，不妨为我提供微薄的一份赞助，支持一下吧！

![赞助奇趣保罗](img/donate.jpg)

## 全新安装

从 [GitHub](https://github.com/Dreamer-Paul/Fantasy) 上或从「赞助版售后群」获取本项目。

将主题压缩包上传到你的网站。Typecho 主题的默认存放路径在 `/usr/themes`

解压主题的压缩包文件，默认得到一个文件夹，应该为 `Fantasy-master`

将文件夹更名为 `fantasy` 以确保主题可以正常工作（赞助版无需修改，应该为 `fantasy-pro`）

登录你的 Typecho 后台，在导航栏找到 **控制台** > **外观** > **Fantasy Theme** > **启用**

## 更新安装

打开主题选项，将里面的设置内容逐一拷贝到记事本保存。

将主题从 Fantasy 更换为 Typecho 默认主题，并删除旧版主题文件。

按照全新安装的步骤获取压缩包并安装。

将记事本内的设置内容逐一填入主题选项的文本框内。

## 获取赞助版

赞助版拥有什么功能？

- 夜间模式
- 三种文章布局
- Pjax 流畅切换页面
- 更好用的二级菜单
- 归档、友链、时间轴等多个独立页面
- 页尾工具栏可自定义展示多种类型的内容
- 以及更多...

如需使用本主题的赞助版，请加入企鹅群 [915297074](https://jq.qq.com/?_wv=1027&k=5Be3Qbk) 后联系群主获取。


# 常见问题

## 前端相关

> 菜单没有分类，分类在哪里？

答：新版（赞助版）已经支持在菜单上显示分类了。早期版本由于设计的限制无法在左侧制作二级菜单，分类默认放在了搜索里面，点击菜单下方的搜索按钮即可。同时你可以购买 [赞助版](?id=获取赞助版)，支持添加一个归档页面，可以显示你的所有分类以及罗列各分类的文章。

> 如何让左侧菜单的“进入后台”项始终显示？

答：打开主题路径下的 `header.php` 文件，替换如下代码即可完成操作。

```php
<?php if($this -> user -> hasLogin()): ?>
        <a href="<?php $this -> options -> adminUrl() ?>" target="_blank">进入后台</a>
<?php endif; ?>
```

替换成

```php
<a href="<?php $this -> options -> adminUrl() ?>" target="_blank">后台</a>
```

> 如何创建归档 / 时间轴 / 友链页面？（赞助版）

答：请在后台新建一个独立页面，并在编辑器右侧找到 “自定义模板”，选中对应的模板即可！

> 如何使用文章阅读统计功能？

答：打开主题选项，勾选“文章浏览次数记录”即可开启，“文章页属性”后面会自动增加该字段的展示。

> 主题的夜间模式从哪打开？（赞助版）

答：Fantasy 的夜间模式和 Single 手动开启的技术实现方式不同，需要将电脑设置成「暗夜模式」才可以开启喔。

- Windows：设置 -> 个性化 -> 颜色 -> 深色
- MacOS：系统偏好设置 -> 通用 -> 外观 -> 深色
- Android：夜间模式（需要系统和浏览器支持，因设备而异，低版本可能不受支持）
- iOS：设置 -> 显示与亮度 -> 深色（或者使用控制中心点击「深色模式」按钮）

> 主题没有演示站的图片 / 卡片模式

答：仅赞助版本提供多布局切换，为我打赏 `33.33` 软妹币即可获得该功能。

> 文章评论的头像裂开无法显示？

裂开主要是因为国内网络环境问题导致，根据文章 [Typecho 一些冷门小技巧](https://paugram.com/coding/typecho-secret-usage.html) 自定义一个 Gravatar 源，即可解决。

> 如何增加和修改图片/卡片模式下的随机文章替代图片？

答：图片文件均存放在主题目录的 `static/img/article` 文件夹，如果打算增加图片数量，需要再额外修改 `fantasy.php` 的 `post_image` 函数，主题默认存在 6 张图片。

```text
1.jpg
2.jpg
3.jpg
4.jpg
5.jpg
6.jpg
```

2022 年 2 月后的新版本，修改变量 `$images_pool_start` 和 `$images_pool_end` 以调整图片区间范围。

```php
// 随机图片池
static $images_pool_start = 1;
static $images_pool_end = 6;

static $images_pool = null;
static $images_pool_pointer = 0;
```

之前的老版本，修改 `rand` 函数内的两个参数，将 `rand(1, 8)` 这个 1-8 的范围替换成你修改后的范围即可~

```php
if($stat){
    Typecho_Widget::widget('Widget_Options') -> themeUrl('static/img/article/' . rand(1, 6) . '.jpg');
}
```

覆盖更新主题时会导致这里失效，注意进行识别！

> 如何使用多栏效果？

答：根据 [奇趣框架](https://works.paugram.com/style/grid.html) 栅格的使用方式编写 HTML 代码，可以随意拼凑多种方式使用。一个三栏编写方式如下：

```html
!!!
<div class="row">
    <div class="col-m-4">
!!!

// 此处即可填写 Markdown 内容

!!!
    </div>
    <div class="col-m-4">
!!!

// 此处即可填写 Markdown 内容

!!!
    </div>
    <div class="col-m-4">
!!!

// 此处即可填写 Markdown 内容

!!!
    </div>
</div>
```

由于 Typecho 的解析方式比较特殊，因此需要带上 `!!!` 划分内容区域。

> 我的表格内容太长，存在溢出页面或换行严重的情况，怎么改善？

答：根据 [奇趣框架](https://works.paugram.com/style/elements.html#table) 表格的使用方式增加一层 `ks-table` 的 DIV 容器，就可以解决这个问题。如果要禁止换行，可以在额外设置一条 `text-nowrap` 的类名。

```html
!!!
<div class="ks-table text-nowrap">
!!!

// 此处即可填写 Markdown 表格内容

!!!
</div>
!!!
```

以上两种方式，均仅限在使用「奇趣框架」的主题和网站上使用，而保罗的主题均采用这个框架进行设计。

## 服务端相关

> 安装主题，提示您选择的风格不存在

答：文件夹要重命名！重命名！重命名！重要的事情说三次！

> B 站追番内容无法正确显示，或出现报错提示？

答：请检查是否在 B 站隐私设置处公开追番数据，否则将无法进行获取。

> 追番内容访问很慢怎么回事？

答：这个和服务器连接 API 服务器的速度有关，1.8 版开始支持缓存功能，只有第一次打开会比较慢。获取之后有 3 天有效期，过期后第一次访问追番页面将会重新获取。

> 博客采用多域名（例：www.sample.com 和 sample.com），其中一个图标字体显示不正常？

答：服务器默认是阻止跨域访问内容的，需要手动修改服务器头或只使用一个域名。

> 伪静态怎么配置？

答：Nginx 配置：

```bash
location / {
    try_files $uri $uri/ $uri.html /index.php?$args;
}
```

Apache 配置：

```bash
<IfModule mod_rewrite.c>
    RewriteEngine on
    RewriteRule index.html$ index.php
    RewriteRule index-([1-9]+[0-9]*).html$ index.php?p=$1
    RewriteRule ([a-z]{1,})-([0-9]{1,}).html$ index.php?action=$1&id=$2
</IfModule>
```

## 其他问题

> 其他问题

如果上述内容不符合你所遇到的问题，请加入群（[915297074](https://jq.qq.com/?_wv=1027&k=5Be3Qbk)）联系群主即时提问交流，也可在 GitHub 的 [Issues](https://github.com/Dreamer-Paul/Fantasy/issues) 区提出。


# 主题选项

## 站点图标

填写一张 png 图片地址（192x192px），不填则使用默认图标

```
默认：网站地址/usr/themes/fantasy/static/img/icon.png
```

## 站点背景

在这里填入一张图片地址，不填则显示纯色背景

```
例如：https://paul.ren/static/bg.jpg
```

## 社交链接

参考下方格式编写，就可以实现我博客的效果了

```html
<a rel="nofollow" title="新浪微博" href="http://weibo.com/234891753" target="_blank">
    <i class="fa fa-weibo"></i>
</a>
<a rel="nofollow" title="企鹅群" href="https://jq.qq.com/?_wv=1027&k=4Buhabv" target="_blank">
    <i class="fa fa-qq"></i>
</a>
<a rel="nofollow" title="GitHub" href="https://github.com/Dreamer-Paul" target="_blank">
    <i class="fa fa-github"></i>
</a>
<a rel="nofollow" title="蒸汽" href="http://steamcommunity.com/id/dreamer-paul" target="_blank">
    <i class="fa fa-steam"></i>
</a>
<a rel="nofollow" title="小窝" href="https://paul.ren" target="_blank">
    <i class="fa fa-home"></i>
</a>
```

## 自定义样式表

如果你对主题现在的部分样式不够满意，可以在这里编写自己的 CSS 代码，以改变主题的默认外观。

## 统计代码

如果你的网站想接入百度统计、Google Analytics 等网站流量统计平台，请在此填写对应的代码。同时这里还可以插入自己想要的额外 JavaScript 代码。需要包裹 `<script>` 标签。

```html
<script>ks.notice("测试的 JavaScript 代码", { color: "red" })</script>
```

## 自定义全局字体

如果你不是很喜欢系统的默认字体，你可以在这里快速设置在 Google Fonts 上托管的免费开源字体。目前版本包括以下字体：

- 思源黑体
- 思源宋体
- 站酷小薇体
- 站酷快乐体

## 文章页属性展示

也就是在文章页 `post.php` 下，标题下面展示的内容。默认输出“日期”、“编辑”（登录后）且无法取消勾选。

- 投稿用户
- 文章分类
- ~~文章标签~~
- 评论数

> PS：文章标签在 1.8 (21.3.1) 版本下已默认展示在页尾底部，此处无法进行选择

## 建站日期

如果你想在页尾增加运行时间显示的效果，需要在这里填入一个建站日期，不填则无法正常输出

```
2018/07/09
```

## 备案号

如果你想在页尾增加显示备案号，需要在这里填入一个备案号，不填则不输出

## 追番数据获取模式

如果你需要用到主题的“追番”页面，可以在这里选择适合你的番剧获取方式

> 该设置项默认使用“番组计划”方式获取，支持显示番剧播放进度（须手动前往该网站或通过脚本的方式更新）。哔哩哔哩的番剧数据获取会更稳定，但不支持番剧进度功能

## 追番用户 ID

如果你需要用到主题的“追番”页面，你需要在这里填写一个 [BiliBili](https://www.bilibili.com) 或 [bangumi.tv](https://bangumi.tv/) 的用户 ID，不填则输出作者的追番记录

## 左侧菜单项

如果你想要扩展左侧菜单的内容，你需要在这里 *按照规定格式* 填写一段 JSON 信息，不填则不输出

一个链接很简单：

```json
{"name": "外链测试", "link": "https://paugram.com"}
```

如果需要给链接设置为在新窗口打开，则需要增加 `target` 参数：

```json
{"name": "外链测试", "link": "https://paugram.com", "target": "_blank"}
```

添加多条就需要在每个项目之间添加 `, ` 作为间隔符：

```json
{"name": "外链测试", "link": "https://paugram.com"}, {"name": "外链测试", "link": "https://paul.ren"}
```

## 页尾展示内容

在主题所有页面的页尾版权处，选择输出对应内容

- 备案号 `需要配置：备案号`
- 社交链接 `需要配置：社交链接`
- 运行时间 `需要配置：建站日期`
- 随机一言

## 页尾工具栏（赞助版）

在主题所有页面的页尾中，展示一个工具栏，功能类似与部分主题的侧边栏

主题默认勾选“最热文章”、“时光机”、“最近评论”和“站点信息”，你可以根据自己的喜好进行选择，建议不超过 4 个。

- 最新文章
- 最热文章
- 时光机
- 最近评论
- 标签云
- 站点信息

## 文章展现风格（赞助版）

主题默认为简洁式风格，你可以在这里选择你最喜欢的文章展现风格

- 简洁
- 详细
- 卡片

它们的效果分别是：

![简洁](/img/simple-mode.jpg)

![详细](/img/detail-mode.jpg)

![卡片](/img/card-mode.jpg)

## 其他页面文章展现风格（赞助版）

该设置项和上面的文章展示风格配置几乎一致，但它作用于「其他页面」。包括但不限于：分类/标签/年份/月份/搜索 等页面下。

- 简洁
- 详细
- 卡片

## 文章浏览次数记录（赞助版）

如果你想开启文章浏览统计，在这里就可以启用它。开启后将同时在文章详情显示浏览数，清除 Cookie 则默认视为新访客

## [X] 搜索栏显示内容（赞助版）

> PS：此功能在赞助版 1.7 后移除，默认只输出文章标签

主题左侧菜单由于构造设计限制，暂不支持二级菜单。文章分类或标签可以在这里找到。当然你可以在 `赞助版` 创建一个 `归档页`，打开就可以看到各分类及其文章

- 标签
- 分类

![卡片](/img/search.jpg)

## PJAX 重载函数（赞助版）

由于主题默认开启了 PJAX，如果你启用了部分 JS 插件，并在使用本主题时出现失效的情况，请在此处填写对应的重载函数

```javascript
// 修复百度统计失效问题
if(typeof _hmt !== 'undefined') _hmt.push(['_trackPageview', location.pathname + location.search]);
```

# 文章页面

## 文章插图（赞助版）

如果你使用了“详细”或“卡片”模式，本主题将默认从文章中取第一张图作为文章插图。如果文章内不包含图片，则会自动调用主题 `static\img\article` 文件夹下的 `8` 张图片。你可以选择将文件夹内的图片进行替换，并通过修改 `fantasy.php` 的 `post_image` 函数，实现随机出现更多图片。

# 独立页面

## 追番页

> 需要在主题选项里配置 [追番用户 ID](#/?id=追番用户-id) 后才可以显示你自己的追番信息

在 Typecho 后台的导航栏找到 **管理** > **独立页面** > **新增** > **自定义模板** > **选择「追番」**

PS：赞助版提供了静态缓存，可大幅度加速访问页面的速度（受服务器位置差异，首次可能会略慢）

![追番页](/img/bangumi-page.jpg)

## 归档页（赞助版）

在 Typecho 后台的导航栏找到 **管理** > **独立页面** > **新增** > **自定义模板** > **选择「归档」**

![归档页](/img/archive-page.jpg)

## 友链页（赞助版）

在 Typecho 后台的导航栏找到 **管理** > **独立页面** > **新增** > **自定义模板** > **选择「友链」**

添加友链的基础格式如下：

```
!!!
<div class="clearfix">
    {名称, 描述, 链接, 头像}
    {名称, 描述, 链接, 头像}
    {名称, 描述, 链接, 头像}
</div>
!!!
```

单条友链的示例如下：

```
{首页, 奇趣保罗的日常, https://paul.ren, https://paul.ren/avatar.jpg}
```

- **名称**：友链名称
- **描述**：友链描述
- **链接**：友链链接
- **头像**：友链头像，支持相对链接或绝对链接

以上属性缺一不可，否则可能会导致解析出现异常。

![友链页](/img/friends-page.jpg)

## 时间轴页面（赞助版）

在 Typecho 后台的导航栏找到 **管理** > **独立页面** > **新增** > **自定义模板** > **选择 “时间轴”**

![时间轴页](/img/timeline-page.jpg)


# 组件要求

## 代码高亮

- 不能与其他插件共用，例如 `Highlight.js`
- 需要在文章中指定语言（按照下面的示例即可）


    ```php
    echo "Hello Paul!";
    ```

或者是...

    ```javascript
    ks.notice("It's Dreamer-Paul!", {
        color: "yellow"
    });
    ```
目前主题的代码高亮是采用了定制过的 `PrismJS` 插件，支持以下语言，如果列表中的语言未包含你所使用的语言，可以在 [其官网](https://prismjs.com/download.html) 进行定制，替换主题 `static` 目录下的 `prism.js` 文件即可！

- HTML + XML + SVG
- CSS
- C-Like
- JavaScript
- ASP.NET(C#)
- Bash + Shell
- BBCode
- C
- C++
- Docker
- Git
- Go
- Haskell
- Java
- JSON
- Less
- Markdown
- Nginx
- Objective-C
- Pascal + Object Pascal
- Perl
- PHP
- PowerShell
- Python
- Puby
- SQL
- Swift
- TypeScript
- VIM


# 参考设置

为了让主题效果最大化的完美呈现，你可以选择参考这里所提供的一些 Typecho 推荐设置，并替换掉默认设置。

## 日期格式

在 Typecho 后台的导航栏找到 **设置** > **评论** > **评论日期格式** 填写 `Y.m.d`

在 Typecho 后台的导航栏找到 **设置** > **阅读** > **文章日期格式** 填写 `Y.m.d`

## 文章输出

在 Typecho 后台的导航栏找到 **设置** > **阅读**

- 文章列表数目：`6`
- 每页文章数目：`6`
