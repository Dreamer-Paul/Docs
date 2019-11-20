# 安装

推荐使用 Typecho 的最新正式版本安装本主题，并采用 PHP 7x 作为生产环境。如果你喜欢本项目，不妨为我提供微薄的一份赞助，支持一下吧！

![赞助奇趣保罗](img/donate.jpg)

## 全新安装

从 [GitHub](https://github.com/Dreamer-Paul/Single) 上获取本项目。

将主题压缩包上传到你的网站。Typecho 主题的默认存放路径在 `/usr/themes`

解压主题的压缩包文件，默认得到一个文件夹，应该为 `Single-master`

将文件夹更名为 `single` 以确保主题可以正常工作

登录你的 Typecho 后台，在导航栏找到 **控制台** > **外观** > **Single Theme** > **启用**

## 更新安装

打开主题选项，将里面的设置内容逐一拷贝到记事本保存。

将主题从 Single 更换为 Typecho 默认主题，并删除旧版主题文件。

按照全新安装的步骤获取压缩包并安装。

将记事本内的设置内容逐一填入主题选项的文本框内。


# 常见问题

> 文章热度不会变？

答：这个是评论数不是浏览数

> 手机版的菜单文章分类无法收缩？

答：这个是我本身的设计，不属于 BUG，主要是制作简单 23333

> 我博客的背景图怎么设置的？

答：1.4 以前的版本请在主题后台添加自定义 CSS，1.4 及以后的版本在后台直接输入图片地址即可。

> 为什么主题免费开源？

答：这是我做的第一款 Typecho 主题，抱着学习的态度制作而成。并且希望借此主题扩展人脉、结识更多的大佬和同道之人。当然你可以为我 [打赏](https://paugram.com/about.html#donate)，给我的博客提供微薄的帮助。这样我以后就可以给大家带来更好的作品了。

> 本主题的 WordPress 版有 BUG？

答：本人并没有参与制作 WordPress 版本，你所使用的均为他人的移植版，我是不提供功能上的解决方案的。

> 发现我的博客有 QQ 头像识别？

答：毕竟是自己捣鼓的第一个比较实用的功能，只要你赞助我的主题，即可获得该功能 /滑稽

> 想参与移植本主题？

答：请注明移植于**奇趣保罗**的 Typecho 主题 Single，优秀的移植作品我将同时推荐显示。

> 本站使用的背景图是哪张？

答：目前采用了我自己设计的随机壁纸 API，所有壁纸都是白色背景的，对于本主题是最适合不过的了。

> 博客采用多域名（例：www.sample.com 和 sample.com），其中一个图标字体显示不正常？

答：服务器默认是阻止跨域访问内容的，需要手动修改服务器头或只使用一个域名。

> 夜间模式会闪屏？

答：1.9 版本已经修复，欢迎下载更新。

> 其他问题

如果上述内容不符合你所遇到的问题，请加入我的企鹅群（[657692292](https://jq.qq.com/?_wv=1027&k=4Buhabv)）联系群主即时提问交流，也可在 GitHub 的 [Issues](https://github.com/Dreamer-Paul/Single/issues) 区提出。


# 主题选项

## 站点图标

填写一张 png 图片地址（192x192px），不填则使用默认图标

```
默认：网站地址/usr/themes/single/img/icon.png
```

## 站点背景

在这里填入一张图片地址，不填则显示纯色背景

```
默认：无
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

```css
// 让看板娘在夜间模式下变暗
.neon .pio-container{
    -webkit-filter: brightness(.7);
    filter: brightness(.7)
}
```

## 统计代码

如果你的网站想接入百度统计、Google Analytics 等网站流量统计平台，请在此填写对应的代码。同时这里还支持插入自己想要的额外 JavaScript 代码。需要包裹 `<script>` 标签。

```html
<script>ks.notice("测试的 JavaScript 代码", { color: "red" })</script>
```

## 作者信息

如果想在文章后面显示作者信息及版权相关提示，可在此填写内容。支持 HTML。

```html
特立独行的一只前端狗。本站未注明转载的文章均为原创，并采用 <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh" target="_blank" rel="nofollow">CC BY-NC-SA 4.0</a> 授权协议，<span style="color: #E91E63">转载请注明来源</span>，谢谢！如本站内容对你有所帮助的话，不妨 <a href="https://paul.ren/donate">捐助支持</a> 一下？
```

## 夜间模式

如果开启，主题则在 `22:00 - 5:00` 期间为访客自动开启夜间模式

![夜间模式](/img/night-mode.jpg)

## 复制提示

如果开启，则会在访客复制内容时提示注意版权事项

![复制提示](/img/copy-notice.jpg)

## 底部信息栏

如果开启，将会在页尾显示 “最近评论”、“最新文章” 和 “时光机” 三大列

![底部信息栏](/img/footer.jpg)

## 推荐文章 ID

在这里填写指定的文章 ID 后，将会覆盖底部的 “热门文章” 信息栏。填写格式如下，采用英文逗号和空格 `, ` 作为分隔。

```
60, 99, 103, 110, 122, 135
```

## 首页、存档页属性显示

在首页、存档页（按日期、分类展示文章的均为存档页）的每篇文章标题下，设置显示文章的一些信息

- 文章分类
- 文章标签
- 评论数

## 文章页属性显示

在文章页上方设置显示文章的一些信息

- 文章分类
- 文章标签
- 评论数
- 阅读数 `赞助版`


# 独立页面

## 友链页（赞助版）

在 Typecho 后台的导航栏找到 **管理** > **独立页面** > **新增** > **自定义模板** > **选择 “友链”**

添加友链的基础格式如下：

```
!!!
<links>
{名称, 描述, 链接, 头像}
{名称, 描述, 链接, 头像}
{名称, 描述, 链接, 头像}
</links>
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

为了让主题效果最大化的完美呈现，你可以选择参考这里所提供的一些 Typecho 设置。

## 日期格式

在 Typecho 后台的导航栏找到 **设置** > **评论** > **评论日期格式** 填写 `Y.m.d`

在 Typecho 后台的导航栏找到 **设置** > **阅读** > **文章日期格式** 填写 `Y.m.d`

## 文章输出

在 Typecho 后台的导航栏找到 **设置** > **阅读**

- 文章列表数目：`6`
- 每页文章数目：`6`