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

##Keeping History Tidy - Squashing Commits:
<<<<<<< HEAD
=======

Squashing combines multiple commits into a single one. Let's merge "Create second file" into "Create initial file" for a cleaner history.
Challenge: Use interactive rebasing with the squash command to achieve this. learn more about squash here

Green Way@PAU MINGW64 ~/Git-exercises (main)
$ git log
commit 481aefee1ee391a24590a512e5cef3b9a564b3d9 (HEAD -> main)
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:23 2025 +0200

    chore: Create another file

    Create second file

commit f1cfaf66854162da84154d4d014375042ca7e8ef
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:15 2025 +0200

    chore: Create initial file

Green Way@PAU MINGW64 ~/Git-exercises (main)
$ git rebase -i HEAD~2
fatal: invalid upstream 'HEAD~2'

Green Way@PAU MINGW64 ~/Git-exercises (main)
$ git rebase -i HEAD~2
fatal: invalid upstream 'HEAD~2'

Green Way@PAU MINGW64 ~/Git-exercises (main)
$ git log
commit 481aefee1ee391a24590a512e5cef3b9a564b3d9 (HEAD -> main)
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:23 2025 +0200

    chore: Create another file

    Create second file

commit f1cfaf66854162da84154d4d014375042ca7e8ef
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:15 2025 +0200

OA    chore: Create initial file

Green Way@PAU MINGW64 ~/Git-exercises (main)
OA$ git rebase -i --root
OA[detached HEAD 3982183] chore: Create initial file
OA Date: Fri Feb 28 14:44:15 2025 +0200
OA 4 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
OA create mode 100644 test2.md
 create mode 100644 test3.md
 create mode 100644 test4.md
OASuccessfully rebased and updated refs/heads/main.
OA
OAGreen Way@PAU MINGW64 ~/Git-exercises (main)
$ git log
OAcommit 3982183c5cad2b4a81ca6262167264efdc1fc68b (HEAD -> main)
OAAuthor: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:15 2025 +0200
OA
OA    chore: Create initial file

    chore: Create another file
OA
    Create second file

Green Way@PAU MINGW64 ~/Git-exercises (main)
$ git log
commit 3982183c5cad2b4a81ca6262167264efdc1fc68b (HEAD -> main)
OAAuthor: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:15 2025 +0200

    chore: Create initial file

    chore: Create another file

    Create second file

Green Way@PAU MINGW64 ~/Git-exercises (main)
>>>>>>> a0333d0 (git advanced)

Squashing combines multiple commits into a single one. Let's merge "Create second file" into "Create initial file" for a cleaner history.
Challenge: Use interactive rebasing with the squash command to achieve this. learn more about squash here

Green Way@PAU MINGW64 ~/Git-exercises (main)
$ git log
commit 481aefee1ee391a24590a512e5cef3b9a564b3d9 (HEAD -> main)
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:23 2025 +0200

    chore: Create another file

    Create second file

commit f1cfaf66854162da84154d4d014375042ca7e8ef
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:15 2025 +0200

    chore: Create initial file

Green Way@PAU MINGW64 ~/Git-exercises (main)
$ git rebase -i HEAD~2
fatal: invalid upstream 'HEAD~2'

Green Way@PAU MINGW64 ~/Git-exercises (main)
$ git rebase -i HEAD~2
fatal: invalid upstream 'HEAD~2'

Green Way@PAU MINGW64 ~/Git-exercises (main)
$ git log
commit 481aefee1ee391a24590a512e5cef3b9a564b3d9 (HEAD -> main)
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:23 2025 +0200

    chore: Create another file

    Create second file

commit f1cfaf66854162da84154d4d014375042ca7e8ef
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:15 2025 +0200

OA    chore: Create initial file

Green Way@PAU MINGW64 ~/Git-exercises (main)
OA$ git rebase -i --root
OA[detached HEAD 3982183] chore: Create initial file
OA Date: Fri Feb 28 14:44:15 2025 +0200
OA 4 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test1.md
OA create mode 100644 test2.md
 create mode 100644 test3.md
 create mode 100644 test4.md
OASuccessfully rebased and updated refs/heads/main.
OA
OAGreen Way@PAU MINGW64 ~/Git-exercises (main)
$ git log
OAcommit 3982183c5cad2b4a81ca6262167264efdc1fc68b (HEAD -> main)
OAAuthor: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:15 2025 +0200
OA
OA    chore: Create initial file

    chore: Create another file
OA
    Create second file

