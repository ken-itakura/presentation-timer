# 自我介绍计时器

[English](README.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [हिन्दी](README.hi.md) | [Español](README.es.md) | [Français](README.fr.md) | [العربية](README.ar.md) | [বাংলা](README.bn.md) | [Português](README.pt.md) | [Русский](README.ru.md) | [Bahasa Indonesia](README.id.md) | [Deutsch](README.de.md) | [한국어](README.ko.md) | [Türkçe](README.tr.md) | [Tiếng Việt](README.vi.md)

用于同学聚会等场合、让参加者依次自我介绍的单页计时器。只需在浏览器中打开 `index.html` 即可使用，无需安装、服务器或网络连接。

## 使用方法

1. 在浏览器（Safari / Chrome）中打开 `index.html`。
2. 在设置界面：导入 CSV（参见 `sample/participants.csv`，或点击“载入示例”）、逐人切换出席/缺席、按任意字段排序、设置标题 / 每人时间 / 称谓 / 语言，并试听音效。
3. 点击“进入计时”（同时启用声音）。
4. 进行计时：

| 操作 | 效果 |
|---|---|
| `Space` / 开始按钮 | 开始下一位发言（伴随掌声） |
| 点击右侧列表中的名字 | 从该人开始；排在其前面的人移入“已跳过” |
| 点击“已跳过”中的名字 | 开始该人的发言 |
| 取消“已跳过”中的“出席”勾选 | 确认后设为缺席并从列表移除（计时不会停止） |

剩 10 秒：每秒一声滴答 · 剩 3 秒：急促的哔哔声 · 0 秒：爆炸声并显示“时间到”标签。右上角显示总用时，右侧列出接下来的 10 位。

## CSV 格式

第一行为表头。自动识别 UTF-8 / Shift_JIS 编码。姓名和称谓列会根据表头（如 `姓名`、`称谓`）自动选择，也可在设置中更改。称谓单元格为空时使用默认称谓。

```csv
name,honorific,group,year
Alex Morgan,,A,2001
Sam Rivera,Dr.,B,2001
```

## 多语言

支持 16 种语言：在设置界面通过“语言”切换（首次使用浏览器语言，所选语言会被保存）。界面文字、标题默认值、默认称谓、示例数据和称谓位置（姓名前/后）随语言变化；阿拉伯语使用从右到左的布局。翻译尚未经母语者审校，可编辑 `index.html` 中的 `I18N` 来修正。添加语言时，在 `LANGS`、`I18N`、`SAMPLE_NAMES` 中各添加一项。

## 移动设备

支持手机竖屏和横屏布局。iPhone 开启静音开关时没有声音。通过“文件”应用打开文件最可靠；使用 GitHub Pages 发布后只需打开网址即可。

## 结构

```
.
├── index.html            # app (HTML / CSS / JavaScript in one file)
├── sample/
│   └── participants.csv  # sample list
├── README.md             # + README.<lang>.md (16 languages)
└── LICENSE               # MIT
```

`index.html` 包含全部内容：多语言词典、CSV 解析、设置界面、基于 Web Audio 的音效合成（无需音频文件）、计时逻辑（基于时间戳，不易漂移）和计时界面。设置和进度会自动保存到 `localStorage`。

许可证：[MIT](LICENSE)
