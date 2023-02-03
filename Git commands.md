# Git&Githup

> **in website " docker with play " **

**//to know who makes update and changes**

```
git config --global user.name"marina Beder"
git config --global user.email "Marina180574@feng.bu.edu.eg"
```
**to know list configuration**

```
git config --list
```

**to intialize git repo in my folder**

**first make folder**

```
mkdir gitwork
```

**to go in this folder**

```
cd gitwork/
```

** to show list**

```
ls
```

**to make file.txt contaian "Hello,Git in this text**

```
echo "Hello,Git">>file.txt
```

## 

**//to show what folder contain  ? **"Hello,Git"

```
cat file.txt
```



> **to conver this project to repo " **



**to conver this project to repo "**

**excute this command from your inside folder**

```
git init
```

**to know files that you have in folder git work**

```
ls -al
```

**to go in this folder**

```
cd gitwork/
```

**to go to inside folder git **

```
cd .git
```

**to know files that you have in folder  .git**

```
ls -al
```

**to go to folder objects which contain blob and tree**

```
cd objects/
```

**to know files that you have in folder  objects**

```
ls -al
```

**to back forward in folder **

```
cd ..
```

**to back forward another step to go main folder gitwork**

```
cd ..
```

**to know status of folder**

```
git status
// will show you:
--On branch master
--No commits yet //i will not take any version from your call 
--Untracked files // means there is new file doesnot add to repo

```

> **explore git objects and trees**
>
> we have three file
>
> - working tree to see files that you have --> ls
> - staging "index "to see files that will be tracked--> git ls-files                                                                 to see files that ("if it is empyty this is meaing that we don't have any file to trackerd") 
> - repo there is no directed way -->find .git/objects/ -type f                     
> - --all of this info 



**to convert file from untracked to tracked and make it in staging **

**to make file.txt contaian "Hello,Git in this text**

```
git add file.txt //add {file name}
git add f*       // add any file start with f
git add *.txt    //add any file .txt
git add *        //add any thing
git add .
```

## 

**//to show what folder contain  ? **"Hello,Git"

```
git status
//shw you:
--On branch master
--No commits yet
--Changes to be committed
// to return file from stage to un stage:
      use "git rm --cached <file>..." to unstage
// to know files in staging --> git ls-files
// to know files in staging with sha1 git ls-files -s
// and will be object in objects to see -->find .git/objects/ -type f
//cd .git/objects/
//ls

```

**to know type file,size, content **

**excute this command from your inside folder**

```
git cat-file -t {sha of file}  //type
git cat-file -s {sha of file}  //size 
git cat-file -p {sha of file}  //content
//still we have not snapshot untill now
```

**intialize the first file in repo **

```
git commit -m "Intial commit"//{leave message}//this file unmodified //
-->find .git/objects/ -type f
// we have three objects in repo{.blob ,.tree, .commit}
the importance of .commit that say to me that this blob related with this blob and who and when this file commited
//any commit effect in three files

```

**to get history **

```
$ git log                                                                 // give you commit ,name && email and date //this is the file .commit store this information
//gives me how many i make commit withe details who make this details in descending order from changes
$ git log --oneline //give the basic info
$ git log --oneline file.txt//to get log in specefic file
$ git log --oneline -2 //to give the last 2 commit
$ git log --oneline --graph
$ git log --oneline --all //to see local and remote

```

**if I have more objects and i want to know the history **

```
// first take this file and -->
git cat-file -t {the first 4 characters from file [in the most popular]}
type of this file is [commit]
git cat-file -p e7fe//to know content{name&&email, date ,tree}
tree is the first folder 
git cat-file -p {4 characters of sha of tree}//give file sha and                                                type(blob)
git cat-file -p 63ea //the content of file
```

**to show status in differrent way**

```
git status -s
//M is red meaning that it is not in inder nor repo
//M is green meaning that file in workflow is the same index but not the same in repo
```

**two know diff working tree and index**

```
git diff
// if i make it before "add git ." the it will show me the difference 
// if i make it after "add git ." wil not give me any diff because git diff show me the difference between working tree and index
```

**two know diff index and repo**

```
git diff --staged
//in file unmodified worktree=index=repo
```

**if you want to open editor when you do commit **

```
git config --global core.editor "vim"
git commit
```

**to know diff **

```
git show sha
```

**to know diff between two specific commit there is no in work tree**

```
git log --oneline --graph//to know sha 
$ git diff {sha}..{sha}
```

> **undoing things**

**//to know who makes update and changes**

**to delete repo**

