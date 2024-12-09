
# Git Notes

## Table of Contents
1. [Git Repository](#git-repository)
2. [Git Push Process](#git-push-process)
3. [Git Remote](#git-remote)
4. [Git Branch](#git-branch)
5. [Local to Server Workflow](#local-to-server-workflow)
6. [Server to Local Workflow](#server-to-local-workflow)
7. [Git Tags](#git-tags)
   - [Creating Tags](#creating-tags)
   - [Modifying Tags](#modifying-tags)

---
```bash
git config --global user.name "FIRST_NAME LAST_NAME"
git config --global user.email "MY_NAME@example.com"
```
---

## Git Repository

```bash
git clone <SSH/HTTPS address>          # Creates a local clone of the server repository.
git init -b {repo name}                # Creates a new local repository.
git fetch                              # Fetches all information from the server; does not merge like 'pull'.
git status                             # Shows the status of the repository.
git pull                               # Updates the repository from the server.
```

---

## Git Push Process

```bash
git add                                # Adds unstaged files to the staging area.
git rm --cached {file}                 # Reverts the 'add' command for the specified file.
git commit -m "message"                # Commits staged changes with a message.
git revert {commit ID}                 # Reverts a specific commit by its ID.
git push                               # Pushes local changes to the server.
```

- **`.gitignore`**:
  - Create this file in the repository directory.
  - Specify files or directories to exclude from `git add` by listing them line by line:
    - Example:
      ```
      *.exe
      temp/
      ```

---

## Git Remote

```bash
git remote -v                          # Shows the origin (server) address.
git remote set-url origin <new-url>    # Sets a new origin (server) address.
```

---

## Git Branch

```bash
git branch                             # Lists all local branches.
git branch -r                          # Lists all remote branches.
git switch {branch_name}               # Switches to the specified branch.
git checkout -b {branch_name}          # Creates and switches to a new branch.
git branch -d {branch_name}            # Deletes a branch locally.
git push <remote-name> <branch-name>   # Pushes a local branch to the server.
git push -u <remote-name> <branch-name># Pushes a branch and sets up tracking (stream).
git merge {branch_name}                # Merges the specified branch into the current branch.
```

- **Viewing Logs**:
  ```bash
  git log --decorate --oneline --graph --all  # Displays logs of all branches with a graph.
  ```

---

## Local to Server Workflow

```bash
git checkout -b {branch_name}                      # Creates a new branch and switches to it.
git push -u origin {branch_name}                   # Creates a remote branch with a tracking stream.
git push --set-upstream origin {branch_name}       # Push a branch to origin/branch name.
```

---

## Server to Local Workflow

```bash
git fetch origin                       # Downloads a list of newly created remote branches.
git switch {branch_name}               # Switches to the specified branch and copies it locally.
```

---

## Git Tags

### Listing and Viewing Tags

```bash
git tag                                # Lists all tags in the project.
git tag -l "v1.8.5*"                   # Lists tags matching a wildcard.
git show TAG                           # Displays details and annotations for a specific tag.
```

### Creating Tags

```bash
git tag -a TAG -m MESSAGE              # Adds an annotated tag locally.
git tag TAG                            # Adds a lightweight tag.
git tag -a TAG -m MESSAGE HASH         # Tags a specific commit with an annotated tag.
git push origin TAG                    # Pushes a specific tag to the remote.
git push origin --tags                 # Pushes all tags to the remote.
```

### Modifying Tags

```bash
git tag -f -a TAG -m MESSAGE           # Re-creates an annotated tag locally.
git tag -d TAG                         # Deletes a tag locally.
git push origin :refs/tags/TAG         # Deletes a tag on the remote server.
```
