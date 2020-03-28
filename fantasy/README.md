# 信息

- 最新版本：1.7
- 上次更新：2020.3.28
- 上次修订：2020.3.28


# 安装

推荐使用 Typecho 的最新正式版本安装本主题，并采用 PHP 7x 作为生产环境。如果你喜欢本项目，不妨为我提供微薄的一份赞助，支持一下吧！

![赞助奇趣保罗](img/donate.jpg)

## 全新安装

从 [GitHub](https://github.com/Dreamer-Paul/Fantasy) 上或从 赞助版售后群 获取本项目。

将主题压缩包上传到你的网站。Typecho 主题的默认存放路径在 `/usr/themes`

解压主题的压缩包文件，默认得到一个文件夹，应该为 `Fantasy-master`

将文件夹更名为 `fantasy` 以确保主题可以正常工作（赞助版无需修改）

登录你的 Typecho 后台，在导航栏找到 **控制台** > **外观** > **Fantasy Theme** > **启用**

## 更新安装

打开主题选项，将里面的设置内容逐一拷贝到记事本保存。

将主题从 Fantasy 更换为 Typecho 默认主题，并删除旧版主题文件。

按照全新安装的步骤获取压缩包并安装。

将记事本内的设置内容逐一填入主题选项的文本框内。

## 获取赞助版

赞助版拥有什么功能？

- 夜间模式
- 三种首页文章布局
- 更好用的二级菜单
- 归档、友链、时间轴等多个独立页面
- 以及更多...

如需使用本主题的赞助版，请加入企鹅群 [915297074](https://jq.qq.com/?_wv=1027&k=5Be3Qbk) 后联系群主获取。


# 常见问题

> 菜单没有分类，分类在哪里？

答：由于设计的限制无法在左侧制作二级菜单，分类默认放在了搜索里面，点击菜单下方的搜索按钮即可。同时你可以购买 [赞助版]()，支持添加一个归档页面，可以显示你的所有分类以及罗列各分类的文章。

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

> 博客采用多域名（例：www.sample.com 和 sample.com），其中一个图标字体显示不正常？

答：服务器默认是阻止跨域访问内容的，需要手动修改服务器头或只使用一个域名。

> 主题没有演示站的图片 / 卡片模式

答：仅赞助版本提供多布局切换，为我打赏 `33.33` 软妹币即可获得该功能。

> 如何增加和修改图片/卡片模式下的文章替代图片？

答：图片文件均存放在主题目录的 `static/img/article` 文件夹，如果打算增加图片数量，需要修改 `fantasy.php` 的 `post_image` 函数。

```php
if($stat){
	Typecho_Widget::widget('Widget_Options') -> themeUrl('static/img/article/' . rand(1, 6) . '.jpg');
}
```

将 `rand(1, 8)` 这个 1-8 的范围替换成你修改后的范围即可~

> 其他问题

如果上述内容不符合你所遇到的问题，请加入提问反馈群（[915297074](https://jq.qq.com/?_wv=1027&k=5Be3Qbk)）或日常交流群（[657692292](https://jq.qq.com/?_wv=1027&k=4Buhabv)）联系群主即时提问交流，也可在 GitHub 的 [Issues](https://github.com/Dreamer-Paul/Fantasy/issues) 区提出。


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

在主题所有页面的页尾中选择输出对应内容

- 备案号 `需要配置`
- 社交链接 `需要配置`
- 运行时间 `需要配置`
- 随机一言

## 文章展现风格（赞助版）

主题默认为简洁式风格，你可以在这里选择你最喜欢的文章展现风格

- 简洁
- 详细
- 卡片

它们的效果分别是：

![简洁](/img/simple-mode.jpg)

![详细](/img/detail-mode.jpg)

![卡片](/img/card-mode.jpg)

## 文章浏览次数记录（赞助版）

如果你想开启文章浏览统计，在这里就可以启用它。开启后将同时在文章详情显示浏览数，清除 Cookie 则默认视为新访客

## 搜索栏显示内容（赞助版）

> PS：此功能在赞助版 1.7 后取消，只输出标签

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

在 Typecho 后台的导航栏找到 **管理** > **独立页面** > **新增** > **自定义模板** > **选择 “追番”**

## 归档页（赞助版）

在 Typecho 后台的导航栏找到 **管理** > **独立页面** > **新增** > **自定义模板** > **选择 “归档”**

## 友链页（赞助版）

在 Typecho 后台的导航栏找到 **管理** > **独立页面** > **新增** > **自定义模板** > **选择 “友链”**

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

## 时间轴页面（赞助版）

在 Typecho 后台的导航栏找到 **管理** > **独立页面** > **新增** > **自定义模板** > **选择 “时间轴”**


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