---
title: My Most Used Git Commands
layout: post
---

# My Most Used Git Commands

Some git commands are more useful than others. These are my top commands:

`git add -p`  
Definitely used most. I tend to make lots of code changes and then cycle through
them patch by patch to carve out commits. The `-p` (or `--patch`) options shows
changes one by one and lets you add each hunk separately to the index. Can also
be used on a specific file or directory, like `git add -p app/supermargins.rb`,
to cycle through the changes there. This one is actually a shortcut for
`git add -i` and then choosing the `5: patch` option.

`git dog`  
This one does not really exist! It's an alias for:

`git log --pretty='format:%C(yellow)%h %Cred%ad %Cblue%an %Creset%s' --date=short -10`

I find myself looking at git history a lot, and this command gives me a nice
compact overview of the recent past. With colors! Can also be called with more
output by using `git dog -30` for example.

`git commit --amend`  
For those times when you forgot to add something to the last made commit. Put
the change in the index and use this, change will be added to the commit. Also
gives you the opportunity to edit the commit message.

`git rebase -i HEAD~`  
For me, the beauty of git is not that it can be used to record history, but that
it can be used to _craft_ history. Building git commits is part of my thinking
process. Making changes to older commits or their order, or even just changing
the commit messages helps me order my thoughts and my coding. Also, it's nice
for my colleagues when the git history is clear and specific.

This command will rebase the number of commits you specify on the current
branch. It will give you several options for every chosen commit:

```
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup <commit> = like "squash", but discard this commit's log message
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified). Use -c <commit> to reword the commit message.
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
```

Per commit you can define what to do with it. I mainly use the `reword`, `edit`,
`fixup` and `drop` commands. Rebasing might feel scary in the beginning, but it
provides you with a lot of freedom.

A few more contenders - I use those regularly, but not daily.

`sortag`  
Nope, does not exist either. This command is an alias for:

`git tag | sort -Vr | head`

I find myself often checking what the last tag is in a repository. This command
gets all tags known to git, does a version number sort (`-V`) and reverses the
result (`-r`) to show you the 10 tags with the highest version number.

`git add -i`  
This one gives you a menu with several options. I mainly use it for the 4th
option, `4: add untracked`. It lets you quickly add several new files to the
index.
