# GIT Notes

## GIT Basics

### Initialization Realted

- configure email: `git config --global user.email useremail`

- configure name: `git config --global user.name username`

- `git init path` creates .git in path directory. `git init` creates .git in current directory.

- To clone a repository from github: `git clone https://www.github.com/username/repo-name`

### To clone a project which is on local machine to another on local machine as well

- `git clone source-project-path destination-project-path`

- Run `npm install` after cloning any Nodejs project (from local machine or from a remote url) to install dependencies given in package.json and package-lock.json.

### Staging Related

- To list status of modified and staged file: `git status`
- To stage a file: `git add filename`
- To stage all modified files: `git add .`
- To un-stage a file: `git reset filename`
- To unstage all files: `git reset`

### Commit Related

- To commit all staged changes: `git commit -m "Commit message"`
- To stage and commit in one step: `git commit -a -m "Commit message"`
- To display commit history: `git log`
- To display commit history each commit on one line: `git log --oneline`

### Branch Related

- To create a branch with branchname: `git branch new-branch`
- To switch to an existing branch: `git checkout existing-branch`
- To create a branch and switch to it: `git checkout -b new-branch`

- copy a file/folder from another branch

- `git checkout branch_A -- Folder\Folder1\file.txt`

### Merge Related

- To merge branch-2 in branch-1 first we need to switch to branch-1. Then use: `git merge branch-2`
- If branch-1 had no new commits while branch-2 got new commits then it is a fast-forward Merge
- In a fast-forward merge simply the additional commits of merged branch are added to the mreged to branch. No new commit is created.
- In a general merge where there are changes in both branches there could be conflict and no-conflict cases.
- In no-conflict case branches are mereged with an additional commit allowing to write a commit message (e.g. describing the changes).
- Git compare at line level, i.e. line by line. If there are conflicts Git will flag that automatic merge failed.
- The conflicts are in the existing lines with different edits. Added lines in either branch do not cause conflicts.
- If automatic merge fails the to abort merge use: `git merge --abort`
- In case of conflict go to the file(s) and resolve the conflicts manually.

### Rebase Related

- The purpose of 'rebase' is similar to 'merge'

### Working with a repository on Github (or Gitlab etc.)

There can be following cases:

- If user is owner of the repository or has write access to it then just 'clone' it directly to his local machine and push to it. This is not recommended workflow.

- If the repository doesn't belong to user and he has no write-access then he has to copy the repository in his account on Github by 'forking' it. Once forked the original is referred to as 'upstream'. The user now clone his copy of upstream to his local machine and works as usual.
- forking is available on Github but it is not available on BitBucket. Only direct collaborators allowed.

### Push related

- the push first argument is 'remotename' (usually 'origin') and second is the 'branch to be pushed'
- To push changes to origin: `git push origin branchname` (on remote branch will be created if not there)
- you don't need to be in the branch being pushed.
- To push all branches: `git push --all origin`
- git push command will only be successful if it can do a fast-forward merge with the remote branch(es). i.e. if there are no conflicts.
- you can force a push by `git push origin branchname --force` but it is not recommended.

### Fetch and Remote Tracking Branches

- Beside local branches, there is a set of copies of remote branches ('remote tracking branches (RTB)') in user's local git repository
- RTB is also called "local copy of the remote repository"
- RTB are not visible or accessable to user directly
- `git fetch` sync RTB with the current state of branches on default remote.
- general fetch is `git fetch remote-alias branchname` 'origin' is used if remote-alias not given. Current branch is used if not specified.
- `git fetch --all` fetches all branches from all remotes into the corresponding remote tracking branches space.
- In simple words `git fetch` says "bring my local copy of the remote repository up to date."
- The references for the local branches are stored in the /.git/refs/heads/
- Remote branch references are stored in the ./.git/refs/remotes/
- `git fetch` just gets the new changes so any deleted file on remote is not deleted from local remote tracking branches
- `git fetch -p` (p for prune) remove from RTB the branches which are deleted on the remote. Good way of syncing and cleaning.

### Pull Related

- To pull a branch from remote (e.g. 'origin'): `git pull origin branchname`
- In reality `git pull` is a combination of `git fetch` followed by `git merge`
- If there are no changes in local branch, `git pull` will merge the remote branch changes to it in a fast-forward way.

### Pull Requests

- A pull request allows you to send the owner of the remote repository a request to pull in your changes
- Users should not push their changes to remote directly. They should generate "pull requests" to start a code-review process
- Most teams use master/main branch as their production code which they release to public. So changes to main/master is carefully scrutinized via pull-request based code-review process.
- A pull request (PR) from user1 to remote is a request to pull user1's modifications for code-review purpose.

- A typical work flow is that user1 branch out from main/master to some feature branch, then work on that and when ready on his side he push it (the feature branch) and then create a PR. If PR is approved then feature branch is merged into main/master (usually the feature branch may then be deleted)

### Understand 'origin' and 'remote'

- 'origin' is an alias on your system for a particular remote repository. It's not actually a property of that (remote) repository.

- There's no requirement to name the remote repository 'origin': in fact the same repository could have a different alias for another developer.

- In simple words "origin" is just the nickname you have given to your remote repository in your local .git when you ran a command like this:

  `git remote add origin https://github.com/username/repo-name.git`

  or

  `git remote add origin https://github.com/msaudagar/react-calculator.git`

  (note in this command we could use any other name in place of origin)
  From then on Git knows that "origin" points to that specific repository (in this case a GitHub repository). You could have named it "github" or "repo" or whatever you wanted.

- if a remote is already connected to some origin and you like to connect it to current local git repository then first remove existing connection by:
  `git remote rm origin`
  then use the command given above e.g.:
  `git remote add origin https://github.com/msaudagar/react-calculator.git`

- Remotes are simply aliases that store the URL of repositories. You can see what URL belongs to each remote by using `git remote -v`

- 'remote' is just a word in Git commands. 'remote', in git-speak, refers to any remote repository, such as your GitHub or another git server.

- When you do git push -u origin master, what it means is "push everything from my local master to the remote named origin".
  The structure of this command is, of course, more general - the more general form is "git push -u <remote> <branch>",
  which will push the branch named branch to the designated remote, creating it at the far end if the remote doesn't already have it (that's what the -u flag does).

- You can have multiple remotes. Usually for a primary 'remote repository' the alias 'origin' is used. Of course multiple remotes we have to use multiple aliases. In commands that require remote argument, 'origin' (or the first defined remote) will be used as the default remote.

- If we do not define aliases for 'remotes' then we will need to write full url of remotes in Git commands that interact with remote repositories.
