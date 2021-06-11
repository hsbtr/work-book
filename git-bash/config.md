### 运行配置  



`git config -l`；查看所有的(name.key)/(value) -l | --list

`git config -unset`；Remove the line matching the key from config file.

`git config -unset-all`：Remove all lines matching the key from config file.

`git config --global core.quotepath false`：解决 Windows Git Bash、Linux 下的中文转码问题；

`git config --global core.editor /usr/bin/vim`：[OS X 下 merge 命令 vi error 问题](http://tooky.co.uk/there-was-a-problem-with-the-editor-vi-git-on-mac-os-x/)；通常 core.editor=vim。

`git config --global credential.helper wincred`：Win Git Bash 启用 http/https 协议时设置。

`git config --global core.ignorecase false`
 设置大小写敏感，保持 Mac/Win/Linux一致性；在目录名大小写修改时，git可正常提交；



作者：michael_jia
链接：https://www.jianshu.com/p/f29ca723db4f
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。