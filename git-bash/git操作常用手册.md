### Git常规提交流程：  

#### 初始化版本库

注： vue脚手架会默认初始化版本库  

```bash
git init
```

#### 创建用户名及邮箱

注： 不加`--global`即是当前项目创建

```bash
git config --global user.name "张三"

git config --global user.email "123456@qq.com"
```

#### 将文件放入暂存区  

注：如果add后面写的是文件名，即是将指定文件放入暂存区，` .`号即是提交除忽略规则中的所有文件，提交后建议查看状态，忽略规则文件请看  [忽略规则文件](#git)

```bash
 git add .
```



#### 查看状态  

```bash
git status
```



#### 进入归档区  
可以进行跟踪，建议查看状态

```bash
gei commit -m "第一次提交"
```



#### 创建远程库源地址  

origin远程源地址名, 可自定义;

```bash
git remote add origin 远程地址链接
```

#### 提交代码到远程源  

第一次提交要加 `-u` ， 有多个分支要加分支名，不写默认master主分支;

```bash
git push -u origin master
```



### 操作远程源地址  
注：根据需要操作  
#### 显示所有远程源  

```bash
git remote -v
```


#### 删除远程源
```bash
git remote rm origin
```



#### 修改远程源

```bash
git remote set-url origin 远程仓库链接
```



#### 添加远程源  
注：新增远程源不要重名

```bash
git remote add origin 远程地址链接
```



#### 显示某个远程仓库的信息  

```bash
git remote show origin
```



### 分支管理
#### 查询本地分支

```bash
git branch
```

#### 创建一个本地分支
创建名为rec的分支

```bash
git branch rec
```

#### 切换分支  
切换到rec分支
注：checkout 根据后缀文件不同功能不同

```bash
git checkout rec
```

#### 合并分支
将rec分支合并到master分支
注：必须要在主分支上

```bash
git merge rec
```

#### 删除分支
删除rec分支

```bash
git branch -d rec
```

#### 查看本地分支  
注：此方法会列出所有远程跟踪分支和本地分支

```bash
git branch -a
```

#### 查看远程分支  
注：如果加上`-d`则是删除远程分支

```bash
git branch -r
```

#### 关联本地分支与远程分支  
将本地分支`muscleape`关联到远程分支`muscleape`上  

```bash
git branch --set-upstream-to=origin/muscleape
```

#### 查看本地分支和远程分支的映射关系  

```bash
git branch -vv
```

#### 查看本地各个分支目前最新的提交  

```bash
git branch -v
```

#### 推送本地分支到远程  

```bash
git push origin A:A
```

#### 删除远程分支  
注：用本地分支名，前面不加origin  

```bash
git push origin -d A 
```

#### 创建分支并且进入  
```bash
git checkout -b a
```

#### 推送所有分支到远程仓库  
```bash
git push origin --all
```

#### 分支重命名

`oldname` 旧分支名 

`newname` 新的分支名

```bash
git branch -m oldname newname
```

注： 修改分支名后，需要将此分支推动到远程源上并且删除远程源的旧分支

```bash
git push origin newname
git push origin -d oldname
```



#### 强行推送  

注：即使本地与远程仓库分支有冲突，也会忽略强行提交，容易造成代码丢失，谨慎使用  
```bash
git push origin --force
```

#### 删除无用的远程分支跟踪  

列出仍在远程跟踪但是远程已被删除的远程分支

```bash
git remote prune origin --dry-run
```

清除上面命令列出来分支的远程跟踪  

```bash
git remote  prune origin
```





### 本地仓库管理  

#### 查看状态  
```bash
git status
```

#### 详细显示信息  
```bash
git log 
```

#### 显示详细信息  
```bash
git log --oneline
```

#### 回滚指定版本号  
注：版本号可以用 git log 查询  
```bash
git reset --hard b2691b4 
```

#### 将当前版本回退到上一个版本  
```bash
git reset --hard HEAD^
```

#### 回退到上两个版本  
```bash
git reset – hard HEAD^^
```

#### 回退一个步骤  
注：可以配合 `git checkout index.js`把已经进去暂存区的文件 返回到上次修改的状态  
```bash
git reset HEAD index.
```

#### 查询某个文件的代码  
```bash
cat index.js 
```

#### 查看被修改了什么  
```bash
git diff index.js
```

#### 撤销上次的修改（工作区）  
```bash
git checkout index.js
```

#### 把存入暂存区的某个文件丢回工作区  
```bash
git rm --cached index.js
```

#### 跟踪取消  
即把文件从git中拿出来，不再进行版本跟踪，但保留工作区的文件
```bash
git rm - - cached filename
```

#### 查看命令历史
```bash
git reflog
```

#### 修改commit注释信息  

在为push的情况下修改commit注释信息

```bash
git commit --amend
```

进入vim界面，i 键进入编辑模式，输入完`esc`键退出输入`：wq`  



### 远程库更新本地库  

#### 克隆远程库  
```bash
git clone 远程库链接
```

#### fetch远程更新  
##### 拉取远程  
第一步，从远程库更新到本地，源与分支名根据自己的情况更改，没有此分支，命令会自动创建此分支  
```bash
git fetch origin master
```

##### 比较  
第二步，比较本地的仓库和远程参考的区别  
```bash
git log -p master.. origin/master
```

##### 合并  
第三步，把远程下载下来的代码合并到本地仓库，远程的和本地的合并  
```bash
git merge origin/master
```

#### fetch本地分支  
##### 拉取代码并新建本地分支  
第一步，从远程的origin仓库的master分支下载到本地并新建一个分支temp  
```bash
git fetch origin master:temp
```

##### diff比较两个分支差异  
第二步，比较master分支和temp分支的不同  
```bash
git diff temp
```

##### 合并  
第三步，合并temp分支到master分支  
```bash
git merge temp
```

##### 删除分支
第四步，删除temp
```bash
git branch -d temp
```

#### pull方法  
注：pull会直接与指定的分支进行合并，没有指定默认是master
```bash
git pull origin
```

#### 问题记录  
远程库新建后有md文档，本地提交时会提示远程库与本地库有不同，不予提交，
解决方案  带上参数 --allow-unrelated-histories   含义 说明为什么要合并 
git pull origin master --allow-unrelated-histories



### 文件和目录操作命令

#### 创建文件夹  

`mkdir` 命令用来建立新的目录；

创建一个名为test的文件夹

```bash
mkdir test
```

#### 删除文件夹

`rmdir`用来删除已建立的目录；

```bash
rmdir test
```

#### 进入test文件夹

`cd` 这个命令是用来进出目录的, `cd` 如果直接输入 cd 后面不加任何东西会回到当前根目录，

注： 如想查看更多命令请自行搜索linux命令

```bash
cd test
```

#### 在test文件夹里创建名为`.gitignore`文件  

```bash
touch .gitignore
```

####  查看当前目录文件  

`ls` 显示一般文件名,`ls`有三个参数分别是 

`-a`  除了显示一般文件名外 连隐藏文件也会显示出来

`-l`  这个命令可以使用长格式显示文件内容 如果需要察看更详细的文件资料就要用到` ls -l` 这个指令,注： 这个参数是字母 L 的小写不是数字 1

`-f`  在列出的文件 目录 名称后加一符号 例如可执行文件加 "*", 目录则加 "/"

```bash
ls
ls -a
ls -l
ls -f
```

#### 复制文件  

`cp` 这个命令相当于 dos 下面的 copy 命令，有一个参数，`r` 参数 `r` 是指连同源文件中的子目录一同拷贝；

`cp –r` 源文件(source) 目的文件(target) 

```bash
cp -r test test3
```

注： test3目录必须存在，以上是同级目录操作，如果需要向上级目录复制，如下

```bash
cp -r test ../test3
```

#### 删除文件  

`rm`  这个命令是用来删除文件的 `rm` 命令常用的参数有三个`-i`,`-r`,`-f`

比如我现在要删除一个名字为 text 的一个文件 输入如下命令:

```bash
rm -i text
```

系统会询问我们是否要删除 text 文件 敲了 y/n 确认是否要删除 text 文件

```bash
rm -r text
```

这个操作可以连同这个目录下面的子目录都删除, 功能比上面讲到的 rmdir 更强大, 不仅可能删除指定的目录 而且可以删除该目录下所有文件和子目录;

```bash
rm -f text
```

这个操作可以不经确认强制删除文件



###  vim常用命令操作  

Vim 有三种基本工作模式：命令行模式 文本输入模式和末行模式

注： `vim` 可简写为 `vi`

#### 常用命令

进入文件

```bash
vim .gitignore
```

插入文本

进入后直接按下`i`键光标在首行即可编辑

编辑完成退出文本模式，进入末行模式，按下`esc`键，输入`:`（英文冒号）加上`wq` 回车

```ba
:wq
```

注： `:wq` 代表保存后退出



#### 命令行模式  

任何时候 不管用户处于何种模式 只要按一下 ESC 键 即可使 `vim` 进入命令行模式 当在 shell 或 bash cmd  环境下输入 `vim` 命令启动 `vim` 编辑器时 也是处于该模式下

##### vim进入与退出

在 shell 模式下 键入 `vim` 及需要编辑的文件名 即可进入 `vim` 例如:

```bash
vim .gitignore
```

即可编辑 `.gitignore` 文件, 如果该文件存在, 则编辑界面中会显示该文件的内容, 并将光标定位在文件的第一行, 如果文件不存在, 则编辑界面中无任何内容,  如果需要在进入 vim 编辑界面后 将光标置于文件的第 n 行, 则在 `vim`命令后面加上 `+n` 参数即可 例如需要从 `.gitignore` 文件的第 5 行开始显示, 则使用如下命令:

```bash
vim +5 .gitignore
```

退出 `vim` 时, 需要在末行模式中输入退出命令 `q `如果在文本输入模式下首先按 `ESC` 键进入命令模式 然后输入 `: `进入末行模式 在末行模式下, 可使用如下退出命令

`:q`   直接退出 如果在文本输入模式下修改了文档内容 则不能退出。

`:wq`  保存后退出

`:x`    同 `wq`

`:q!`  不保存内容 强制退出

##### vim显示行号  

在末行模式下 输入如下命令

```bash
set number
```

以上命令可使·`vi` 在编辑界面中显示行号

此外, 在末行模式下 可使用如下 `nu `命令 `number` 的简写,  来显示光标所在行的行号及该行的内容;



<div id="git"></div>

### 忽略规则文件

#### 创建忽略跟踪文件  

```bash
touch .gitignore
```

#### 编辑文件
用vim进入忽略文件，i键进入插入模式，写入忽略文件规则，完成后esc键退出插入模式，英文输入:wq回车

```bash
vim .gitignore
```

注：
`.gitignore`只能忽略那些原来没有被track的文件，如果某些文件已经被纳入了版本管理中，则修改`.gitignore`是无效的。
解决方法就是先把本地缓存删除（改变成未track状态），然后再提交

```bash
git rm -r --cached .
git add .
git commit -m 'update .gitignore'
```


#### 语法  
注： 空格不匹配任意文件，可作为分隔符，可用反斜杠转义  

 `#`  开头的文件标识注释，可以使用反斜杠进行转义  

`!`   开头的模式标识否定，该文件将会再次被包含，如果排除了该文件的父级目录，则使用 ! 也不会再次被包含。可以使用反行转义  

`/`    结束的模式只匹配文件夹以及在该文件夹路径下的内容，但是不匹配该文件  
`/`    开始的模式匹配项目跟目录，如果一个模式不包含斜杠，则它匹配相对于当前` .gitignore `文件路径的内容，如果该模式不在 `.gitignore` 文件中，则相对于项目根目录  
`**`   匹配多级目录，可在开始，中间，结束  
`?`    通用匹配单个字符  
`[]`   通用匹配单个字符列表  


### git bash 中文乱码问题
windows系统git 中文编码是gdk  
解决方案 依次执行以下命令  

```bash
git config --global gui.encoding utf-8
git config --global i18n.commitencoding utf-8
git config --global i18n.logoutputencoding utf-8
export LESSCHARSET=utf-8


```

