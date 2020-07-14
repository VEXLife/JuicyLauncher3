# 第一章：搭建工作环境
如果您只是一名编程爱好者，建议您先玩一玩 Minecraft ，再来编写。

## 安装软件
要想制作启动器，我们就得有开发工具。这里，我使用Visual Studio 2017。当然，Express版也是没有问题的。这个教程中的示例使用Visual C#编写。[点此前往Visual Studio下载页面](http://www.visualstudio.com/zh-hans/downloads "访问Visual Studio官方网站以下载")

网页是中文，提供的安装文件是联机版安装器。

安装完Visual Studio，我们需要Java运行环境，请到[这里](https://java.com/zh_CN/download "访问Java官方网站以下载")选择合适的版本下载安装。

完成Java安装后，我们还需要选一个JSON解析库。对于不知道自己正在使用的编程语言有哪些JSON解析库的，您可以访问[json.org](https://www.json.org/json-zh.html)，在它的页面底部有大部分解析库的汇总。

## 设计用户界面
个人认为，这个启动按钮就不错。下方显示的信息可供用户核验。
<style>
.launchbtn {
  display: inline-block;
  border-radius: 2px;
  border: none;
  background-color: #0066ff;
  color: #FFFFFF;
  text-align: center;
  font-size: 36px;
  padding: 30px 3px 0px 0px;
  width: 350px;
  transition: all 0.3s cubic-bezier(0.6, 0.3, 0.4, 0.7);
  cursor: pointer;
  box-shadow: 0px 2px 6px #000000;
  line-height: 20px;
}
.launchbtn span{
  cursor: pointer;
  position: relative;
  right: 0;
  transition: all 0.3s cubic-bezier(0.6, 0.3, 0.4, 0.7);
}
.launchbtn span i{
  cursor: pointer;
  position: relative;
  left: 10px;
  font-size: 40px;
  transition: all 0.3s cubic-bezier(0.6, 0.3, 0.4, 0.7);
}
.launchbtn:hover{
  background-color: #00ccff;
  box-shadow: 0px 2px 10px #000000;
}
.launchbtn:hover span{
  right: 5px;
}
.launchbtn:hover span i{
  left: 20px;
}
.launchbtn:active{
  background-color: #0055ff;
  box-shadow: 0px 2px 4px #000000;
  transform: scale(0.98);
}
</style>
<button class='launchbtn'><span>启动Minecraft<i class='fa fa-angle-right'></i></span><br><font size=2>版本：未选择&nbsp;&nbsp;&nbsp;游戏名字：User</font></button>

其它部分设计得尽量美观一点（不要学我），提供一个版本选择的空间、游戏名字的控件、“启动”按钮（你要是想把它改成“开始游戏”“启动Minecraft”“点击进入”之类的话我也不拦你）、“设置”按钮，具体怎么布局自由发挥，可以用XAML和各种做好的控件库，反正你自己觉得开心就好。如果去掉了窗体边框，请加上拖动功能，并提供关闭按钮。

## 初始化启动器设置
用户第一次运行时，我们必须为用户提供一些基本的默认配置来简化使用。在程序启动时如果没有配置文件，则认为是第一次启动，创建默认的配置文件。版本部分可以留空，还应创建好.minecraft文件夹，并将其作为游戏根目录。默认的Java虚拟机参数应调整为：
``` bash
-Dfml.ignoreInvalidMinecraftCertificates=true -Dfml.ignorePatchDiscrepancies=true
```
如果有，则在每次窗体引发Load事件时读取和载入配置。

### 自动寻找Java
默认Java路径通过读取注册表HKEY_LOCAL_MACHINE\SOFTWARE\JavaSoft\Java Runtime Environment\<第一个版本名称，如1.8.0_144>下的JavaHome键值并拼接"\bin\javaw.exe"得到。注意**有JRE和JDK两种以及32位和64位的问题**，其对应的路径都是不同的，我们都要顾及到。

### 保存设置
无论是何种情况窗体被关闭，都应将选择的版本和用户名存入配置文件中。

本文作者：Author0