Green Way@PAU MINGW64 ~/Git-exercises (main)
$ git log
commit 3982183c5cad2b4a81ca6262167264efdc1fc68b (HEAD -> main)
OAAuthor: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:15 2025 +0200

    chore: Create initial file

    chore: Create another file

    Create second file

Green Way@PAU MINGW64 ~/Git-exercises (main)

Splitting a Commit in Git
Sometimes, a commit message might describe too many changes at once, like "Create third and fourth files." It’s better to separate such commits for better tracking and clarity. In this guide, we’ll learn how to split a commit using git reset and create individual commits with distinct messages.

Example Scenario:
You have a commit that says:

sql
Copy
Edit
Create third and fourth files
But you want to split this into two separate commits with different messages, such as:

"Create third file"
"Create fourth file"
Steps to Split the Commit
Check your commit history: Start by reviewing your recent commits with:

bash
Copy
Edit
git log
Example output:

sql
Copy
Edit
commit 0aabe05e25b76176ccfb01221a3783553e444546 (HEAD -> main, origin/main)
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Mon Mar 3 15:58:48 2025 +0200

    git advanced

commit a0333d03db4181fcc88aafe6361e321c0da7d5f3
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Mon Mar 3 15:51:07 2025 +0200

    git advanced

commit 3982183c5cad2b4a81ca6262167264efdc1fc68b
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:15 2025 +0200

    chore: Create initial file
    chore: Create another file
    Create second file
Reset the commit (soft reset): Use the git reset command to unstage the changes in the last commit while keeping them in the working directory.

bash
Copy
Edit
git reset --soft HEAD~1
This command will move the HEAD to the previous commit and keep all changes staged.

Stage the first file and commit: Add the changes for the third file and commit it with an appropriate message.

bash
Copy
Edit
git add test3.md
git commit -m "Create third file"
Stage the second file and commit: Add the changes for the fourth file and commit it with a new message.

bash
Copy
Edit
git add test4.md
git commit -m "Create fourth file"
Check the commit history: After splitting the commit, check your commit log again to confirm that you have two separate commits:

bash
Copy
Edit
git log
Example output:

sql
Copy
Edit
commit db4e098e2a82f447571d00d83191271fd102089c (HEAD -> main)
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Mon Mar 3 16:03:14 2025 +0200

    Create third file

commit a0333d03db4181fcc88aafe6361e321c0da7d5f3
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Mon Mar 3 15:51:07 2025 +0200

    git advanced

commit 3982183c5cad2b4a81ca6262167264efdc1fc68b
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:15 2025 +0200

    chore: Create initial file
    chore: Create another file
    Create second file
Pull the latest changes and rebase: If your branch has diverged from the remote, you may need to rebase your changes before pushing.

bash
Copy
Edit
git pull origin main --rebase
Commit the fourth file: After resolving any conflicts and ensuring your changes are up-to-date, commit the fourth file if necessary.

bash
Copy
Edit
git add test4.md
git commit -m "Create fourth file"
Final status: Verify the status to confirm there are no pending changes:

bash
Copy
Edit
git status

Copy
Edit
git add test4.md
git commit -m "Create fourth file"
Check the commit history: After splitting the commit, check your commit log again to confirm that you have two separate commits:

bash
Copy
Edit
git log
Example output:

sql
Copy
Edit
commit db4e098e2a82f447571d00d83191271fd102089c (HEAD -> main)
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Mon Mar 3 16:03:14 2025 +0200

    Create third file

commit a0333d03db4181fcc88aafe6361e321c0da7d5f3
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Mon Mar 3 15:51:07 2025 +0200

    git advanced

commit 3982183c5cad2b4a81ca6262167264efdc1fc68b
Author: Dushimepaulette1 <p.dushime1@alustudent.com>
Date:   Fri Feb 28 14:44:15 2025 +0200

    chore: Create initial file
    chore: Create another file
    Create second file
Pull the latest changes and rebase: If your branch has diverged from the remote, you may need to rebase your changes before pushing.

bash
Copy
Edit
git pull origin main --rebase
Commit the fourth file: After resolving any conflicts and ensuring your changes are up-to-date, commit the fourth file if necessary.

bash
Copy
Edit
git add test4.md
git commit -m "Create fourth file"
Final status: Verify the status to confirm there are no pending changes:

bash
Copy
Edit
git status


~
README.md[+] [dos] (11:27 04/03/2025)                                                                                                                                                                    246,1 Bot
-- INSERT --


