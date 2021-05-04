# GIT
```
git init (Initialize git repositories)
```

```
git config --global user.email "mdshayon0@gmail.com"
git config --global user.name "Md Shayon"
```


```
git status (git knows we have some file in this folder)
```

```
git add filename.extension (add single file)
# this will track all the file inside the folder
git add . 
# This will add all file of same extension
git add *.extension 
```
 - all the files are green color that means all are added to git
```
git status
```
 - remove single file from repository
```
git rm --cached file.extension 
```
 - Add the folder path to your repo's root **.gitignore** file.
path_to_your_folder/
 - Remove the folder from your local git tracking, but keep it on your disk.
```
git rm -r --cached path_to_your_folder/
# all the files are green color that means all are added to git
git status 
```
 - we can change anything . if we change we need to command 
``` 
git add . 
git commit -m "some change"
# this will track all the file inside the folder
git add . 
# we can commit when it open with a code editor. But this is not best way
git commit 
# what will change we have to write in double quotation
git commit -m "starting code" 
```
 - viewing commit history
```
Git log 
# only run in git cmd. Create a folder for ignoring a file from our repository
touch .gitignore 
```

 - create a file (I name it log.txt   you can name anything you want)
 - open **.gitignore** with any text editor include the file name which want to ignore(for example log.txt)
 - for ignoring entire directory open **.gitignore** with any text editor include the directory name with forward slash before which want to ignore(for example /dir1)
 - for ignoring all same file extension open **.gitignore** with any text editor include **.extension** which want to ignore(for example *.txt)


https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches


git commit -m "another change"
git branch (only for general cmd. current branch I am working on)
git checkout -b login (this will create branch name login)
git branch login (this will create branch name login)
git checkout login (Switched to branch 'login')
create a new file or folder name anything, add all, commit
git checkout login (Switch back to master then you can see new created folder or file has gone)
git merge login (marge all branch or workflow)
(Create a repository in github. There will be all instruction for next steps)
git remote (list remote repositories)
git remote add origin git@github.com:MdSamsuzzohaShayon/SomethingThatShowInInstraction.git
git push -u origin master
git commit -m "Change something"
git push (for uploading changed file to github)




Downloading git repository with all branch
git remote add origin https://github.com/project-url.git
git pull