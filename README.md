
#gitskills

git技巧就不分享了，前面同学的笔记已经很完整了。

这里分享一个git可视化工具 git小乌龟-**TortioseGit**   用过svn的同学可能对小乌龟并不陌生，它是一个非常方便的辅助工具


安装步骤

1、安装 git for windows （git-xxx-bit.exe）

2、安装TortoiseGit，安装完成之后打开TortoiseGit。

![](http://github.com/a474516631/gitskills//raw/master/image/1.png)


tortoisegit使用方法

这里说下怎么在使用小乌龟时无需输入密码就提交项目 并且兼容bash方法

1、首先，在你的github首页设置项目的拉取方式为SSH（https好像是必须输入密码提交的）
![](http://github.com/a474516631/gitskills//raw/master/image/2.jpg)
2、在本地磁盘目录，点击 右键，选择 TortioseGit  在选择setting，进入设置界面
![](http://github.com/a474516631/gitskills//raw/master/image/6.png)
3、找到Git 下的remote（远端） 选择你的远程库 默认是叫origin 选择putty（ppk）
![](http://github.com/a474516631/gitskills//raw/master/image/7.png)
到这边就有俩种操作获取ppk文件

一种你可以直接用**小乌龟自带的puttygen 生成公钥 然后保存成ppk** ：

打开 TortioseGit安装目录 在./bin 下有一个puttygen.exe  打开它 点击 Generate   在进度条下空白区域随意移动鼠标 它会根据鼠标移动路径随机生成公钥 
![](http://github.com/a474516631/gitskills//raw/master/image/3.png)
![](http://github.com/a474516631/gitskills//raw/master/image/4.png)
 生成后点击Save public key 将钥匙保存起来 我的保存路径是C:UsersAdministrator.sshid_rsa.pub
 随后生成私钥
 点击Save private key 将钥匙保存起来 我的保存路径是C:UsersAdministrator.sshmykey.ppk
![](http://github.com/a474516631/gitskills//raw/master/image/9.png)
之所以保存成**id_rsa.pub** 这个名字是因为bash提交默认这个名字，**你改掉的话bash会找不到公钥**  

第二种操作就是**使用git bash 命令行**的方式 

打开C:UsersAdministrator.ssh  然后右键打开git bash Here  

输入 ssh-keygen -t rsa -C “aaaa@mail.com(替换成你github上邮箱)”

按3个回车，密码为空。

最后得到了两个文件：id_rsa和id_rsa.pub

然后打开 TortioseGit安装目录 在./bin 下有一个puttygen.exe ，打开它，**打开菜单栏conversation选择import key** 

选择id_rsa  不带pub后缀的那个 

点击Save public key 将钥匙保存起来 我的保存路径是**C:UsersAdministrator.sshid_rsa.pub**
随后生成私钥
点击Save private key 将钥匙保存起来 我的保存路径是**C:UsersAdministrator.sshmykey.ppk**



往事具备

ok！ 然后找到Git 下的remote（远端） 选择你的远程库 默认是叫origin 选择刚刚生成的**mykey.ppk**文件
点击应用

现在这些钥匙都有了  我们需要把钥匙放在github上了  

把刚刚生成的id_rsa.pub 文件内容复制下来

打开github.com

右边头像下settings 选择**SSH and GPG keys**

点击**New SSH key ** 按照你的喜好输入key name 

然后把**id_rsa.pub 文件内容粘贴上去**  保存
![](http://github.com/a474516631/gitskills//raw/master/image/11.png)
完成 试试使用TortioseGit提交吧
![](http://github.com/a474516631/gitskills//raw/master/image/10.png)

第一次参加学院课程  请多关照。。。

