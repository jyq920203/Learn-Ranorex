# svn更新提交的几种情况：
1. 本地修改，服务端没有修改，update，没有修改
2. 本地没有修改，服务端修改，update，本地被覆盖
3. 本地修改，服务端也修改，update，如何没有修改同一处，那么合并；如果修改同一处，update会出现冲突，这时候就需要手工编辑冲突，然后再上传到服务器中；这时候你update并不会让你编辑的文件消失，有冲突只是会显示冲突，没有冲突会合并；
4. 同时修改一个文件，不同地方，每次必须先update，再提交，不update也是会冲突的。

# 冲突解决的两种办法：
1. 将红色感叹号标注的文件，修改文件名称，然后update，这时候会将服务器上的文件更新下来，用beyound compare进行比较，然后提交你手工修改合并的版本。
2. 冲突后，使用edit conflict进行文件的冲突编辑。当文件出现冲突的时候，就需要去比较文件，出现黄色感叹号的时候就是有了冲突，一般你的文件夹中会出现四个文件，如果文件本身是二进制的，那么会出现三个文件；需要右击黄色的感叹号文件，然后点击edit conflict

* AA.c 是按照你更新的内容与存在的冲突，系统自动合并的版本
* AA.c.mine 是你的更新版本
* AA.c.r6 是更新操作以前的版本，就是在这个版本的基础上做的现有修改
* AA.c.r7 是版本库中的最新版本，这里有别人的修改，而就是这个修改和你的修改冲突了

# 建议
1. 是关于Repository文件，由一个人统一录制，然后需要更新的时候，大家将本地的文件删除，因为这是一个二进制的文件，经常会冲突而且不可以对比更新。
2. 还有一个文件就是excel，由于由多个页签，也需要由一个人统一管理。
3. 使用Ranorex自带的svn插件进行提交，因为很多文件是不需要提交的，自带的插件功能会再提交的时候摒弃这些文件。如bin目录，会在build的时候自动生成，不需要提交到配置库，每个人本地的bin文件差异很大，不需要提交。不影响别人使用。
4. 一定记住先update，确认没有conflict的时候再提交。

# 如何去除一些已经上传到配置库但实际并不需要上传的文件？
右击文件选择unversion and add to igored list

# svn图标不显示
**解决方法一（失败）：**

升级最新版本，我的本来就是最新版本

**解决方法二（失败）：**

右键 ->TortoiseSVN->setting->Icon Overlays->Status cache->default/Shell。none 是不显示

**解决方法三（失败）：**

修复或者卸载重装

**解决方法四（成功）：**

Windows Explorer Shell 支持 Overlay Icon 最多 15 个，Windows 自身已经使用了 4 个，所以就只剩下了 11 个 供我们使用。如果你之前安装了例如 Groove 这样的软件，那么可能我们可利用的就更少了，轮不到 Tortoise 了。像这样的情况，我们可以调整 Tortoise 图标名称的字母顺序，来提高 Tortoise 的优先位置，因为 Windows 内部就是安装名称的字母顺序来优先显示的。  解决的步骤  在 运行里 输入 regedit 进入 注册表 界面，HKEY_LOCAL_MACHINE->SOFTWARE->Microsoft->Windows->CurrentVersion->Explorer->ShellIconOverlayIdentifiers 打开后发现 Tortoise 系列（1TortoiseNormal，2TortoiseAdded 等）前面有好多项，Tortoise 系列排到了 15 名之后，难怪不显示。现在的任务就是把它们提到前面了，修改一下它们的名字就好（我是看第一项的前缀是空格，说明空格的字符排序在前面，我就加了几个空格），我改后的名字如（    TortoiseNormal，    TortoiseAdded 等），然后关闭再打开注册表，发现 Tortoise 系列系列图标已经排到前面了，这时 SVN 的图标并没有显示，靠，重启 Explorer（在任务管理器中结束 explorer.exe，在文件 -> 新建任务 -> 输入 explorer，当然可以重启电脑，不过好 sb），这样就 ok 了，可爱的 SVN 图标又出现了。
