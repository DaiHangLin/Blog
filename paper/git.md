# ------------   2017.10.12 ---------------

## 1. git status
//查看git status 可能存在三种文件

~~~java
//第一种 未被跟踪的文件，即新添加的文件
1.1  Untracked files:  
  //git add <file> 将文件添加staged中
  1.1.1 (use "git add <file>..." to include in what will be committed)
//第二种 已添加的文件且还未加入到staged中
1.2  Changes not staged for commit 
  1.2.1 (use "git add <file>..." to update what will be committed)
  //git checkout -- <file> 撤销对该文件的修改
  1.2.2 (use "git checkout -- <file>..." to discard changes in working directory)
//第三种 已加入到暂存中,可以提交	
1.3  Changes to be committed
  // git reset HEAD <file>  取消暂存
  1.3.1 (use "git reset HEAD <file>..." to unstage)
~~~
## 先添加修改的文件staged中
    git add a1.txt
    git add a2.txt

## reset 默认是第一个commit前 并且不在暂存中

    git reset --mixed (HEAD~0)  
    git status 
    //发现所有修改的文件都在unstaged中

## 添加所有文件添加到暂存中
    git add .
    git commit //新增一次commit记录
    git log //查看历史提交记录
      // 1 commit a4863
      // 2 commit f7a86

# 2.git reset      
## 将1的commit删除，并且所有的修改都不在暂存中
    git reset --mixed HEAD~1
    // 将1的commit删除，并且所有的修改都不在暂存中
    
## 将1的commit删除，并且所有的修改都在暂存中
    git reset --soft HEAD~1
    // 将1的commit删除，并且所有的修改都在暂存中
   
## 将1的commit删除，并且丢弃所有的修改   
    git reset --hard HEAD~1
    // 将1的commit删除，并且丢弃所有的修改
	
# 3. git rebase
## git rebase -i //对最近的几次commit进行修改

    git rebase -i HEAD~2
	  //  pick f7a8619  commnet1
	  //  pick a4863c2  comment2
	  //  rebase 有几个Commands 
		10.1.1 pick     // use commit
		10.1.2 reword   // use commit, but edit the commit message
		10.1.3 edit     // use commit, but stop for amending
		10.1.4 squash   // use commit, but meld into previous commit
		10.1.5 fixup    // like "squash", but discard this commit's log message
		10.1.6 exec     // run command (the rest of the line) using shell
	10.2 //也可以直接删除一条记录  这样的话这条commit就会被删除  
	
	
