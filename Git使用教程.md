# Git

> 入门使用教程博客：https://blog.csdn.net/youzhouliu/article/details/78952453
>

> Linux回车换行：https://www.cnblogs.com/helloHKTK/p/7351946.html
>



## Git常用命令：

1. 查看用户名和邮箱：git config user.name/email

   修改：git config --global user.name "newusername"

   > https://blog.csdn.net/autoliuweijie/article/details/52230165

2. ​



1. git diff 文件名 ：查看文件修改的内容。
2. git log :查看最近提交日志；分行显示：git log --pretty=oneline




### git查看配置信息：

1. git config --global --list 查看用户信息

   > https://www.cnblogs.com/merray/p/6006411.html


### 创建版本库：

- 内容修改


- git add 文件名 ：添加到暂存区中

- git status：提交文件前，查看下文件状态

- git commit -m "提交信息" ：把文件提交到仓库

- git log：查看文件版本日志信息

  ![image](https://github.com/comeCU/testgit/raw/master/img/Git001.png)


    ![image](https://github.com/comeCU/testgit/raw/master/img/Git002.png)

### 版本回退：

- git log：显示版本日志；git log -pretty=oneline 分行显示


- git reset --hard HEAD^ :回退到上一个版本
- git reset --hard HEAD^^ :回退到上第二个版本，一次类推
- git reset --hard HEAD~100 :回退100 个版本




### 添加到暂存区，提交分支：

1. git add test.txt 将文件添加到暂存区
2. git commit -m "一次性提交所有文件，包括新建的test.txt文件"



### 撤销修改：

1. 未加到暂存区之前，直接使用：git checkout -- readme.txt
2. 已经使用git add放入暂存区后，在对文件做了修改后 **回到修改之前**：git checkout -- readme.txt



### 删除文件：

1. rm b.txt 可以直接在目录下删除掉或者使用rm b.txt
2. 此时文件已经在本地仓库中看不到了，但是可以用： git checkout -- b.txt 恢复文件
3. 只要没有commit之前，可以恢复版本库中的文件。




### 创建GitHub远程仓库：

1. 首先已经注册了GitHub账户
2. 在git bash命令行创建SSH Key ：ssh -keygen -t rsa -C "youremail@example.com" ,（如果已经创建则可以直接略过）。选择生成私钥和公钥的本地目录。
3. 登录GitHub打开settings中的SSH and GPG Keys页面，点击 “Add SSH Key” 粘贴本地公钥 .pub文件的内容。

### 本地添加到远程库：

1. GitHub中 选择“new repository”，填入仓库名，create。之后GitHub会给出提示。

2. 根据GitHub给吃的提示，将本地的testgit仓库推送到Github仓库：

   - git remote add origin https://github.com/comeCU/testgit.git

   - git push -u origin master

   - 弹出GitHub登录框，输入用户名密码登录。

     ![image](https://github.com/comeCU/testgit/raw/master/img/Git003.png)

   - 在Github查看版本库：

     ![image](https://github.com/comeCU/testgit/raw/master/img/Git004.png)

   - **注：**之后只要在本地作了提交，就可以：git push origin master

     将本地master分支的最新修改推送到GitHub上。

   ​

### 远程库克隆到本地：

1. GitHub中已经创建好了库

2. 使用命令：git clone https://github.com/comeCU/testgit2

   ![image](https://github.com/comeCU/testgit/raw/master/img/Git005.png)

3. 克隆别人的库只需将后面的用户名和库名**换成相应的即可**



### 新建、切换、查看分支：

1. 查看分支：git branch
2. 创建分支：git branch [name]
3. 切换分支：git checkout [name]
4. **创建并切换分支：git checkout -b [name]**
5. 合并某分支到当前分支：git merge [name]
6. 删除分支：git branch -d [name]



### 分支管理策略：

1. 通常合并分支时，git一般使用”Fast forward”模式，在这种模式下，删除分支后，会丢掉分支信息，现在我们来使用带参数 –no-ff来禁用”Fast forward”模式。
2. 创建一个dev分支。`git checkout -b dev`
3. 修改readme.txt内容。
4. 添加到暂存区。 `git add`


1. 切换回主分支(master)。`git checkout master`
2. 合并dev分支，使用命令 `git merge –no-ff  -m “注释” dev`
3. 查看历史记录: `git log --graph --pretty=oneline --abbrev-commit`




#### 冲突问题：

> https://www.cnblogs.com/startcaft/p/6639709.html

#### 1. 不会发生冲突：

- 现在master中修改test.txt文件，git add，git commit。
- 再新建分支newmaster，在该分支中修改test.txt文件，git add，git commit
- git checkout master到master分支，git merge newmaster 合并分支
- 不发生冲突
- git log --graph --pretty=oneline --abbrev-commit显示提交信息

#### 2.（详情查看链接） 



### master和rebase：

> https://www.cnblogs.com/kym/archive/2010/08/12/1797937.html



### 用Github做远程图床：

1. 在库中新建img文件夹
2. 链入图片路径更改为："!\[image\](https://github.com/comeCU/testgit/raw/master/img/Git00.png) "这种格式(注：image的括号需要进行转义‘\'，否则将无法正常的显示后面的路径字符串)。
3. 此方法可为typora设置图床！

