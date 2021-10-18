
## 安装Git并连接GitHub<br>
Mac自带xcode，在terminal中输入git后按指引完成安装，并在本地配置git：

    git config --global user.name XXX
    git config --global user.email xxxxxx@xxx.com

查看配置情况

    git config user.name
    git config user.email

创建SSH用于连接Github，如果使用多台电脑，每台都要创建。在profile里可以查看SSH相关内容，包含创建方法。

    ssh-keygen -t ed25519 -C "your_email@example.com"

然后一直按回车键直到SSH key生成完毕，用以下命令查看密钥并复制，填写到Github的https://github.com/settings/keys里：

    cat ~/.ssh/id_rsa.pub

做到这步就可以在去Github创建repository（仓库）并clone到本地。[url]可以是HTTPS或SSH，点击仓库的<span style="background-color: #E1FFD4"> Code </span>按钮查看

    git clone [url]

或者将本地项目同步到GitHub远程仓库。[参考](https://www.jianshu.com/p/7c836f2d5c66) <br>
在本地项目文件夹下打开终端：

    git init //初始化git仓库
    git add . //把所有项目文件添加到提交暂存区
    git add [file] //添加某文件，e.g., git add readme.md
    git commit -m '说明本次提交的内容' //把暂存区中的内容提交到仓库
    git remote add origin git@github.com:[githubUerName]/[resName] //关联本地仓库和远程仓库
    git push -u origin master //把本地仓库内容push到远程仓库的master分支

push的-u参数是设置本地仓库默认的upstream,即把本地仓库同远程仓库的master分支进行关联。<br>
pull时不带参数也默认从master分支拉取。<br>
如果git remote add origin xxxx时报错remote origin already exists，删除后重试

    git remote rm origin //删除origin



    
<br>
<br>
<br>

## 安装工作软件提升快乐<br>

工欲善其事，必先利其器，这些软件能让后续操作更加便利愉快 ~
1. 代码编辑器：[Visual Studio Code](https://code.visualstudio.com/)
2. 终端：[iTerm2](https://www.iterm2.com/downloads.html)
3. 命令行工具：[Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh)

1和2可直接下载安装，so easy。同事小伙伴说2和3对初学者并不是必要的，但我看他的终端太好看了就自己去下载了！<br>
安装Oh My Zsh：

    sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

将Mac的默认Shell设置为zsh。[参考](https://www.jianshu.com/p/8d822ce0d425)

    chsh -s /bin/zsh

完成后，就可以去更改主题拥有fancy的终端了！在~/.zshrc文件中修改ZSH_THEME，具体请看[参考1](https://www.jianshu.com/p/a91b8d75a6d7)，[参考2](https://www.jianshu.com/p/53eb1075f627)

    vim ~/.zshrc

>在vim里修改文件，要先按 i 进入编辑模式，修改完成之后按 esc退出编辑模式，最后 shift+zz 保存并退出

<small>P.S. 我还没用用最经典的agnoster主题，因为稍微有点麻烦，回头再说👀</small>
<br>
<br>
<br>

## 安装Homebrew,node.js<br>
Homebrew是软件包管理器，有了它安装配置软件会很便利。<br>我在安装docsify的时候第一次遇到nmp(理所当然安装失败），所以才有了以下内容的学习。<br>
最初我是这样安装homebrew的

    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

结果后续安装node的时候错误提示zsh: command not found: brew
试了好多办法都没解决，最后发现了这个！（序列号选择中科大（1））[来源在这里，大感谢！](https://zhuanlan.zhihu.com/p/111014448)

    /bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"

<br>

接下来安装node.js, 3种方法 [参考](https://www.cnblogs.com/tristers/p/12171714.html)
- [下载nodejs](http://nodejs.cn/download/)
- 用brew安装nodejs
  - 运行以下命令：<br>
    brew install nodejs
- 用yarn安装nodejs<br>
  - 安装yarn：<br>curl --silent --location https://rpm.nodesource.com/setup_8.x | sudo bash -<br>
  - 安装nodejs：<br>sudo yum install -y nodejs

检查安装是否成功<br>
node-v<br>
npm -v
<br>
<br>
<br>
<h4> node.js、nvm和npm的关系 </h4>

- nvm：nodejs 版本管理工具
  - 一个 nvm 可以管理多个 node 版本和 npm 版本。
  - 注意：一个node版本对应一个npm版本。
- npm：nodejs 包管理工具
  - 在安装nodejs 的时候，npm 也会跟着一起安装，它是包管理工具，npm管理 nodejs中的第三方插件。
- cnpm：国内淘宝镜像
  - 因为npm的服务器位于国外可能会影响安装。淘宝镜像与官方同步频率目前为 10分钟 一次以保证尽量与官方服务同步。
[来源](https://juejin.cn/post/6844904127802114055)<br>

nvm我还没装

<br>
<br>

## 出现的问题及解决方法

[/usr/local/include/node is not writable](https://www.coder.work/article/1382901)<br>
[There is no tracking information for the current branch](https://cloud.tencent.com/developer/article/1654369)<br>
[pathspec 'master' did not match any file(s) known to git](https://www.cnblogs.com/superjishere/p/11602532.html)<br>
⭐️ [HEAD 游离](https://blog.csdn.net/u011240877/article/details/76273335) , [HEAD detached at](https://www.jefsky.com/archives/186.html)<br>
[Please enter a commit message to explain why this merge is necessary](https://www.jianshu.com/p/ec9ff05976cc)<br>
[The current branch main has no upstream branch](https://blog.csdn.net/benben_2015/article/details/78803753)




## 用docsify建博客
[docsify](https://docsify.js.org/#/)


## 有用的网站们<br>
[Github Docs 官方 中英文](https://docs.github.com/cn)<br>
[Github常用命令备忘单](https://training.github.com/downloads/zh_CN/github-git-cheat-sheet/)<br>
[emoji百科全书](https://emojipedia.org/)<br>
[Godaddy买域名](https://www.godaddy.com/)


👻👻👻👻👻👻