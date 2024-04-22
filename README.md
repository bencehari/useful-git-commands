# Useful git commands

> **Comment:** "[remote]" will be "origin" most of the time.

- `git fetch`  
  Fetches changes from remote (should always start with this one)
- `git fetch [remote] --prune`  
  After fetching, remove any remote-tracking branches which no longer exist on the remote
  - Shortcut: `git fetch -p`
- `git status`  
  Check changes, untracked files, etc.
- `git pull`  
  Pull all changes from the remote
  - If pulling fails due to conflicts (and there is no local commit):
    - `git checkout -b [local-backup-branch]`  
      "Move" changes to a new branch
    - commit local changes to [local-backup-branch]  
      "Save" changes to the new branch
    - `git checkout [original-branch]`  
      Go back to the original modified branch
    - `git checkout .` and `git clean -fd`  
      Delete local changes (they are in [local-backup-branch])
    - `git pull`  
      Pull the changes from [remote]
    - `git merge [local-backup-branch]`  
      Merge local changes, resolve conflicts locally
    - `git branch -D [local-backup-branch]`  
      Clean-up
- `git branch`  
  Shows all local branches
- `git branch -a`  
  Shows all local and remote branches
- `git checkout .`  
  Discards all local file modifications
- `git clean -fd`  
  Discards added files and folders (f - files, d - folders)
- `git add .`  
  Stage all changes
- `git add [rel-path-to-file-1] [rel-path-to-file-2] [rel-path-to-file-3]`  
  Stage selected file(s). Can be much simpler to use a GUI for this.
- `git commit -m "messge"`  
  Commits staged (added) changes with message. Add message. Add meaningful message!
- `git commit -m "message1" -m "message2"`  
  Commits staged changes with additional message. If message1 would be too long.
- `git commit --amend -m "message"`  
  Adds new staged changes to last commit with new message (replaces commit with a new one).  
  Without additional changes, it will change only the message.
- `git commit --amend -C HEAD`  
  Same as above, but leave the message unchanged.
- `git push`  
  Pushes local commits to the remote.
- `git push -u [remote] [new-local-branch]`  
  Push new local branch to remote.
- `git log -[x]`  
  Shows the last [x] number of commits in the active branch.
- `git reset --soft [commit-hash]`  
  Goes to the commit provided by hash, and place all changes after that to stash.
- `git reset --hard [commit-hash]`  
  Goes to the commit provided by hash, and deletes all changes after that.

### Sometimes needed

Remove all committed files after adding them to .gitignore:

- `git rm -r --cached .`  
  After `git status`, everything should be green. This is good, don't panic.
- `git add .`  
  Add everything (files newly excluded won't added back)
- `git commit -m "XY files/files with extensions removed"`  
  Commit the changes. With a meaningful message, of course.

Delete remote branch (if you have permission):

- `git push -d [remote] [branch-name]`

### One-time stuff

- Global
  - `git config --global user.email [your-email]`  
    Set e-mail for repository
  - `git config --global user.name [your-name]`  
    Set user name for repository
- Repository only
  - `git config user.email [your-email]`  
    Set e-mail for repository
  - `git config user.name <your-name>`  
    Set user name for repository
