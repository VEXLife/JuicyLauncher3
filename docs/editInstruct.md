# 教程编写合作说明
将您的文章（Markdown形式）以Pull Request的形式上传[此GitHub仓库](https://github.com/VEXLife/JuicyLauncher3)即可。为保护您的成果不受侵犯，建议您在您的文章的末尾标注您的ID，并在此页将自己的名字加入到参与编写人员名单中。如果有的话，也请提供您的百度贴吧ID便于联系。

<Note type=warning>
  参与教程编写活动即视为<b>您同意遵守<a href="#/rules">教程编写合作者守则</a></b>。
</Note>

## 关键词
这个教程文档使用**扩展插件程序**替换关键词以便于维护。

### 术语
如果某个术语出现频繁，您可以将它设为关键词。在[index.html](https://github.com/VEXLife/JuicyLauncher3/blob/master/docs/index.html)中，您会看到这样的代码：
``` javascript {highlight: [5,6,7]}
const keyWords = {
    name: 'keyWords',
    extend(api) {
        api.processMarkdown(text => {
            return text
                .replace(/…/g, '<a href="…" title="…">…</a>')
                //…
        });
    }
}
```
编辑高亮的代码部分即可，比如Term这个术语，只需添加一行
``` javascript
.replace(/ Term /g, '<a href="<描述Term这个术语的网站>" title="了解Term">Term\n<external-link-icon /></a>')
```
就好。
<Note type=tip>
  建议您像上面那样在待替换的关键词周围加上空格，以免误将代码中的内容识别。
</Note>
目前，已支持的术语如下所示，请在编撰过程中遇到这些术语时在其周围添加空格以使其能被识别。

*  Minecraft 
*  Forge 
*  LiteLoader 
*  OptiFine 

### 署名
同上，您应当在文末的“本文作者”部分使用“Author<编号>”，然后在关键词中添加像这样的代码：
``` javascript
.replace(/Author<编号>/g, '<a href="https://github.com/<您的GitHub ID>">您的GitHub ID</a>（您常用的论坛平台名：<a href="<您在该平台的个人主页链接>">您在该平台的ID</a>）')
```
这样，当您的ID或个人主页变更时，您只需改动一处即可。

## 表情
表情可增添文字的趣味性。我们为您提供了相应的控件，您可以引用它们，便于我们维护。

### 滑稽
若要贴子好，滑稽少不了。作为贴吧文化的重要元素，滑稽怎么能缺席呢？插入下面的代码，即可得到一只可可爱爱的小滑稽（基于SVG的矢量图）<XieYanXiao />。
``` html
<XieYanXiao />
```
与此同时，我们也为您提供贴吧原版滑稽（非矢量图），您只需改用下面的代码，即得到<HuaJi />。
``` html
<HuaJi />
```

## 正在编写的内容
为了防止出现多名编写者编写了冲突的内容，导致部分编写者的劳动遭到浪费的现象，下面列出了当前已被认领的编写内容。请您在开始编写前检查您要写的内容是否已有人认领，如果没有，请添加，并附上您自己的联系方式。在您完成或感到精力、时间不足时，您可以删除您的记录来开放给其他作者自由编辑。

<Note type=warning>
  请注意，如果内容冲突，我们会优先保留认领者贡献的内容。
</Note>

| 认领的章节 | 认领者 |
| :-: | :-: |
| C\#部分 | Author0 |

本文作者：Author0
