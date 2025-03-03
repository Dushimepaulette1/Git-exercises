##Editing Commit History:

It's crucial to maintain accurate commit messages. Modify the message from "Create another file" to "Create second file".
Challenge: Utilize interactive rebasing (git rebase -i HEAD~2) to edit the commit message and ensure clarity. learn more about git rebase here
##Terminal commands
Green Way@PAU MINGW64 ~ (main)
$ cd Git-exercises/

Green Way@PAU MINGW64 ~/Git-exercises (main|REBASE)
$ ls
test1.md

Green Way@PAU MINGW64 ~/Git-exercises (main|REBASE)
$ ls
test1.md

Green Way@PAU MINGW64 ~/Git-exercises (main|REBASE)
$ git status
interactive rebase in progress; onto f1cfaf6
No commands done.
Next commands to do (2 remaining commands):
   pick f8a8700 chore: Create another file
   squash 026feb4 Create second file
  (use "git rebase --edit-todo" to view and edit)
You are currently editing a commit while rebasing branch 'main' on 'f1cfaf6'.
  (use "git commit --amend" to amend the current commit)
  (use "git rebase --continue" once you are satisfied with your changes)

nothing to commit, working tree clean

Green Way@PAU MINGW64 ~/Git-exercises (main|REBASE)
$ git rebase --edit-todo

Green Way@PAU MINGW64 ~/Git-exercises (main|REBASE)
$ git rebase --continue
[detached HEAD 481aefe] chore: Create another file
 Date: Fri Feb 28 14:44:23 2025 +0200
 3 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.md
 create mode 100644 test3.md
 create mode 100644 test4.md
Successfully rebased and updated refs/heads/main.

Green Way@PAU MINGW64 ~/Git-exercises (main)
$ git add test4.md


