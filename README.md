4th Dec 2015: from github directory, just do
git clone https://github.com/hakeJTC/hakeAssess - not using that now.

2nd June 2015: Andy's git push stopped working, giving RPC error, with 'the remote end hung up unexpectedly'. This was on my size-spectra-methods repo, but another one still worked. I think it may have been caused by a colleague doing and then accepting his own pull request, which is a different order to what we normally do. It had worked fine before that.

Solution, thanks to Chris:
edit the .git/config file   -- mine had some http:// addresses when they should all be https://  .  Changed them, based on Chris' config file, to:

[branch "master"]
	remote = origin
	merge = refs/heads/master
[remote "origin"]
	url = https://github.com/andrew-edwards/size-spectra-methods

Restarted shell, and it works. 

24th May 2016: Had same error as noted above (but config file had https), but worked fine when I went home. So it was just timing out at work because the internet was so slow. Could git push straight away at home. 

---
# git-workshop

*Created by Chris Grandin, February 2014*

Hello World!

Hello again.... Andy's edit.

Okay, figured out my problems - I was looking at the 'latest commit' of the Network Graph Visualiser, not my home git-workshop version. So refreshing wouldn't update to the latest pushed version, it would just refresh a particular commit (which was no longer the latest, but was still a particular commit).

If you add text, save file, then remove it again and save, git knows that nothing has changed....

[Changing this in the master version, then want to merge this and the line added in the test branch.]

[Adding this in the 'test' branch, then going to try merging back again..... ]

Resolved those two (just in emacs - easy enough as can easily add text like this sentence).

git-workshop is a repository for learning how to use git version control.
Also included are examples for using *Latex* and the R package *knitr* to apply version control to documents
which are to be edited by more than one person, working collaboratively.


The purpose is to introduce git version control to new users and supply some
useful tools for working with git.

---

To make everything in this repository work correctly, you will need to <a href="https://github.com/" target="_blank">sign up for GitHub</a>
and install the following things on your computer. If you have older versions of GitHub or MikTex installed, remove them and start fresh.
GitHub *requires* Microsoft .NET 4.5.1 as of February 2014.

