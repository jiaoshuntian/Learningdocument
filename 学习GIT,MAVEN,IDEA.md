# GIT
### 1.GIT安装配置
1. git的下载地址为[http://git-scm.com/downloads](http://git-scm.com/downloads)
2. 配置个人用户名和邮箱  
``	
	$ git config --global user.name "jiaoshuntian"  
``
``  
	$ git config --global user.email 312199339@qq.com
``
### 2.工作区、暂存区、版本库
- **工作区：** 就是在电脑里能看到的目录
- **暂存区：** 英文叫stage, 或index。一般存放在"git目录"下的index文件（.git/index）中，所以我们把暂存区有时也叫作索引（index）。
- **版本库：** 工作区有一个隐藏目录.git，这个不算工作区，而是Git的版本库。

![](http://www.liaoxuefeng.com/files/attachments/001384907702917346729e9afbf4127b6dfbae9207af016000/0)

### 3.GIT基本操作
**1.选择一个合适的地方建一个空目录作为版本库**  
`$ mkdir learngit`  
`$ cd learngit`  
`$ pwd`  
pwd用于显示当前目录  
**2.把该目录作为仓库**  
`$ git init`  
**3.把文件添加到版本库**  
`$ git add readme.txt`  
`$ git commit -m "i wrote a new file"`  
注：-m后输入的是本次提交的说明，commit一次可以提交很多文件  
**4.查看仓库的状态、修改、历史记录、查看文件**  
`$ git status`  
`$ git diff`  
`$ git log`  
`$ git cat readme.txt`  
**5.版本回退**  
`$ git reset -- hard HEAD^` 回到上个版本  
`$ git reset -- hard HEAD^^` 回到上上个版本  
`$ git reset -- hard HEAD~100` 往上一百个版本  
`$ git reflog` 查看做过的每一条命令以便回退版本  
**6.撤销、删除**  
`$ git checkout -- readme.txt`丢弃工作区的修改（回到最近一次commit或add）  
`$ git reset HEAD readme.txt` 既可以回退版本，也可以把暂存区的修改回退到工作区  
`$ git rm readme.txt`  
**7.添加远程github仓库**  
第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有`id_rsa`(私钥) 和`id_rsa.pub`（公钥） 这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Git Bash，创建SSH Key：  
`$ ssh-keygen -t rsa -C "312199339@qq.com"`  
第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面：
然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容： 
![](https://raw.githubusercontent.com/jiaoshuntian/Learningdocument/073477175992b5b38c52b87e2e55a43f7083cd5a/SSH.png)
![](http://i.imgur.com/qypW6xi.png)  
第3步：在github上建立一个`learngit`仓库并在本地的`learngit`仓库下运行命令:  
`$ git remote add origin git@github.com:jiaoshuntian/learngit.git`
# Maven安装配置
### 1.下载
[http://maven.apache.org/download.cgi](http://maven.apache.org/download.cgi)  
下载完成后解压
### 2.配置Maven
右键“计算机”，选择“属性”，之后点击“高级系统设置”，点击“环境变量”，来设置环境变量，有以下系统变量需要配置：  
新建系统变量 MAVEN_HOME 变量值：D:\apache-maven-3.1.1  
编辑系统变量 Path 添加变量值：;%MAVEN_HOME%\bin
### 3.检验是否成功
用win键+R，来打开命令行提示符窗口，即Dos界面，输入mvn --version  若出现版本信息说明配置成功
![](http://i.imgur.com/TTF962u.png)
#intellij idea
###1.下载
[https://www.jetbrains.com/idea/download/#section=windows](https://www.jetbrains.com/idea/download/#section=windows)
###2.在IDEA中配置GIT  
1.选择菜单”File — Settings”，找到”Version Control — Git”，到Git的安装目录下的Git.exe执行文件所在地![](http://i.imgur.com/SwoBPsQ.png)
2.配置在Github上注册的账户![](http://i.imgur.com/j3Qh3wA.png)  
3.分享项目Github上：  
选择菜单”VCS — Import into Version Control — Share project on Github”。填写描述信息后，点击”Share”按钮即可。![](http://img2.tuicool.com/uYBj2y.jpg!web)  
4.获取Github项目：
选择菜单”VCS — Checkout from Version Control — Github”：![](http://img1.tuicool.com/JZJ3mm.jpg!web)  
等待一段时间的验证和登陆，在”Git Repository URL”下来列表中既有自己的项目，也有在Github网站上”Wacth”的项目，选择后，选择存放的路径，再输入项目名称，点击”Clone”按钮，即完成获取过程。  
5.提交自己的代码  
选中要提交的文件或文件夹，鼠标右键，Add
![](http://i.imgur.com/7b1pSx0.png)  
commit  
![](http://i.imgur.com/EF8M5Y7.png)  
提交信息要写!  
![](http://i.imgur.com/YX9VFEz.png) 
提交成功后PUSH到远程服务器  
![](http://i.imgur.com/ze0Okae.png)