## Git Advanced Exercises
```markdown
# Git Challenges

This repository contains a series of challenges aimed at improving your understanding and proficiency with Git.
These tasks cover common scenarios you'll encounter when working with version control.
Below is a breakdown of the challenges,
along with a brief explanation and step-by-step instructions for each task.

## 1. Missing File Fix

### Problem
You forgot to add `test4.md` to the last commit. After running `git status` and `git log`, you realize this oversight.

<<<<<<< HEAD
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
=======
### Challenge
Recover from this error by staging/adding `test4.md` and amending the commit message with an appropriate description.
>>>>>>> 8b65daf004ffbcf525fe8f10569991fee1268b48

### Steps
1. Run `git status` to verify the missing file.
2. Stage the file with `git add test4.md`.
3. Amend the last commit message using:
   ```bash
   git commit --amend
   ```
4. Modify the commit message to something descriptive and save.

---

## 2. Editing Commit History

### Problem
You need to maintain clear and accurate commit messages. The message "Create another file" is unclear and should be changed to "Create second file."

<<<<<<< HEAD
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
=======
### Challenge
Use interactive rebasing (`git rebase -i HEAD~2`) to edit the commit message and ensure clarity.
>>>>>>> 8b65daf004ffbcf525fe8f10569991fee1268b48

### Steps
1. Run:
   ```bash
   git rebase -i HEAD~2
   ```
2. Change the word `pick` to `reword` next to the commit you want to modify.
3. Edit the commit message and save.

> Learn more about [Git rebase](https://git-scm.com/book/en/v2/Git-Tools-Rebasing) for deeper understanding.

---

## 3. Keeping History Tidy - Squashing Commits

### Problem
Your history is cluttered with multiple commits that can be combined into one for a cleaner and more meaningful log.

### Challenge
Use interactive rebasing with the `squash` command to combine the commits "Create second file" and "Create initial file" into a single commit.

### Steps
1. Run:
   ```bash
   git rebase -i HEAD~2
   ```
2. Change `pick` to `squash` (or `s` for short) for the second commit.
3. Combine the commit messages and save.

> Learn more about [Squashing commits](https://www.git-scm.com/book/en/v2/Git-Tools-Rewriting-History).

---

## 4. Splitting a Commit

### Problem
The commit message "Create third and fourth files" is too vague, and you want to split it into two commits with more precise messages.

### Challenge
Use `git reset` to separate the changes into two individual commits with distinct messages.

### Steps
1. Run:
   ```bash
   git reset --soft HEAD~1
   ```
2. Stage the files for the first commit:
   ```bash
   git add <file1>
   ```
3. Commit with a specific message:
   ```bash
   git commit -m "Create Third File"
   ```
4. Stage and commit the remaining changes for the second file:
   ```bash
   git add <file2>
   git commit -m "Create Fourth File"
   ```

> Learn more about [splitting commits](https://www.git-scm.com/book/en/v2/Git-Tools-Rewriting-History).

---

## 5. Advanced Squashing

### Problem
You want to combine two commits into one, but this time, the commits contain more complex changes.

### Challenge
Use interactive rebasing to squash the last two commits ("Create third file" and "Create fourth file") into one commit with a new message: "Create third and fourth files."

### Steps
1. Run:
   ```bash
   git rebase -i HEAD~2
   ```
2. Change `pick` to `squash` for the second commit.
3. Edit the combined commit message and save.

> Check step 4 for more on [advanced squashing](https://www.git-scm.com/book/en/v2/Git-Tools-Rewriting-History).

<<<<<<< HEAD
Splitting a Commit in Git
Sometimes, a commit message might describe too many changes at once, like "Create third and fourth files." It’s better to separate such commits for better tracking and clarity. In this guide, we’ll learn how to split a commit using git reset and create individual commits with distinct messages.
<<<<<<< HEAD

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

=======
>>>>>>> fb2c0ac (updates on the readme)
=======
---
>>>>>>> 8b65daf004ffbcf525fe8f10569991fee1268b48

## 6. Dropping a Commit

### Problem
You mistakenly created a commit with unwanted changes that you need to remove from your history.

### Challenge
Use `git rebase -i` to identify and remove the "Unwanted commit" from your history. Here’s how to proceed:

### Steps
1. Create a new file named `unwanted.txt` and commit it with the message "Unwanted commit":
   ```bash
   touch unwanted.txt
   git add unwanted.txt
   git commit -m "Unwanted commit"
   ```
2. Run:
   ```bash
   git rebase -i HEAD~2
   ```
3. Change `pick` to `drop` for the unwanted commit.
4. Save and exit the rebase editor.