1. If you have a .NET version less than 4.5 ([Check version](https://github.com/downloads/shanselman/SmallestDotNet/CheckForDotNet45.exe "Which .NET version is on my machine?")), then upgrade it: <a href="http://go.microsoft.com/fwlink/p/?LinkId=310158" target="_blank">Microsoft .NET 4.5.1</a>.
2. <a href="http://windows.github.com" target="_blank">GitHub for Windows</a>
3. <a href="http://mirrors.ctan.org/systems/win32/miktex/setup/basic-miktex-2.9.5105-x64.exe" target="_blank">Miktex typesetting software</a>
4. The knitr package for R - install.packages("knitr")

---

Once you have installed GitHub for Windows, go to my [git-workshop](https://github.com/cgrandin/git-workshop "https://github.com/cgrandin/git-workshop")
, make sure you are signed in, and **Fork** the project (button on the top right). This will create a copy of the repository on your GitHub site.

Open the GitHub Application. Choose Tools->Options and under *configure git*, fill in your name, the email address you used for signing up to GitHub,
and change your *default storage directory* to something simple that you will be able to find later. I recommend **c:\github**. Make sure that for
*default shell*, *PowerShell* is checked. *pull behavior* should have *use rebase for pulls* checked. Click *Update* and close the application.
**This is a one-time step and you will not need to do it again unless you want to sign in with a different user name.**

Open the Git Shell, (not the GitHub application). The shortcut should be
**C:\Users\your-computer-user-name\AppData\Local\GitHub\GitHub.appref-ms --open-shell**

Note your starting directory, this is where your files will be. It should be the same as the one you entered into the GitHub application in the steps above.

Type the following to clone your repository onto your local machine:

      git clone https://github.com/your-git-user-name/git-workshop

## Useful commands in the Git Shell
      git help                          <List git commands>
      git clone url                     <Clone repository found at url>
      git status                        <View changes & staging>
      gitk                              <GUI - show revision tree information>
      git gui                           <GUI - show revisions, merge branches>
      git mergetool                     <GUI - merge helper. DiffMerge from sourcegear is a good one>
      git remote -v                     <Look at all remote data sources (URLs)>
      git remote add NAME URL           <Add the remote reposiroty at URL, and give it the name NAME>
      git fetch NAME                    <Fetch the commits from the repository denoted by NAME>
      git add FILENAME                  <Add new file called FILENAME>
      git remove FILENAME               <Remove existing file called FILENAME>
      git rm FILENAME                   <Remove existing file called FILENAME>
      git commit -a -m "MESSAGE"        <Commit with MESSAGE recorded to the log>
      git log                           <View commit log>
      git branch                        <List all branches>
      git checkout -b NAME              <Create new branch called NAME>
      git checkout NAME                 <Switch to already-existing branch called NAME>
      git branch -d NAME                <Safely delete the branch called NAME>
      git branch -D NAME                <Forcibly delete the branch called NAME>
      git log branchA ^branchB          <show log of commits in branchA but not in branchB>
      git log master ^origin/master     <Show difference between local master and origin/master (latest copy of remote)>
      git push origin --delete NAME     <Delete the branch NAME from the remote>
      git reset --soft HEAD~N           <Undo commits safely. Move back N commits, keeping changes from last N-1 commits>
      git reset --hard HEAD~N           <Move back N commits, destroying changes made in latest N-1 commits>
      git log --diff-filter=D --summary <Shows all commits in which files were deleted>
      git checkout -- FILENAME          <Undo an unstaged/uncommitted change to FILENAME, i.e. get the file back if deleted>
      git checkout --patch B FILE       <Merge changes to FILE from branch B into your current branch>
## Useful Git aliases
      git r                             <View remote URLs for the project, same as 'git remote -v'>
      git s                             <View status of the repository, same as 'git status'>
      git f                             <View sync information between origin master and master>
      git co NAME                       <Change to branch "NAME", same as 'git checkout "NAME"'>
      git cb NAME                       <Create branch "NAME", same as 'git checkout -b "NAME"'>
      git com "MESSAGE"                 <Commit all with message, same as 'git commit -a -m "MESSAGE"'>
      git pom                           <Push to origin master (GitHub), same as 'git push origin master'>
      git mas                           <Show difference between local and remote masters, same as 'git log master ^origin/master'>
      git sam                           <Show difference between remote and local master, same as 'git log ^master origin/master'>
      git dl                            <Show modified files in last commit>
      git dlc                           <Show file differences in last commit>
      git lg                            <Show merge structure in a colored format>
      git lds                           <Show one-line commits in a colored format>
      git ld                            <Show one-line commits with reletive times in a colored format>
      git wdiff                         <Highlight individual words when diffing, same as 'idiff --word-diff=plain'>

This is a great resource for understanding git: <a href="http://git-scm.com/documentation" target="_blank">git-scm</a>

A very useful video tutorial by a GitHub expert, a must watch if you will be using git: <a href="http://www.youtube.com/watch?v=ZDR433b0HJY" target="_blank">Git Video</a>

posh-git is the project which is the Git Shell we have been using here. Check out the details about the prompt and other things here:
<a href="https://github.com/dahlbyk/posh-git" target="_blank">posh-git</a>

---
## Branching (Chris explained to Andy, 10/6/16)

It's basically all in Chris's Powerpoint, but copying and summarising here. The idea is that you want to change something, but don’t want your code to break in the meantime. You want to be able to revert back to a particular point in time, and then possibly delete the extra code that you tried (if it didn't work). If you just carry on as normal it's a bit fiddly to remove the unwanted commits from GitHub, and having two branches means that you can easily switch to see how the code used to look.

Create a branch and go to it:

	git cb test

You will now have a new branch called test, identical to the master. You will be in that branch, as seen in your shell prompt.

To view all branches (current one in green):

	git branch

To change to a branch:

	git co test

Commit and push as usual ('git push' will give an error and tell you the full command you need). And then to go back to master:

	git co master

When in master, to merge in the commits from the test branch:

	git merge test

To delete a branch:

	git branch –d test
	git push origin --delete test

where the second one deletes it from GitHub.

If you edit a file in a branch and do not commit or stash it, then git won't let you switch to another branch. But it seems okay with that if test and master are the same (i.e. the first time you do an edit). Once you've done a commit on test then you can't switch without committing or stashing. Stashing is just parking something (but not committing it) so you can then switch branches (e.g. to see what the code says in another branch). Just do, from test:

	git stash
	git co master
Look at your code in master.Then

	git co test
	git stash apply
to retrieve the stashed version. Advisable to do this straight away (i.e. don't leave for the night with something stashed as you'll forget about it, and the command line prompt doesn't highlight that you have something stashed). To see what you have stashed:

	git stash list

**Compare a file across branches**

	git difftool branch1 branch2 path/filename

where branch1 is 'older', e.g.

	git difftool master binData code/countsFunctions.r

where 

	git difftool 

opens a window which makes it easier to see changes than just using

	git diff

Also, 

	git difftool branch1 branch2

opens up the difftool window for one file, then when you close the window it opens a new one for the next file - so it looks like it systematically goes through all files in turn.


	
---