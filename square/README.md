# 信息

- 最新版本：608b5a9
- 上次更新：2024.4.20
- 上次修订：2024.4.20

文档国内（备用）链接：https://dreamer-paul.gitee.io/docs/square

# 安装

你可以通过代码直接引用或者通过 Typecho 插件的方式快速使用。如果你喜欢本项目，不妨为我提供微薄的一份赞助，支持一下吧！

![赞助奇趣保罗](img/donate.jpg)

## 独立使用

在网页 `head` 标签引用项目的 CSS 文件 `SQPlayer.css`：

```html
<head>
...
<link href="SQPlayer.css" rel="stylesheet" type="text/css"/>
...
</head>
```

在网页 `body` 标签内的最后一行，或使用 `defer` 属性引用项目的 JS 文件 `SQPlayer.js`：

```html
<body>
...
<script src="SQPlayer.js"></script>
</body>
```

Or...

```html
<head>
...
<script src="SQPlayer.js" defer></script>
</head>
```

在网页 `body` 标签内插入一个 `sqp` 标签：

```html
<body>
...
<sqp></sqp>
...
</body>
```

如果使用 `data-cid` 属性引用播放器，就写成这样，其中 `23682511` 就是网易云音乐一首歌的 ID。

```html
<sqp data-cid="23682511"></sqp>
```

如果使用静态方法引用播放器，则需要同时编写四个属性。

```html
<sqp data-title="Crimson & Clover" data-artist="Tommy James" data-cover="封面链接" data-link="歌曲链接"></sqp>
```

其他属性可以参考本文档的 [属性](#属性) 节点。

## 使用插件

> 使用保罗的 Typecho 插件，你就可以快速给自己的博客添加播放器！

### 全新安装

从 [GitHub](https://github.com/Dreamer-Paul/Square-Player) 上获取本项目。

将插件压缩包上传到你的网站。Typecho 插件的默认存放路径在 `/usr/plugins`

解压插件的压缩包文件，默认得到一个文件夹，应该为 `Square-Player-master`

将文件夹更名为 `SQP` 以确保插件可以正常工作

登录你的 Typecho 后台，在导航栏找到 **控制台** > **插件** > **Square Player** > **启用**

### 调用播放器

在你的文章里编写如下代码，即可自动根据该网易云音乐 ID 获取信息。

```html
!!!
<sqp data-cid="23682511"></sqp>
!!!
```

# 属性

Square Player 支持以下属性，它们分别的意义是：

属性名|用途
------|----
`left`|至左显示
`data-title`|歌曲名，用于自定义歌曲
`data-artist`|艺术家，用于自定义歌曲
`data-cover`|专辑封面图片链接，用于自定义歌曲
`data-link`|歌曲地址，用于自定义歌曲
`data-cid`|网易云音乐的 ID，如果编写了此项目，将忽略以上 `data-*` 设置

将以上属性放在 `<sqp>` 标签内即可生效。

# 方法

## 播放器实例

### Play

播放该实例的音乐

```javascript
player.play();
```

### Pause

暂停该实例的音乐

```javascript
player.pause();
```

### Toggle

切换播放/暂停该实例的音乐

```javascript
player.toggle();
```

### Destroy

卸载当前实例，释放内存

```javascript
player.destroy();
```

## 扩展方法

### Init

遍历页面的 `sqp` 元素，初始化播放器。方块播放器的扩展方法默认会遍历整个页面，如果你的网站使用了 PJAX 技术，在切换页面的同时，不妨试试以下方法重载播放器？

```javascript
_SQP_Extend.init();
```

项目默认使用的是由 Meto 提供的网易云 API，你也可以修改此处代码，将服务替换为 [保罗的 API](https://api.paugram.com)。

```javascript
window._SQP_Extend = new SQP_Extend({
  server: "paul"
});
```

### Destroy

卸载页面的所有播放器实例，释放内存。部分 PJAX 库貌似并没有「离开页面」的事件，没法像 Vue/React 这样的框架可以在生命周期里实现更彻底的内存释放。

```javascript
_SQP_Extend.destroy();
```
