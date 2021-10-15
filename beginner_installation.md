
## 安装Git
Mac自带xcode，在terminal中输入git完成安装，并在本地配置git

    git config --global user.name XXX
    git config --global user.email xxxxxx@xxx.com




## 安装软件包管理器Homebrew
最初按照以下方式安装后，进一步
错误提示：zsh: command not found: brew
试了好多办法都没解决，最后发现了这个！
解决方法：用以下命令安装，序列号选择中科大（1）的

    /bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"

来源：https://zhuanlan.zhihu.com/p/111014448