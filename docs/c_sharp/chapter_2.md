# 第二章：启动Minecraft！
下面给出伪代码：
``` csharp
public void LaunchMinecraft(String MaxMem,String VerName,String NickName,String JrePath)
{
  String mcPath=CurrentDir + "\\.minecraft"//得到.minecraft目录路径
  String natives=mcPath + "\\versions\\" + VerName + "\\" + VerName + "-natives";//得到natives目录路径
  String mcJar=mcPath + "\\versions\\" + VerName + "\\" + VerName + ".jar";//得到版本jar路径
  String jsonPath=mcPath + "\\versions\\" + VerName + "\\" + VerName + ".json";//得到json路径
  JSONArray libs=new JSONObject(ReadAllTextFromFile(jsonPath)).getJSONArray("libraries");//获得库的json数组
  String libjars="";//定义库列表字符串
  foreach(JSONObject libitem in libs.toJSONObjects())//遍历
  {
    String lnsuffix="";//后缀默认为空
    if(libitem.has("natives"))
    {
      lnsuffix="-"+libitem.getJSONObject("natives").get(System.getName());//获取系统名
    }
    String libpath=CurrentDir + "\\" + libname[0].Replace(".", "\\") + "\\" + libname[1] + "\\" + libname[2] + "\\" + libname[1] + "-" + libname[2] + lnsuffix + ".jar"//拼接库路径
    if(File.exists(libpath))//文件存在
    {
      if(libitem.has("extract"))
      {
        Unzip(libpath,natives);//解压natives，别忘了跳过META-INF文件夹
      }else{
        libjars+=libpath+";";//加入到库列表
      }
    }
  }
  libjars+=mcJar;//遍历完成后加入版本jar
  String minecraftArguments=new JSONObject(ReadAllTextFromFile(jsonPath)).get("minecraftArguments").replace("${auth_player_name}",NickName).replace("${version_name}",VersionName).replace("${game_directory}",mcPath).replace("${assets_root}",mcPath + "\assets").replace("${assets_index_name}",new JSONObject(ReadAllTextFromFile(jsonPath)).getJSONObject("assetIndex").get("id")).replace("${user_type}","Legacy");
  RunExecutableFile(JrePath+" -Xmx"+MaxMem+" -Dfml.ignoreInvalidMinecraftCertificates=true -Dfml.ignorePatchDiscrepancies=true -Djava.library.path="+natives+" -cp "+libjars+" "+new JSONObject(ReadAllTextFromFile(jsonPath)).get("mainClass")+" "+minecraftArguments);//运行游戏，我没加引号，记得如果有空格natives和libjars等含路径的变量都要加引号。
}
//其中，String ReadAllTextFromFile(String path)函数用于返回指定路径文本文件的全部文本内容，Unzip(String path,String dest)方法用于解压path指定的压缩文件到dest指定的目录，一般用Zip压缩算法即可。JSONObject.*和JSONArray.*指Json解析库提供的json对象的调用。
```

本文作者：[VEXLife](https://github.com/VEXLife)（贴吧ID：[VEXLife](https://tieba.baidu.com/home/main?un=VEXlife)）