```
rm -rf .git/
```

**to convert file from tracked to untracked from work tree to cached **

```
git rm --cached file.txt
```

**to discard change modification in file it will take the last version from index and put it in work tree {modified}**

```
git restore file.txt
```

**to convert from stage to unstage {modified and stage}**

```
git restore --staged file.txt
git restore file.txt //to discard
```

**to moddfy in message which is committed**

```
$ git commit --amend
```

**HEAD**

```
a1a1ba5 (HEAD -> master) fourth line //head point to file master
```

**to back to old version to unstage**

```
git reset HEAD~1
--if you want to take this old version to worktree
----> $  git reset --hard  HEAD~1
```

**to make fast forward**

```
git reset --hard HEAD@{1}
```

**to show  reference**

```
git reflog
```

//////////////////////////////////////////////////////////////////////////////////////////////////////

> **Tags**
>
> //when you make commit it doesnot means that you make a new version 
>
> //but in some times you make commit and you can named after this commit that you have a new version this the role of tages

**to make tag**

```
git tag -a v2.0 -m "version 2 of file"
// to show version2
$ git show v2.0
//tag is object like:blob , tree and commit
```

> **Branching**
>
> //  when i want to make for example testing and this test i will not to affected on the master branch then  i will go to branching and do some modification without affected on master

**to make braching**

```
git branch testing //{name of branch}
```

**to show all branches that i have**

```
git branch
/** master //green color means this branch is current and * means HEAD
  testing*/
  //MASTER AND TESTING POINTS TO THE SAME THING
  AND HEAD POINTS TO MASTER
```

**to switch branches**

```
git switch testing // head on testing
// when i make any commit it will be in testing branch
/* when i make  $ git status  iwill find
  On branch testing
nothing to commit, working tree clean*/
/* when i make  git log --oneline  iwill find
 (HEAD -> testing, master) third line */
```

**to switch to master branch**

```
git switch master
```

> **merging to merge branch intto master  **

**merge testing into master**

```
-- $ git switch master
----$ git merge testing
```

**to show you branches that mrged  into master**

```
git branch --merged
```

**when we merged branches into master then we don't need these branshes so we delet it **

```
git branch -d testing
```

**divert history : **

when you make new branch then make new file in master file   when you merge branch into master it will make new branch in master 

```
$ git branch testing
$ git switch testing
$ git log --oneline
$ git commit -am "fifth line"
$ git switch master
$ echo "line one in new file"
$ echo "line one in new file">>file2.txt
$ git add .
$ git commit -am "new file addeed in mast
$ git log --oneline
$ git switch master
$ git merge testing
$ git log --oneline
$ git branch --merged
$ git branch -d testing
```



> **working with remotes **
>
> we will simulate between two folders in computer for learning 
>
> --make new folder remote repo and make file 
>
> 

**then make clone from this repo**

```
$ git clone ./remote-repo/local-repo //{path }/{new name}
```

**go to local repo**

```
cd local-repo/
```

**to show all remote repo**

```
git remote //if answer is orgin then we this is local repo take from remote repo
```

**to show all remote repo in details **

```
$ git remote -v
origin  C:/Users/marin/./remote-repo/ (fetch) /*means down stream*/
origin  C:/Users/marin/./remote-repo/ (push)/*means up stream*/
// this means that i make two things in remoe im can do (fetch)
// and i can do (push)
```

**to know branches come from remote**

```
git branch -r
```

**to take cahnges that happenes in mater after clone  **

```
git fetch origin {name of remote}
//come all changes from remote but not make merge 
//your barnch is behind ing git status /*means that you should make merge*/
then :
git merge

```

```
/*when you make changes in local repo*/
/*if you change in local repo and make $ git status 
-->you find your branch is a head of*/
```

**to make graph = **git log -onleline --all -graph --decorate

```
$ alias graph="git log --oneline --all --graph --decorate"
```

**to local branch**

```
git branch fearture /m/make new branch in local but not found in remote
switch to branch 'feature'
/*if you make $git push origin 
/*you find the current branch feature has no upstream branch */ 
--solution 
$git push --u origin feature//branch feature will create and then make push
```

**to make fetch down strean we make fetch and merge in the same time**

```
git pull origin// make fetch and merge into local  
```

**to track  more detaials**

```
git branch -vv
```

**to go to folder objects which contain blob and tree**

```
cd objects/
```

**to know files that you have in folder  objects**

```
ls -al
```

**to back forward in folder **

```
cd ..
```

**to back forward another step to go main folder gitwork**

```
cd ..
```

