# latexdiff的使用和配置


## latexdiff的使用
**latexdiff** 可以对Latex文档中所作的修改进行高亮显示。

用法为在tex文件所在的目录下使用`latexdiff origin.tex modify.tex > diff.tex`命令。其中**origin**,**modify**和**diff**分别指改动前的文件，改动后的文件和使用 latexdiff 命令后生成的文件，相关文件名还请根据实际情况作出修改。命令执行完后会在tex目录下生成一个名为**diff.tex**的文件，打开编译即可。( Tips:在tex目录下`shift`+`鼠标右键`即可调出含有cmd/powershell选项的下拉选框 )。
![Res](https://raw.githubusercontent.com/wtligit/pic/master/latexdiff/Res.png)

但是latexdiff的使用往往不是一帆风顺的，有几个经常遇到的问题，如：
1，**>**符号前忘记加空格
2，生成的tex文件在编译的时候，标题处喜欢报错，删除之
3，生成的tex文件总是报**Missing \begin{document}**错误，新建个文件把内容都拷贝进去，再编译即可
4，**latexdiff：The Perl script could not be found**，下文详述


## The Perl script could not be found的解决方案
1，如果你在命令行输入`latexdiff`后，输出不是如下图所示，说明你需要安装latexdiff与Perl。

![latexdiff](https://raw.githubusercontent.com/wtligit/pic/master/latexdiff/commandTrue.png)

2，安装latexdiff
    使用**Package Manager(Admin)**来安装，一般可以在 开始菜单\CTeX\MiKTeX\Maintenance(Admin)找到，之后搜索latexdiff，点击左上角的加号安装（如果只有减号可以点说明 latexdiff 已经装上了）。
    
![manager](https://raw.githubusercontent.com/wtligit/pic/master/latexdiff/manager.png)

3，安装Perl
    在 http://www.perl.org/get.html 安装对应版本，Win下有两个版本，应该是都可以的，本文安装的 ActiveState Perl。
    
4，编辑环境变量
    为了在任何位置都能使用latexdiff，我们将Ctex的miktex和Perl的bin目录写进系统变量Path中，比如笔者的路径为：C:\CTEX\MiKTeX\miktex\bin 和 C:\Perl64\bin
    
5，完成上述步骤后，在命令行中输入`latexdiff`，如果输出如步骤1中图示，那么恭喜你，你已经可以使用`latexdiff`了，如果提示：

latexdiff: The Perl script could not be found.  
latexdiff: Data: scripts/latexdiff/perl/latexdiff.pl

别着急，请继续往下看！

6，上面的报错提示是说在所在目录下找不到要用的latexdiff.pl，那么我们顺着这个目录进入scripts/latexdiff会发现在该目录下有一系列以latexdiff开头的没有后缀的文件，而并没有Perl这个文件夹（或者这个文件夹内什么都没有）。创建这个文件夹，把所有以latexdiff开头的文件复制进Perl文件夹，然后给它们都加上`.pl`的后缀。
当然也可以在 [Ctan]https://www.ctan.org/tex-archive/support/latexdiff 网站下载latexdiff前缀的文件放到Perl中,或者在我的[Github](https://github.com/wtligit/latexdiff-Instructions-Configuration/tree/master/perl)里直接下载。
两种方法都可以，我们的目的就是让latexdiff可以在正确的位置存在并被找到。

7，此时在命令行输入`latexdiff`，如果输出如步骤1中图示，那么恭喜你，你已经可以使用`latexdiff`了，如果依然提示找不到 latexdiff.pl ,请在 开始菜单\CTeX\MiKTeX\Maintenance(Admin) 中找到**Setting(Admin)**,然后更新`FNDB`。
![FNDB](https://raw.githubusercontent.com/wtligit/pic/master/latexdiff/FNDB.png)




