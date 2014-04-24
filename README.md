---
# git-workshop

*Created by Chris Grandin, February 2014*

Hello World!

Hello again.... Andy's edit.

Andy adding this on 24th April.

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

