# 信息

- 最新版本：2.4
- 上次更新：2022.8.11
- 上次修订：2024.7.8

# 安装

推荐使用 Typecho 的最新正式版本安装本插件，并采用 PHP 7x 作为生产环境。如果你喜欢本项目，不妨为我提供微薄的一份赞助，支持一下吧！

![赞助奇趣保罗](img/donate.jpg)

## 使用插件

使用保罗的 Typecho 插件，你就可以快速给自己的博客添加看板娘！

### 全新安装

从 [GitHub](https://github.com/Dreamer-Paul/Pio) 上获取本项目。

将插件压缩包上传到你的网站。Typecho 插件的默认存放路径在 `/usr/plugins`

解压插件的压缩包文件，默认得到一个文件夹，应该为 `Pio-master`

将文件夹更名为 `Pio` 以确保插件可以正常工作

登录你的 Typecho 后台，在导航栏找到 **控制台** > **插件** > **Pio** > **启用**

### 更新安装

打开插件的选项，将里面的设置内容逐一拷贝到记事本。

禁用本插件，并删除旧版插件原有的文件。

按照全新安装的步骤获取压缩包并安装。

将记事本内的设置内容逐一填入插件设置的文本框内。

### 指导视频

你是 Typecho 新手吗？不妨先观看一下本视频后再进行操作吧！[访问原站观看](https://www.bilibili.com/video/av47815909) 将支持展示 CC 字幕！

<iframe src="//player.bilibili.com/player.html?isOutside=true&aid=47815909&bvid=BV1Kb411s7h4&cid=83754339&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"></iframe>

## 独立使用

如果你使用的博客平台不是 Typecho 从而无法使用，或是想在自己的网站项目里使用保罗的看板娘插件，可以通过参考本节点来实现。

从 [GitHub](https://github.com/Dreamer-Paul/Pio) 上获取本项目。

将插件压缩包解压，提取其中的 `models` 和 `static` 文件夹。

### 引用 CSS 资源

在你网站的 `head` 标签内引用本项目的 CSS 样式表文件。

```html
<!-- 引用看板娘交互所需的样式表 -->
<link href='你的站点路径/static/pio.css' rel='stylesheet' type='text/css'/>
```

### 引用 JS 资源

在你项目的页尾部分引用本项目的 JS 文件。

```html
<!-- 引用 Live2D 核心组件 -->
<script src='你的站点路径/static/l2d.js'></script>
<!-- 引用看板娘交互组件 -->
<script src='你的站点路径/static/pio.js'></script>
```

### 插入 DOM 内容

> PS：在独立使用的情况下，看板娘的自定位置和高宽无法通过 JS 直接设置，请根据需要自行修改或使用后端语言进行输出。

```html
<div class="pio-container {自定位置}">
    <div class="pio-action"></div>
    <canvas id="pio" width="{看板娘宽度}" height="{看板娘高度}"></canvas>
</div>
```

而他们的允许值如下：

| 参数名 | 类型 | 允许值 |
| ----- | ---- | ---- |
| 自定位置 | `string` | `left` `right`|
| 看板娘宽度 | `number` | 整数，不带 `px`，即 HTML 写法 |
| 看板娘高度 | `number` | 整数，不带 `px`，即 HTML 写法 |

这是一段示例：

```html
<div class="pio-container left">
    <div class="pio-action"></div>
    <canvas id="pio" width="350" height="350"></canvas>
</div>
```

### 设置启动器

加载完 JS 文件后并不会立即自动生成看板娘，你需要编写一段启动代码来运行看板娘。

这是一段示例：

```javascript
var pio = new Paul_Pio({
    "mode": "fixed",
    "hidden": true,
    "content": {
        "welcome": ["欢迎来到保罗的小宇宙！", "今天天气不错，一起来玩吧！", "博主每天都有些折腾记录，欢迎前往他的小窝阅读~"],
        "custom": [
            {"selector": ".comment-form", "text": "欢迎参与本文评论，别发小广告噢~"},
            {"selector": ".home-social a:last-child", "text": "在这里可以了解博主的日常噢~"},
            {"selector": ".post-item a", "type": "read"},
            {"selector": ".post-content a, .page-content a", "type": "link"}
        ]
    },
    "night": "single.night()",
    "model": ["https://paugram.com/usr/plugins/Pio/models/yuan/model.json"]
});
```

启动器的必备参数可以参考本文档的 [参数](#参数) 节点。

# 常见问题

> 插件无法启用，Typecho 提示插件不存在（还有可能提示 Server Error）

答：请确认插件文件夹名称修改为 `Pio` 而不是 `Pio-master`。近期有人反馈使用部分 <a href="https://racns.com/211.html" rel="nofollow">后台美化模板</a> 后也会出现无法启用插件的情况，修改后台文件本身就是一种影响稳定性的操作，不建议这样做。

> 插件成功启用，打开网站发现没有显示看板娘

答：如果你使用的是 IIS 服务器/基于 IIS 的虚拟机空间，则为缺少 MIME 导致。详见本 [Issue](https://github.com/Dreamer-Paul/Pio/issues/1)。

如果你使用的是自己的 VPS 服务器，很有可能是「模型地址」与「站点地址」不同，导致产生了跨域访问。遇到这种情况建议你的站点「只使用一个域名」，并且强制使用 HTTPS（如果有），这样就能确保到网站只有一个入口，这样就不会出现跨域的情况了。如果你仍要使用多域名的方式使用，请参阅下面的 “如何设置跨域访问” 问题。

如果你的网站是虚拟空间搭建的，同时采用 CNAME 解析或是开启了部分主机商的“加速”选项。则是由于实际域名与站点域名不同，跨域访问被阻止。这种情况只能联系或更换服务商，或是采用其他人的支持跨域使用的看板娘 API。（我本来也想做的但是缺经费，Emmm... ~~点击上方赞助为我加油~~）

还有一种情况就是你使用的模板存在 Bug，具体的症状表现为任何「需要在前端展示」的插件均失效。这种情况你可以联系模板作者修复，或是自己修改模板的 `footer.php` 文件，添加下面的函数。确保插件所使用的 JS 文件和 CSS 样式能够正常在页面上输出和访问。

```php
<?php $this -> footer(); ?>
```

> 看板娘成功加载，但显示不齐全，只显示了一部分

答：由于每个模型的设计比例不一致，请在插件选项里设置 [自定宽高](#自定宽高)，即可纠正。如果是独立使用，请修改 [DOM](#插入-dom-内容) 里的 `width` 和 `height` 属性.

> 插件设置里已经关闭“在移动设备上隐藏看板娘”了，但依旧不显示？

答：部分主题兼容了本插件（例：Miracle），并默认在手机上禁止显示看板娘。你需要自己修改主题对应的 CSS 文件，将相关代码进行删除。

```css
.pio-container{
    display: none;
}

@media (min-width: 992px){
    .pio-container {
        display: block;
    }
}
```

> 如何设置跨域访问

如果你使用的不是虚拟空间而是自己的 VPS 服务器，同时打算多域名使用，最简单的方法就是改回同域名，将模型放在插件的 `models` 文件夹内。你还可以通过修改 Nginx 的站点配置解决。

```bash
location ^~ 你的站点路径
{
    add_header Access-Control-Allow-Origin 允许访问的网站地址，包括协议;
}
```

例如你的看板娘模型在 `www.paul.com/model`，并只能允许 `paugram.com` 访问

```bash
location ^~ /model
{
    add_header Access-Control-Allow-Origin https://paugram.com;
}
```

> 我使用的模板有 PJAX，切换页面之后看板娘无法显示或报错

答：在你模板的设置选项找到重载设置，通过本插件的 [重载方法](#重载) 进行重载。还有一种极端方法就是直接关闭 PJAX 功能。

> 想要我博客现用的模型？还有更多？

答：去我自己搭建的 [梦象模型站](https://mx.paul.ren) 或是加我的群找我要吧！千万别引用我这个小水管的地址啊 😉

> 我有在其他渠道获取的模型，如何使用？

答：你可以在插件设置里面选择使用外链方法载入模型（[选择外链模型](#选择外链模型)），或是将自己的模型放在插件的 `models` 文件夹内（[选择模型](#选择模型)），确保每个模型放在单独的一个文件夹，并且模型配置文件以 `model.json` 命名。以下是示例结构：

```
plugins/Pio/models
 ┌ pio（模型名称）
 ├─ motions（动作文件）
 ├─ textures（贴图文件）
 ├─ model.moc（配置文件）
 └─ model.json（配置文件）
```

> 点击页面或模型，控制台就会出现报错

答：这是由于模型的 `model.json` 缺少 `hit_areas_custom` 属性导致的，目前比较常见的报错是下面这种。你可以手动添加相关代码进行修复。

```javascript
l2d.js:1 Uncaught TypeError: Cannot read property '0' of undefined
    at o.r.hitTestSimpleCustom (l2d.js:1)
    at o.hitTestCustom (l2d.js:1)
    at o.tapEvent (l2d.js:1)
    at p (l2d.js:1)
    at g (l2d.js:1)
```

在 `model.json` 添加下列代码即可解决。

```json
"hit_areas_custom": {
    "head_x": [-0.35, 0.6],
    "head_y": [0.19, -0.2],
    "body_x": [-0.3, -0.25],
    "body_y": [0.3, -0.9]
}
```

> 看板娘隐藏后如何让她再次显示

答：目前 2.4 版默认设计为永久隐藏，你可以通过清除浏览器 localStorage 的方式（`F12` -> `Application` -> `Local Storage` -> `你的网站` -> `posterGirl` -> `X 删除`）让她再次出现，这个问题将在下一个版本进行改善。

> 其他问题

如果上述内容不符合你所遇到的问题，请加入群（[915297074](https://jq.qq.com/?_wv=1027&k=5Be3Qbk)）联系群主即时提问交流，也可在 GitHub 的 [Issues](https://github.com/Dreamer-Paul/Pio/issues) 区提出。

提 Issues 的正确方式，可以参考如下案例：

[关闭看板娘后，重新显示的位置不对](https://github.com/Dreamer-Paul/Pio/issues/21)
[能否增加自定义边距功能](https://github.com/Dreamer-Paul/Pio/issues/19)

“运行环境”处如果没有出现「后台报错」的情况，可以在对应环境处使用 `/` 留空不填写。

```
操作系统版本：/
Apache/Nginx 版本：/
PHP 版本：/
插件版本：7d3cac
浏览器版本：任意新浏览器
```


# 后台设置

如果你通过 Typecho 插件的方式食用，即可参考本节点。

## 选择模型

这里的模型均位于 `插件目录/models` 文件夹，并且所有模型的配置文件名必须为 `model.json` 才可以正常使用。

## 选择外链模型

用于使用外链模型。填写该选项后，上面选择的模型均无效。前台仅显示这里填写的一个模型。

引用的链接建议采用绝对路径（例 `https://paul.ren/static/416/model.json`）而不是相对路径（例 `/static/416/model.json`）否则会导致在不同页面下由于链接 404 错误，无法显示看板娘。

> PS：模型配置文件一般为 `model.json`，请勿引用 `.moc` 文件！

## 自定位置

可选靠左或靠右，根据你所使用的主题布局来进行决定。

## 自定宽高

如果你在 [梦象](https://mx.paul.ren) 下载模型，一般会给你推荐高宽。按照这个填入即可，无需 `px` 单位。如果没有推荐高宽，你可以自行修改测试。修改成功后看板娘就不会出现显示不全的问题啦！

## 夜间模式函数

用于切换主题的夜间模式。如果你的主题支持切换夜间模式，在这里填写对应的方法可以在看板娘中点击按钮进行调用。例如在 `Single` 主题下，其夜间模式切换方法为 `single.night()`

## 展现模式

- **静态**：只保留看板娘自身和文字提示，适合所有模型。
- **固定**：固定看板娘的位置，增加功能按钮，适合所有模型。
- **可移动**：看板娘的位置可以被用户更改，也保留了功能按钮，不适合半身模型。

## 隐藏看板娘

用于控制是否在移动设备上隐藏看板娘。可以改善部分低配设备的浏览性能，默认开启（即隐藏）。

## 时间小贴士

用于在指定时间展示对应的生活小贴士，如果开启将覆盖入站提示内容。

## 交互提示扩展

用于加载自定义提示内容，如果需要让看板娘增加和访客的互动，在这里编写 JSON 内容就可以实现。具体的参数可以

> 从 2.4 版本开始，自定内容选择器和本功能合并，自定内容选择器的文章提示功能可参考本文档的 [Custom](#Custom) 相关文档进行实现。

> 从 2.1 版本开始，插件内增加了检测功能，如插件配置选项留空将会自动进行补全。

具体参数及配置方法，请参考本文档内参数的 [Content](#Content) 节点


# 初始化参数

如果你不通过插件的形式食用，或是要在插件里实现一些高级功能，即可参考本节点，配置看板娘启动器。该参数在对象声明后，可通过 `prop` 参数来再次设置和修改。修改内容后，使用 [init](#重载) 方法重载看板娘或内容。

| 参数名 | 类型 | 是否必填 | 描述 |
| ----- | ---- | ------- | ---- |
| mode | `string` | 必填 | 展现模式：不同的模式有不同的交互效果 |
| hidden | `boolean` | 选填 | 隐藏看板娘：是否在手机上隐藏看板娘 |
| content | `object` | 必填，不启用也要保留结构 `{}` | 交互提示：配置交互提示扩展内容 |
| night | `string` 或 `function` | 选填 | 切换夜间模式：填写后将支持切换夜间模式 |
| model | `string[]` | 必填 | 需要加载的模型，支持多条 |
| tips | `boolean` | 选填 | 时间小贴士：小贴士启用后将替换入站信息 |

设置启动器必备参数的内容最全可以写成这样，当然你可以把这段复制下来自己研究和修改。

```javascript
var pio = new Paul_Pio({
    "mode": "static",
    "hidden": false,
    "content": {
        "welcome": "欢迎来到保罗的小窝"
    },
    "night": "single.night()",
    "model": ["static/pio/model.json"],
    "tips": true
});
```

## Mode

| 参数名 | 描述 |
| ----- | ---- |
| `static` | 静态：只保留看板娘自身和文字提示，适合所有模型 |
| `fixed` | 固定：固定看板娘的位置，增加功能按钮，适合所有模型 |
| `draggable` | 可移动：看板娘的位置可以被用户更改，也保留了功能按钮，不适合半身模型 |

## Hidden

默认为 `false`，如需在手机等移动设备上隐藏，请设置为 `true`。

## Content

提示内容一共有以下几个参数可以自行设置，均为选填。如不额外设置则降级为插件默认的提示文字，按照自己的需求填写即可覆盖默认设置。

> PS：如果 JSON 格式错误，将会导致该参数无效，插件加载失败并报错。可以通过使用网上的 JSON 格式化工具，检查自己编写的配置信息是否符合标准。

| 参数名 | 类型 | 描述 |
| ----- | ---- | ---- |
| welcome | `string` 或 `string[]` | 欢迎入站的信息 |
| touch | `string` 或 `string[]` | 点击~~触摸~~看板娘时随机提示的文字 |
| skin | `[string, string]` |鼠标移入切换皮肤 / 人物按钮时的提示文字|
| home | `string` 或 `string[]` |鼠标移入进入首页按钮的提示文字|
| close | `string` 或 `string[]` |鼠标移入关闭看板娘按钮的提示文字|
| link | `string` 或 `string[]` |关于按钮点击后跳转的链接|
| referer | `string` |当访客通过其他来源访问站点时的提示内容，`%t` 为来源网站（2.1 新增）|
| custom | `object` |自定义元素及提示（2.2 新增）|

这是一个较为齐全的示例，在不同主题下的设置会有所差异，仅供参考。具体的参数设置，请看下方的详细说明。

```json
{
    "welcome": ["你好，欢迎来到保罗的小窝", "我是从云，傲完就娇的从云~"],
    "touch": ["你这个绅士！", "别碰我！"],
    "skin": ["想看看我的新服装吗？", "新衣服真漂亮~"],
    "home": "点击这里回到首页！",
    "link": "https://paul.ren/about",
    "close": "QWQ 有缘再会吧~",
    "referer": "你通过 %t 来到了这里",
    "custom": [
        {
            "selector": ".comment-form",
            "text": ["欢迎参与本文评论，别发小广告噢~", "快来参加本文的评论吧~"]
        }
    ]
}
```

下面是各项参数的详细说明：

### Welcome

【2.1 版本及以上】允许字符串或数组，用于用户进站提示。不填本参数则为默认输出。

```json
默认："欢迎来到本站！"
示例："欢迎来到保罗的博客！"、["欢迎来到保罗的小窝", "我是从云，傲完就娇的从云~"] 或不填本参数。
```

【2.0 版本】只允许数组，用于用户进站提示。里面有两个项目，分别是直接进站和跳转入站的文字内容。其中 `%t` 是来源站点，第一项必填，不填则为默认输出。

```json
默认：["欢迎来到保罗的博客！", "欢迎来自 %t 的朋友！"]
示例：["欢迎来到保罗的博客！"]、["欢迎来到保罗的小窝", "我是从云，傲完就娇的从云~"] 或不填本参数。
```

### Touch

允许字符串或数组，填写点击看板娘的提示内容。不填本参数则为默认输出。

```json
默认：["你在干什么？", "再摸我就报警了！", "HENTAI!", "你够了喔！"]
示例："别碰我！"、["你在干什么？", "萝莉是什么呀"] 或不填。
```

### Skin

只允许数组，用于用户更换皮肤或模型。里面有两个项目，分别是点击更换的提示和更换完成后的提示。不填本参数则为默认输出。

```json
默认：["想看看我的新衣服吗？", "新衣服真漂亮~"]
示例：["要让我的朋友上阵吗？", "让她休息一会儿吧~"] 或 ["要让我的朋友上阵吗？"]
```

### Home

允许字符串或数组，填写点击返回首页按钮时看板娘的提示内容。不填本参数则为默认输出。

```json
默认："点击这里回到首页！"
示例：["点击这里回到首页！", "让我们回家吧！"]
```

### Close

允许字符串或数组，填写点击关闭看板娘按钮的提示内容。不填本参数则为默认输出。

```json
默认："QWQ 下次再见吧~"
示例：["Bye! ", "下次再见吧~"]
```

### Link

> 此功能在 2.1 版本中新增。

允许字符串，用于修改“关于”按钮的链接地址。不填本参数则为默认输出。

```json
默认："https://paugram.com/coding/add-poster-girl-with-plugin.html"
示例："https://paul.ren/about"
```

### Referer

> 此功能在 2.1 版本中新增。

允许字符串，用于修改其他来源进站的提示。不填本参数则为默认输出。

- `%t`：来源站点地址

```json
默认："欢迎来自 %t 的朋友！"
示例："Hi，欢迎你在 %t 的指引下来到这里~"
```

### Custom

> 此功能在 2.2 版本中新增，但 2.3 及后期版本的编写方式有所改变。本文档暂时只提供 2.4 版本的食用方法。

只允许数组，数组内包含一个 JS 对象，我把它称作为 **触发器**，用于扩展看板娘的自定义提示内容。当鼠标移入指定的元素，将提示对应的内容（`title` 或 `innerText`）。不填则不启用该功能。

| 参数名 | 类型 | 是否必填 | 描述 |
| ----- | ---- | ------- | ---- |
| selector | `string` | 必填 | 选择器：选择需要添加鼠标移入事件的元素选择器 |
| type | `string` |选填 `read` 或 `link` | 类型：分别用于首页文章链接和文章页链接，将会尝试获取 `title` 属性，否则获取 `innerText` 属性 |
| text | `string` |选填，未包含 `type` 时必填 | 文字：用于指定事件触发时，看板娘提示的文字内容 |

这是一段示例：

```json
{
    "selector": ".comment-form",
    "text": "欢迎参与本文评论，别发小广告噢~"
},
{
    "selector": ".home-social a:last-child",
    "text": "在这里可以了解博主的日常噢~"
}
```

> 如果你使用的是 2022/8/8 的最新开发版，选中的 DOM 元素若有 title，则输出 title，反之输出 innerText（元素里面的文字内容）

```json
{
    "type": "read",
    "selector": ".post-item a"
}
```

对应的 HTML 结构是这样的：

```html
<div class="post-item">
    <h2>
        <a href="https://paugram.com/coding/my-ecommerce-sku-add-algorithm.html" title="电商 SKU 算法">说说我那不靠谱但可用的电商产品 SKU 增改算法</a>
    </h2>
    <p>这是耗费了我好几天反复试错，最终实践的一种电商产品 SKU 增改算法，也许并不是特别优雅，但确实能正常使用。本文就大概讲下思路吧，我还给这个“算法”起了个名字，叫“阶梯查找法”。阅读本文大概需要...</p>
    <div class="post-meta">
        <time class="date">2022.06.01</time>
        <span class="category"><a href="https://paugram.com/coding">进击的码农</a></span>
        <span class="comments">8 °C</span>
    </div>
</div>
```

看板娘将会提示：**想阅读 “电商 SKU 算法” 吗？**

> 如果你想要编写一个适用于 Single 主题的文章链接触发器，可以参考如下示例：

```json
{
    "type": "read",
    "selector": ".post-item a"
}
```

对应的 HTML 结构是这样的：

```html
<div class="post-item">
    <h2>
        <a href="https://paugram.com/tech/problem-of-activex.html">不死的 ActiveX 又来搞事情了</a>
    </h2>
    <p>那天晚上，我亲戚突然问我电脑有没有 IE8，我就说我是 Win10 系统，只能尝试模拟。我猜肯定是他需要在某些市@政单位的网站上操作，结果遇到问题了询问我有没有什么解决方法。事情确实如此，他后面...</p>
    <div class="post-meta">
        <time class="date">2019.07.27</time>
        <span class="category"><a href="https://paugram.com/tech">做个技术宅</a></span>
        <span class="comments">4 °C</span>
    </div>
</div>
```

看板娘将会提示：**想阅读 “不死的 ActiveX 又来搞事情了” 吗？**

> 如果你想要编写一个适用于 Single 主题的文章链接触发器，可以参考如下示例：

```json
{
    "type": "link",
    "selector": ".post-content a"
}
```

对应的 HTML 结构是这样的：

```html
<article class="post-content">
    <p>你好，欢迎来到本小宇宙。这是一个记录生活、分享技术的个人博客。我叫保罗，是一个巨蟹座，会做点小前端、小设计的萌新码农... 本站主题是自己写的 <a href="https://github.com/Dreamer-Paul/Single" target="_blank">Single</a>，喜欢就 Star 支持一下吧~</p>
</article>
```

当鼠标移入文章的链接“Single”时，看板娘将会提示：**想了解一下 “Single” 吗？**

其他主题的使用方式由于结构差异，还请自行摸索！

## Night

只允许填入字符串，用于切换主题夜间模式（前提是主题提供了该方法）默认将使用 `eval()` 函数执行，不填则不启用该功能。

在 Single 主题下，只需要这样填写：

```javascript
night: "single.night()"
```

## Model

必填，只允许数组，用于引用模型 JSON 文件。不填本参数则无法开启看板娘。

```javascript
model: ["static/pio/model.json", "static/kia/model.json"]
```

## Tips

可选，填入 `true` 则启用时间小贴士，覆盖入站提示内容。默认为 `false`，不填则不启用该功能。

```javascript
tips: true
```

# 实例方法

## 重载

> 此功能在 2.1 版本中新增。

如果你的主题有 PJAX 功能，可使用以下方法重载本插件。重载后即可避免因在 PJAX 切换页面后，因 DOM 刷新导致看板娘显示异常的问题。

```javascript
var pio = new Paul_Pio({
    ...
});

pio.init();
```

| 参数名 | 类型 | 是否必填 | 描述 |
| ----- | ---- | ------ | ---- |
| noModel | `boolean` | 选填 | 为 `true` 时，仅刷新文字内容，不重新渲染看板娘模型 |

如使用 AJAX 插入了一个新元素后，执行下面的方法可仅刷新文字相关的功能，并重新为选择器指定的元素添加事件。

```javascript
var pio = new Paul_Pio({
    ...
});

pio.init(true);
```

## 说话

> 此功能暂未发板，请直接使用 `master` 分支的代码使用。

| 参数名 | 类型 | 是否必填 | 描述 |
| ----- | ---- | ------ | ---- |
| text | `string` | 必填 | 文本内容，如果设置 `options.html` 为 `true` 则输出 HTML（危险行为，需要注意）|
| options | `object` | 选填 | 额外配置项，可设置展示时长和 HTML 渲染模式 ⚠️ |

```javascript
var pio = new Paul_Pio({
    ...
});

// 看板娘提示一段普通文本
pio.message("保罗的小窝有动态更新啦");

// 看板娘提示一段 HTML 内容
pio.message(`保罗最近写了日记：<a href="https://paul.ren/note">全高应用在 Safari 上溢出的问题 / 跨域</a>，快前往阅读吧！`, { time: 10000, html: true });
```

### Options

可选属性一共有以下几个参数可以自行设置，均为选填。如不额外设置则降级为插件默认行为，按照自己的需求填写即可覆盖默认设置。

| 参数名 | 类型 | 是否必填 | 描述 |
| ----- | ---- | ------ | ---- |
| text | `string` | 选填 | 展示时长，默认为 `3000` 毫秒，也就是 3 秒钟 |
| html | `boolean` | 选填 | 输出 `text` 文本为 HTML 形式展示 ⚠️ |
