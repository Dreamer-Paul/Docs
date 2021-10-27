# 信息

- 最新版本：1.0
- 上次更新：2021.10.27
- 上次修订：2021.10.27

文档国内（备用）链接：https://dreamer-paul.gitee.io/docs/hingle

# 安装

推荐使用 Hexo 的最新正式版本安装本主题。如果你喜欢本项目，不妨为我提供微薄的一份赞助，支持一下吧！

![赞助奇趣保罗](img/donate.jpg)

## 全新安装

根据 [官网](https://hexo.io/zh-cn) 提示，安装 Hexo 命令行工具 `npm install hexo-cli -g` 初始化一个 Hexo 主页项目。

从 [GitHub](https://github.com/Dreamer-Paul/Hingle) 上获取本项目。

下载并解压，将文件夹重命名为 `hingle` 并放置在 Hexo 目录的 `themes` 目录下。

修改 Hexo 目录下 `_config.yml` 文件的 `theme` 字段，更换成 `hingle` 即可。

```yml
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: hingle
```

修改主题目录下的 `_config.yml` 文件，可参考 `_config.example.yml` 文件和当前文档进行设置。

## 更新安装

升级主题前，请先参阅 [更新记录](https://github.com/Dreamer-Paul/Hingle/releases) 上对应版本的说明（现在可能还没有，毕竟还没有发布第一个版本）

重新修改 `_config.yml` 文件的内容（如果需要），保存后重新使用 `hexo d` 命令部署你的主页即可。


# 常见问题

## 前端相关

> 手机版的菜单文章分类无法收缩？

答：这个是我本身的设计，不属于 BUG，主要是制作简单 23333

> 我博客的背景图怎么设置的？

答：参考主题 `background` 设置项。

> 我博客使用的背景图是从哪来的？

答：目前采用了我自己设计的 [随机壁纸 API](https://api.paugram.com)，所有壁纸都是白色背景的，对于本主题是最适合不过的了。

> 夜间模式会闪屏？

答：下个版本将会切换为根据系统设置适配，不再提供手动开关。

> 文章底部作者信息的头像如何设置？

答：参考主题 `author_avatar` 设置项。

> 如何使用多栏效果？

答：根据 [奇趣框架](https://works.paugram.com/style/grid.html) 栅格的使用方式编写 HTML 代码，可以随意拼凑多种方式使用。一个三栏编写方式如下：

```html

<div class="row">
    <div class="col-m-4">
        <!-- 你的内容，支持 Markdown -->
    </div>
    <div class="col-m-4">
        <!-- 你的内容，支持 Markdown -->
    </div>
    <div class="col-m-4">
        <!-- 你的内容，支持 Markdown -->
    </div>
</div>
```

相较于 Typecho，Hexo 对 HTML 内容的解析方式不需要带上 `!!!` 就可以。

## 其他问题

> 为什么主题免费开源？

答：这是我做的第一款 Hexo 主题，抱着学习的态度制作而成。并且希望借此主题扩展人脉、结识更多的大佬和同道之人。当然你可以为我 [打赏](https://paul.ren/donate)，给我的博客提供微薄的帮助。这样我以后就可以给大家带来更好的作品和文章了。

> Single 主题和 Hingle 主题有什么关系？

答：Single 主题为本主题的原始版本，源代码为 Typecho 平台所设计，但前端部分是可以灵活切换的，因此我做了一次移植，得到了现在的 Hingle 主题。

> 想参与移植本主题？

答：请注明移植于**奇趣保罗**的 Hexo 主题 Hingle，优秀的移植作品我将同时推荐显示。

> 其他问题

如果上述内容不符合你所遇到的问题，请加入群（[915297074](https://jq.qq.com/?_wv=1027&k=5Be3Qbk)）联系群主即时提问交流，也可在 GitHub 的 [Issues](https://github.com/Dreamer-Paul/Hingle/issues) 区提出。


# 主题配置项

此处将列出本主题的 `_config.yml` 配置文件属性和相关说明，在修改配置之前，建议你先学习一下 YAML 文档的 [使用方式](https://www.ruanyifeng.com/blog/2016/07/yaml.html)，这将减少你在编写配置中遇到的大多数问题。

> 字段属性在文档上均显示为首字母大写，实质为小写

## Author

作者名称，字符串类型，默认为 `Hingle`

```yml
# 默认
author: 'Paul'
```

## Author_Avatar

作者头像地址，字符串类型，默认为 `https://sdn.geekzu.org/avatar/d22eb460ecab37fcd7205e6a3c55c228?s=200&r=X&d=`

```yml
# 默认
author_avatar: 'https://sdn.geekzu.org/avatar/d22eb460ecab37fcd7205e6a3c55c228?s=200&r=X&d='
```

## Author_Text

作者信息，可以插入作者自述、版权说明等内容，字符串格式，默认为 `请在这里设置你的作者信息`，支持 HTML 内容。

```yml
# 示例
author_text: '特立独行的一只前端菜狗。本站未注明转载的文章均为原创，并采用 <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh" target="_blank" rel="nofollow">CC BY-NC-SA 4.0</a> 授权协议，<span style="color: #E91E63">转载请注明来源</span>，谢谢！如本站内容对你有所帮助的话，不妨 <a href="https://paul.ren/donate">捐助支持</a> 一下？同时欢迎订阅关注 <a href="https://paul.ren/note" target="_blank">我的日记</a>，唠嗑（分享）每日的折腾经历。' # 作者信息
```

## Social

自定义社交链接，数组类型，默认提供了 3 个项目。社交链接的图标采用 [FontAwesome 4.0](https://fontawesome.com/v4.7.0/icons) 的设计，别问我为什么用 4.0，因为新版商业化了，看着就不舒服==

一个链接的编写方式可以是这样子：

```yml
# 示例
social:
  - title: 'GitHub' # 社交网站名称
    icon: 'github' # 图表类名，最终生成 fa fa-github
    link: 'https://github.com/Dreamer-Paul' # 社交网站链接
```

如果要编写多条，按照这个格式往下写就可以了

```yml
# 示例
social:
  - title: 'Github'
    icon: 'github'
    link: 'https://github.com/Dreamer-Paul'
  - title: 'Steam'
    icon: 'steam'
    link: 'http://steamcommunity.com/id/dreamer-paul'
  - title: '首页'
    icon: 'home'
    link: 'https://paul.ren'
```

它最终会生成这样的一段 HTML 代码：

```html
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

## Background

自定义站点的背景图片，字符串类型，默认没有启用这个设置项。如要启用，在此编写一段有效的 URL 即可完成。

```yml
# 默认
# background: 'https://api.paugram.com/wallpaper?source=gh'
```

## Menu

页眉导航项目，键值对类型，默认编写了 2 个项目，点击可能是 404 页面。

```yml
# 默认
menu:
  '关于我': /about
  '朋友们': /friends
```

## Config

本设置项用于改变 `single.js` 初始化的设置，用于控制主题前端上的一些功能。

### Night

如果开启，主题则在 `22:00 - 5:00` 期间为访客自动开启夜间模式

![夜间模式](/img/night-mode.jpg)

### Copyright

如果开启，则会在访客复制内容时提示注意版权事项

![复制提示](/img/copy-notice.jpg)


# 二次开发

## 页眉

主题本身并没有提供展示自定义下拉菜单的功能，但你可以通过修改 `layout/_partial/header.ejs` 的方法实现。这个是二级菜单的结构：

```html
<div class="has-child">
    <a>分类</a>
    <div class="sub-menu">
        <a href="#1">二级链接</a>
        <a href="#2">二级链接</a>
        <a href="#3">二级链接</a>
    </div>
</div>
```

## 容器

主题的容器框架其实是可以修改间距的，默认为 `min`，你可以试试删掉它，或是改成 `mid` 或者 `max` 试试看？这些文件一般都在 `layout` 目录下。

```html
<div class="wrap min">
    <!-- 这个是我的奇趣框架项目 (Kico Style) 内置的 -->
</div>
```
