# .netCore-WPF_Designer
Workaround to use the designer in WPF Core App (.netCore WPF).

[CoreHiWPF](https://github.com/yanglr/.netCore-WPF_Designer/tree/master/CoreHiWPF): An executable WPF Core application project, need to open with Visual Studio 2019.



## Workaround to use the designer in WPF Core App


**Reference:**

[dotnet/samples - WPF Hello World sample with linked files](https://github.com/dotnet/samples/tree/master/wpf/HelloWorld-WithLinkedFiles)



## Install vs 2019 Professional/Enterprise version

Firstly, you need to Install vs 2019 Professional/Enterprise version. Then installing .net core 3.0 SDK is needed. Now you can try to create a .net core WPF application,

[![1555775855179](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/1555775855179.png)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/1555775855179.png)

After setting the relevant project name and storage path, it will pop up:

[![img2-BravoYeung](https://github.com/yanglr/.netCore-WinForms_Designer/raw/master/screenShots/p2.jpg)](https://github.com/yanglr/.netCore-WinForms_Designer/raw/master/screenShots/p2.jpg)

## Check "Use preview SDK" under .NET core in VS options

[![img3](https://github.com/yanglr/.netCore-WinForms_Designer/raw/master/screenShots/p3.jpg)](https://github.com/yanglr/.netCore-WinForms_Designer/blob/master/screenShots/p3.jpg)

After setting done, restart vs to take effect.



## Use VS build-in template, create WPF Project named "CoreHiWPF" of .net core



[![1555775855179](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/1555775855179.png)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/1555775855179.png)

[![1555775915106](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/1555775915106.png)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/1555775915106.png)

## Under the created solution, use VS build-in template to create new WPF project "HiWPF" of .net framework type



[![1555775957478](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/1555775957478.png)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/1555775957478.png)

[![1555775984667](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/1555775984667.png)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/1555775984667.png)

 



此时Solution中的文件目录为:

[![1555776045894](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/1555776045894.png)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/1555776045894.png)

## Update Assembly Name of .net core WPF "CoreHiWPF", make Assembly Names of two projects are the same

右键点击 .net core WPF项目 CoreHiWPF，选择最后的Properties, 然后将其Assembly Name 改为`HiWPF`.

[![1555773128801](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/1555773128801.png)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/1555773128801.png)

接着右键该项目，选"Edit CoreHiWPF.csproj"。

[![1555773253120](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/1555773253120.png)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/1555773253120.png)

按下图加入如下相应代码:

[![1555773381960](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/1555773381960.png)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/1555773381960.png)

```
  <ItemGroup>
    <ApplicationDefinition Include="..\HiWPF\App.xaml" Link="App.xaml">
      <Generator>MSBuild:Compile</Generator>
    </ApplicationDefinition>
    <Compile Include="..\HiWPF\App.xaml.cs" Link="App.xaml.cs" />
  </ItemGroup>

  <ItemGroup>
    <Page Include="..\HiWPF\MainWindow.xaml" Link="MainWindow.xaml">
      <Generator>MSBuild:Compile</Generator>
    </Page>
    <Compile Include="..\HiWPF\MainWindow.xaml.cs" Link="MainWindow.xaml.cs" />
  </ItemGroup>
```

## Ensure .net core WPF project CoreHiWPF is set as start up project

如果.net core WPF项目 CoreHiWPF 已经高亮，就不用管了。否则，需要选中项目 CoreHiWPF ，右击后选“Set As Start up project”.

## Try XAML Designer

此时关闭所有打开的文件，双击项目``HiWPF`中的`MainWindow.xaml`，就可以在XAML Designer中看到空白的WPF window了。

[![1555773860860](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/1555773860860.png)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/1555773860860.png)

## Modify the file MainWindow.xaml and related .cs if needed

接下来，我在`MainWindow.xaml`的`Grid`中加入了两行，一行放的是一个含有文本可换行的`Label`，另一行是`Exit`按钮。然后在Exit按钮上加入了`Click`事件，在`Window`上加入了`Loaded`事件。

[![modify](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/modify.gif)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/modify.gif)

代码改完之后，`F5`运行，最后的界面如下:

[![1555774408266](https://github.com/yanglr/.netCore-WPF_Designer/raw/master/screenShots/1555774408266.png)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/screenShots/1555774408266.png)

项目代码已推到`github`，欢迎`Fork`和`star`.

传送门: [.netCore-WPF_Designer](https://github.com/yanglr/.netCore-WPF_Designer) , 如果觉得自己配置起来麻烦，也可以 clone 下来自己体验一把喔~


**Reference：**

[dotnet/samples - WPF Hello World sample with linked files](https://github.com/dotnet/samples/tree/master/wpf/HelloWorld-WithLinkedFiles)

[ReadMe in Chinese (中文)](https://github.com/yanglr/.netCore-WPF_Designer/blob/master/ReadMe.zh-Hans.md)