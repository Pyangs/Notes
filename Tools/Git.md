## log
##### show recent commits in specific branch
    # checkout to a branch first
    $ git log

##### show recent x commits and file(s) changed
    # git log -n x --stat 
    # eg: show recent 2
    $ git log -n 2 --stat

##### show recent x commits and detials
    # eg: recent 1
    # git log -n 1 -p

## Branches
##### add a local branch remote to origin branch
    $ git checkout -b dev origin/dev

##### show local branches
    $ git branch

##### show origin branches
    $ git branch -r

#####   show all branches 
    $ git branch -a

##### show files in branch_A but not in branch_B
    $ git log branch_A ^branch_B

##### fetch all branches 
    $ git fetch --all

##### show what texts in branch_A but not in branch_B
    $ git log branch_A..branch_B

##### show the diff between branch_A and branch_B
    $ git log branch_A...branch_B

##### show the diff between branch_A and branch_B
    $ git diff branch_A branch_B

##### merge branch_A into brranch_B
    $ # checkout to branch_B first 
    $ git merge branch_A

##### show latest push in every branch
    $ git branch -v

## Version control & tags
##### go back to previou version 
    $ # will not delete local codes
    $ git reset HEAD^

##### add a tag to current branch
    $ git tag -a v0.1.2 -m “version0.1.2”

##### add a tag to a specific commit
    $ git tag -a v0.1.1 9fbc3d0

##### push tags to origin
    $ git push origin --tags
    $ git push origin v1.0.2

##### give up all local change 
    $ git checkout -- .

##### update local branches list
    $ git fetch origin -p

##### 更新远程仓库，从引用 fork 的原仓库地址同步内容，此时原仓库的master（主干分支）已经可以在本地访问了
    $ git remote update originUpstream


