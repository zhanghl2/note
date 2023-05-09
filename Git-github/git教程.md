**Git 基础入门**

**一、安装与配置**

**1.下载与安装:**

https://git-scm.com/download/

**2.使用入口**

win：右键菜单—git bash

mac：终端窗口

**3.基础配置**

a.首次使用添加身份说明，使用以下两个命令：

$ git config --global user.name "你的昵称"

$ git config --global user.email 邮箱@example.com

b.创建仓库

① 在项目文件夹下使用 git bash 输入$git init

② 使用他人项目创建仓库

02:30

$git clone 项目 url

**二、状态与提交版本**

1.跟踪

a.跟踪文件

$ git add <name>

b.跟踪当前目录

$ git add .

2.取消跟踪

a.rm 删除

$ git rm <name>

b.保留但不跟踪

$ git rm-cache <name>

3.文件状态修改

03:37

![](https://i0.hdslb.com/bfs/note/4f936ee8c91ba81ce721fb2d61e200ff9e14d119.png@818w_!web-note.webp)

a.将修改文件缓存

git add <file-name>

![](https://i0.hdslb.com/bfs/note/721755daf3184c8c3ac92c864a62bc6d5ab6d67d.png@1058w_!web-note.webp)

b.取消缓存

git reset HEAD <name>

![](https://i0.hdslb.com/bfs/note/06eea77326932160bc8480bd40ed654822d5d899.png@1058w_!web-note.webp)

c.提交缓存的修改

git commit

d.文件状态总结

04:01

e.git commit 具体操作

04:41

①git commit 进入提交界面,

按" i "键进入输入模式后输入本次提交详情,

然后 esc 退出编辑模式, 按" : "进入命令栏, 输入"wq"保存并退出.

②git commit -m ' 你对提交内容的描述 '

05:04

③git commit -a

连带未暂存文件一起提交

git commit -am '提交描述'

15:51

④git reset head~ --soft

05:16

使用该命令取消本次提交, 但是首次提交不可撤回.

f.查看状态

05:47

①git status

红色代表 已修改, 未暂存

绿色代表 已暂存

提交后, 则不显示

②git diff

06:21

详细查看文件的第几行第几个字母被修改了

③git log

06:30

查看提交历史信息

17:19

git log --all

查看所有分支的提交

结合 graph 食用更佳

17:30

git log --all --graph

06:59

git log--pretty

git log--pretty=oneline

自定义格式...

④git log--graph

07:17

12:04

**三、远程仓库**

07:39

注册比较简单, 就不教了

07:51

**1.链接远程仓库到本地**

08:15

git remote add origin 远程仓库链接

**2.重命名仓库**

08:34

git remote rename 目标仓库名 修改内容

**3.推送到远程仓库**

a.

08:55

git push 仓库名 分支名

b.GitHub 已禁止使用用户名与密码验证

① 使用 token 令牌验证

09:21

② 简单方式:ssh 鉴权

10:14

**四、分支**

**1.分支的概念**

12:04

**2.经典 git 模型**

13:08

**3.创建分支**

15:02

git branch 分支名

16:38

git checkout -b 分支名

**4.查看分支**

git branch --list

**5.切换分支**

15:19

git checkout 分支名

**五、分支合并**

18:04

**1.无冲突合并**

在 合并至 的分支使用

git merge 要合并的分支

**2.分支冲突 merge conflict**

18:49

将 分支 2 合并到 master 分支 时, 与 分支 1 冲突了. 原因是 分支 1 和 分支 2 修改了同一处内容.



git status 查看哪里有冲突

vi 到冲突文件中, 选择一个分支的内容保留下来, 保存退出

git add 文件名

git commit -m '提交描述'

git log --all --graph 查看合并状态

**六、推拉与远程跟踪分支**

**1.推送**

20:04

git push 仓库名 分支名

**或者**

git push -u 仓库名 分支名

第一次使用 -u 指定推送目标后, 此后可直接使用 git push

**2.拉取**

20:38

git fetch

20:45

git checkout 远程分支

git checkout -b 本地分支名 远程分支

git checkout --track 远程分支

**七、贮藏功能**

**1.git stash**

22:08

代码写到一半有 13 事儿来了, 要切换到其他分支是不允许的, 可以把当前分支修改的东西储藏起来再切换.

**2.git stash apply**

22:52

切换回来后, 恢复之前存储的内容

**3.多次存储**

23:08

a.回看存储记录

git stash list

b.恢复指定记录

23:37

git stash apply stash@{记录号}

c.恢复并删除记录

24:27

① 恢复并删除最近一次记录

git stash pop

②**删除**指定记录

git stash drop @stash{记录号}

**八、\*\***重置\***\*与变基**

**1.reset(重置)**

a.head

25:11

head: 当前的提交

head~: 上次的提交

head~2: 倒数第二次的提交

b. --soft

25:34

仅取消 commit 操作, 把修改文件暂存.

如果不加 --soft 则表示恢复到暂存前, 修改的内容是存在的.

c. --hard

26:01

取消暂存, 还取消修改内容, 彻底回到上次提交的状态.

不推荐使用, 可能丢失数据.

**2.rebase(变基)**

26:26

a.将 B 分支的修改移动到 A 分支

26:33

git checkout B

git rebase A

b.注意事项

27:04

注意他人在远程分支二次开发时, 审慎使用变基

c.交互式操作

27:27
