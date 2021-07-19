# Git Cheat Sheet

Note: Something written like \<this> means you should replace everything, including the brackets.

## Add/Commit/Push

---

So you have a file you either created or modified, and you want your changes reflected by git. We need to run a series of commands to achieve this.

First, run git add. Here are some possible variations:

> `git add <filename>`

adds a single file,

> `git add <filename1> <filename2> <filename3>`

adds a group of files,

> `git add -u`

adds all modified files.

Second, run git commit. Here is how it should almost always look:

> `git commit -m "<Helpful message about what I changed>"`

Third and last, run git push.

> `git push`

almost always works. If you have just created a new branch, git push will give you an error message and ask you to instead run:

> `git push --set-upstream origin <branchname>`

which you can just copy and paste from the error message.

## Branches

---

When developing any sort of software, it is helpful to use branches. The `main` or `master` branch holds only very stable versions of the code, and is often deployed directly to a website. Other branches can be worked on directly by developers. If I wanted to create a new branch to work on the streaming history feature, I would run the following commands:

> `git branch`

tells me what branch I am currently on. If I am creating a new branch, I probably want to be on `main`. If I am on `main`, I run:

> `git checkout -b streaming-history`

which creates a branch called `streaming-history` and swtiches me to it.

If I have finished developing and testing the streaming history feature and I am ready to put the code into `main`, I will open a pull request. This can be done entirely on github.com. With the repository site open, I would click _Pull Requests > New pull request > base: main, compare: \<my-branch> > Create pull request_. I would add one reviewer, perhaps someone else who is familiar with the streaming history feature. That person can look at my changes, add comments, and either request that I make changes or approve the branch as-is.

## Merge Conflicts

---

If my branch and the main branch have differences that git cannot easily resolve, it will alert me about merge conflicts. This can come up in various ways, for example, if I run:

> `git pull origin <my-branch>`

in order to have changes to `main` reflected in my branch. This could also come up when I open a pull request. If it comes up from the former, I can resolve them in VS Code. I open the file that has conflicts and VS Code highlights the problem areas, asking if I want to `Accept Current Change | Accept Incoming Change | Accept Both Changes | Compare Changes`. I probably want to click one of the first two. `Accept Current Change` keeps the changes I have on my branch, while `Accept Incoming Change` keeps the changes of the branch I pulled in (`main` in this example). `Accept Both Changes` keeps both, and `Comapre Changes` will show me more details.

Once I have gone through all of the conflicts in all of the conflicting files, I save, then add, commit, and push my changes. The merge conflicts should now be resolved.

## Confused?

---

> `git status`

is your friend. I use this command all the time.

`Changes not staged for commit:` are changes that I have saved locally but not yet `git add`ed.

> `git add -u`

adds all of these.

`Untracked files:` are files I have locally but not `git add`ed.

`Changes staged for commit:` are changes I have `git add`ed but not `git commit`ed.

If this cheat sheet didn't cover what you need to know, consult Google or try this one: https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet.
