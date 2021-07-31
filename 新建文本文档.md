查看git 名称：  
git config --global user.name  
查看git 邮箱：  
git config --global user.email  
  
设置git 名称  
git config --global user.name xkb  
设置git 邮箱：  
git config --global user.email 6148@qq.com  
  
用户目录创建用户别名：  
touch ~/.basrc  
输入：  
#用于输出git提交日志  
alias git-log='git log --pretty=oneline --all --graph --abbrev-commit'  
#用于输出当前目录所有文件及基本信息  
alias  ll='ls -al'  
  
查看提交记录：  
 git log --pretty=oneline --abbrev-commit --all --graph  
  

解决输入中文乱码打开GitBash执行下面命令  
git config --global core.quotepath false  
2. $git home/etc/bash.bashrc文件最后加入下面两行安装目录执行  
export LANG="zh_cN.UTF-8"   
export LC_ALL="zcN. UTF-8"  
  
  
内容提交  
git add .  添加提交全部  
git add 接文件名  代表添加提交某一个文件  
git commit -m "提交注释" 提交文件  
git status 查看状态  
git log 提交记录  
    
版本回退覆盖  
git reset --hard 后面为提交ID  
git reset --hard 6f16c6bd388f270123b2bc2244151b576cbb9cbc  
  
 git reflog查看全部操作用来防止错误覆盖  
git reset --hard db64df0 恢复  
  
  
不上传某一类文件  如不上传.a类型文件  
创建 .gitignore文件，文件中写入*a，执行mv .gitingore .gitignore  
  
连接远程仓库  
1、生成密钥： ssh-keygen -t rsa  
2、查看密钥： cat ~/.ssh/id_rsa.pub  
3、git网页上配置密钥信息  
4、验证是否配置成功 ssh -T git@github.com  
  
  
合并分支  
git fetch origin  
git checkout main  
git merge master --allow-unrelated-histories（合并分支解决冲突）  
  
直接合并分支，显示  
fatal:refusing to merge unrelated histories  
git add *  
git commit -m '合并分支'  
git push  



