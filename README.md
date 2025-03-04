## Git Advanced Exercises

```markdown
# Git Challenges

This repository contains a series of challenges aimed at improving your understanding and proficiency with Git. These tasks cover common scenarios you'll encounter when working with version control. Below is a breakdown of the challenges, along with a brief explanation and step-by-step instructions for each task.

## 1. Missing File Fix

### Problem
You forgot to add `test4.md` to the last commit. After running `git status` and `git log`, you realize this oversight.

### Challenge
Recover from this error by staging/adding `test4.md` and amending the commit message with an appropriate description.

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

### Challenge
Use interactive rebasing (`git rebase -i HEAD~2`) to edit the commit message and ensure clarity.

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

---

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
Here’s how to structure the *Reordering Commits* challenge in the same format as the previous ones:

---

## 7. Reordering Commits

### Problem
Sometimes, you may need to reorder the commits in your history to maintain a logical flow. This can be done using `git rebase -i`.

### Challenge
Use interactive rebasing (`git rebase -i`) to rearrange the commits in your Git history.

### Steps
1. Run the following command to start the interactive rebase for the last few commits:
   ```bash
   git rebase -i HEAD~<number_of_commits>
   ```
   Replace `<number_of_commits>` with the number of commits you want to reorder (e.g., `HEAD~5` for the last 5 commits).
   
2. This opens an editor listing the commits you selected. Each commit is preceded by the word `pick`.

3. To reorder commits, change the order of the commits by moving the lines around. For example:
   ```bash
   pick 1234567 Commit A
   pick 2345678 Commit B
   pick 3456789 Commit C
   ```
   If you want to swap Commit B and Commit C, simply move them in the list like this:
   ```bash
   pick 1234567 Commit A
   pick 3456789 Commit C
   pick 2345678 Commit B
   ```

4. Save and close the editor to proceed with the rebase. Git will attempt to apply the commits in the new order.

5. If there are no conflicts, the rebase will complete successfully. If there are conflicts, Git will prompt you to resolve them. After resolving conflicts, use:
   ```bash
   git rebase --continue
   ```

6. After successfully completing the rebase, verify the commit order by checking the commit log:
   ```bash
   git log --oneline
   ```
