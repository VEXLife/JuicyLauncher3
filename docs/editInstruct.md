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
.replace(/ Term /g, '<a href="<描述Term这个术语的网站>" title="了解Term">Term</a>')
```
就好。
<Note type=tip>
  建议您像上面那样在待替换的关键词周围加上空格，以免误将代码中的内容识别。
</Note>

### 署名
同上，您应当在文末的“本文作者”部分使用“Author<编号>”，然后在关键词中添加像这样的代码：
``` javascript
.replace(/Author<编号>/g, '<a href="https://github.com/<您的GitHub ID>">您的GitHub ID</a>（您常用的论坛平台名：<a href="<您在该平台的个人主页链接>">您在该平台的ID</a>）')
```
这样，当您的ID或个人主页变更时，您只需改动一处即可。

本文作者：Author0
