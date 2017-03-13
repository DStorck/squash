#Repo to learn about git-squash

Let's say you have a bunch of commits that are not that interesting, and a good one that fixed a feature or something.  
at the moment i have:
```
DStorck~/Samsung/squash (master)$ git hist
* 6498fd8 2017-03-13 | fifth commit -bad (HEAD -> master) [Deirdre Storck]
* dd31419 2017-03-13 | fourth commit - bad [Deirdre Storck]
* 8130c25 2017-03-13 | third commit [Deirdre Storck]
* 9600517 2017-03-13 | second commit - added a line of text [Deirdre Storck]
* 4e5891a 2017-03-13 | first commit (origin/master) [Deirdre Storck]
```

type `git rebase -i HEAD~5`

this will open up an interactive vim editor, where you can SQUASH down your commits

```
pick 9600517 second commit - added a line of text
pick 8130c25 third commit
pick dd31419 fourth commit - bad
pick 6498fd8 fifth commit -bad
pick c7803df sixth commit - good

# Rebase 4e5891a..c7803df onto 4e5891a (5 commands)
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
# d, drop = remove commit
#
# These lines can be re-ordered; they are executed from top to bottom.
```
Change the 'pick' to 's' or 'squash', and it will squash those into an older commit.

```
pick 9600517 second commit - added a line of text
s 8130c25 third commit
s dd31419 fourth commit - bad
s 6498fd8 fifth commit -bad
pick c7803df sixth commit - good
```
and now:
```
DStorck~/Samsung/squash (master)$ git hist
* 8d800a4 2017-03-13 | sixth commit - good (HEAD -> master) [Deirdre Storck]
* 1342bb8 2017-03-13 | second commit - added a line of text [Deirdre Storck]
* 4e5891a 2017-03-13 | first commit (origin/master) [Deirdre Storck]
```
You have re-written history.
WARNING! Do not attempt to squash commits that are shared.  This will anger the gods. 
