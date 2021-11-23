# _Valenzano lab_ website repo
<img src="https://user-images.githubusercontent.com/4720805/141675891-e0f6e034-6e6d-429c-815b-0b77c716b89d.png" width="18%"></img>  

This document contains the instructions on how to contribute to the development and maintenance of the **_Valenzano lab_** [website](https://valenzano-lab.github.io/labsite/) at the [Leibniz Institute on Aging](https://www.leibniz-fli.de/).  

The Valenzano lab website is written in [RMarkdown](https://bookdown.org/yihui/rmarkdown/) and is built using the [__Distill__](https://rstudio.github.io/distill/website.html) package.  
If you are a member of the Valenzano lab and are interested in actively contributing to the lab website, please do the following:  
1. get your own [github](https://github.com/) account 
2. familiarize yourself with [git](https://ryoaxton.medium.com/familiarize-yourself-with-git-fadcc125dbb9), [version control](https://en.wikipedia.org/wiki/Version_control) and [markdown](https://en.wikipedia.org/wiki/Markdown)
3. request to Dario to add you as a [collaborator](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-user-account/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository) on this repo.  
  
Once you are a collaborator on this repo, you can contribute to improving its content by issuing [pull requests](https://www.youtube.com/watch?v=rgbCcBNZcdQ).

### How to push changes to the master branch

```
username$ git status
username$ git add .
username$ git commit -m "description of changes"
username$ git push -u origin master
```


### How to create a new branch

```
username$ git branch -a # to list all your current branches
username$ git checkout master # to switch to the branch 'master'
username$ git checkout -b develop # creates a new branch named 'develop'
username$ git checkout develop # puts you in the 'develop' branch in case you're not there
username$ git add .
username$ git commit -m "whatever" # commits your changes to the branch 'develop'
username$ git push -u origin develop # pushes your commits to 'develop' 
```

### Merging branches (develop to master)

```
username$ git branch -a
username$ git checkout master 
username$ git merge develop
username$ git push
```

### Deleting a remote and local branch (don't do this unless you know what you're doing)

```
username$ git push -d origin develop
username$ git branch -d develop
```

As a rule-of-thumb, do not push your changes to the 'master' branch.  
Rather, first push your changes to a remote branch, like 'develop', and only then merge on the 'master' branch following the instructions above.  
