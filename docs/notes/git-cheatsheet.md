# Git cheat sheet

> Starter list from John. **Fill in the "What it does" column yourself, in your own words.** Try each command in
> a scratch repo before you write its line. Add commands as you meet them. Save this as
> `docs/notes/git-cheatsheet.md` and commit it on a `docs/` branch.

## Where am I? (run these constantly)

| Command | What it does (my words) |
| --- | --- |
| `git status` | tells you what branch you are on and the status of the files in said branch |
| `git branch` | lists your local branches and marks the one you are on with a `*` |
| `git branch -a` | tells you what branch you are on and shows you all other branches, including the ones on GitHub |
| `git log --oneline --graph --all` | makes a graph of all the commits in the repo, across every branch |
| `git diff` | shows changes in your working tree that aren't staged yet |
| `git diff --staged` | compares your staged changes to your last commit |

Tip: the current branch is also shown in VS Code's bottom-left status bar and in the Git Bash prompt.

## Start work

| Command | What it does (my words) |
| --- | --- |
| `git switch main` | switches you to main lol |
| `git pull` | pulls the latest version of the branch you are on from GitHub |
| `git switch -c docs/my-change` | switches you to a new branch and names it |

## Save work

| Command | What it does (my words) |
| --- | --- |
| `git add <file>` | adds the named file to the staging area |
| `git add -p` | lets you stage "chunks" of a file |
| `git commit -m "Add …"` | save your changes locally and leave a message |
| `git push -u origin docs/my-change` | push your commits to GitHub, to the specific remote branch you named. `-u` remembers the link so next time you can just type `git push` |
| `git push` | push your commits to the branch you are on in GitHub |

## Connect to GitHub

| Command | What it does (my words) |
| --- | --- |
| `git remote -v` | lists your remotes: the nickname (like `origin`) and its URL |
| `git remote add origin <url>` | link your local repo to a remote repo and nickname it `origin` |
| `git push -u origin --all` | pushes all your branches to the remote repo named origin |
| `git branch -M main` | renames the current branch to main, even if a main exists already |

## Bring in other work

| Command | What it does (my words) |
| --- | --- |
| `git fetch` | downloads what's new from GitHub without changing your files or branches |
| `git merge main` | merge main into the branch you are on |
| `git merge --abort` | cancel the merge and revert back |
| `git merge <branch>` (local, no PR) | the history of the branch you're on is updated to include the commits from the merged branch |

## Undo (read the warnings before running these)

| Command | What it does (my words) |
| --- | --- |
| `git restore <file>` | discards any uncommitted changes in that file. WARNING: permanent, there is no undo |
| `git restore --staged <file>` | moves the file out of the staging area without touching it |
| `git commit --amend` | saves over the last commit, replacing it. WARNING: don't use it on a commit you already pushed |
| `git revert <commit>` | undoes the commit without deleting the history |
| `git stash` / `git stash pop` | stash grabs all your uncommitted work on tracked files and saves it on a "shelf" so you can do pop later and place it in another branch or something |

## Investigate history

| Command | What it does (my words) |
| --- | --- |
| `git log --oneline -- <file>` | gives a brief history of the commits of that file |
| `git show <commit>` | shows the details of that commit |
| `git blame <file>` | shows who did what to each line and when they did it |
| `git grep "<text>"` | search the repo for the string |
| `git log -S "<text>"` | search for the commits that added or removed the string |
| `git log -S "<text>" -m` | the `-m` lets the search include merge commits, which are ignored by default |
| `git grep -E "<text1>\|<text2>"` | searches all tracked files for either of the texts on each side of the pipe |

## Clean up

| Command | What it does (my words) |
| --- | --- |
| `git branch -d <branch>` | deletes the branch if it's already merged |
| `git fetch --prune` | deletes your local records of branches that were deleted from the GitHub repo |
| `[gone]` in `git status -sb` or `git branch -vv` | the remote branch was deleted (my local copy is still there, so it's safe to delete it) |

## Terminal

| Command | What it does (my words) |
| --- | --- |
| `unzip <file>` | extracts the contents of a ZIP file into the current folder |
| `dig +short <name> <type>` | looks up a DNS record for a name; `+short` gives a clean answer, like just the IP |

## Setup (once per machine)

| Command | What it does (my words) |
| --- | --- |
| `git config --global user.name "Your Name"` | it sets your name on each of your future commits |
| `git config --global user.email "you@example.com"` | sets your email on each of your commits |
| `git config --list` | shows you all the config settings |

## Reading command syntax

| Pattern | Meaning |
| --- | --- |
| `<file>` | a placeholder: replace it with the real file name (don't type the `<` `>`) |
| `[--option]` | an option but not needed|
| `-m` vs `--message` | the same thing, so just use -m lol|
| `HEAD` | where i am currently|
| `origin` | default nickname for remote repo|
| `origin/main` vs `main` | main is on my pc, origin/main is the local last record of main from github pulled|

## Questions I still have

-
