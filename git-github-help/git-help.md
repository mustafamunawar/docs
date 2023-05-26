# GIT Notes

## GIT Basics

### Understand refs, heads and HEAD

- In Git you have many brances. Each branch has many commits. The "tip" or the most recent commit of a branch is its "head".

- In Git, a "ref" is a human readable name that references a Git commit ID. A ref is essentially a pointer to a commit. Examples of refs are Git branch names such as "main" and "dev". Another example of refs are Git tags such as v0.1 or v0.2. You can think of each of these as a variable name that points to a commit ID. The commit ID that a ref points to is dynamic so it can change over time.

- When representing a branch name, a "ref" such as "main" (previously called "master") represents the tip (most recent commit ID) on that branch. Refs are stored in a special hidden location in your Git repository at the path .git/refs/.

- In Git, a "head" (not HEAD) is a ref that points to the tip (latest commit) of a branch. You can view your repository’s heads in the path .git/refs/heads/. In this path you will find one file for each branch, and the content in each file will be the commit ID of the tip (most recent commit) of that branch.

- For example, there is literally a file called "main" in that path that contains the commit ID of the tip of the "main" branch. When you make a new commit on a branch or pull commits from a remote, the head file for that branch is always updated to reflect the commit ID of the tip of the branch. In this way, your branch name ref always stays in sync with the most recent commit at the tip of the branch.

- HEAD is a special ref that points to the commit you are currently working on - the currently checked out commit in your Git working directory. You can think of it as a global variable or environment variable within your Git repo that can change depending on which commit you've checked out in your working directory. It is stored in a file called .git/HEAD. Check its content by:

```shell
$ cat .git/HEAD
ref: refs/heads/master
```

- In lowercase, "head" is a general term that means any commit that represents a branch tip. In uppercase, "HEAD" is a specific Git ref that always points to the commit currently checked out in the working directory.

- `git checkout <commit ID>` take you to any previous commit but then you are in a detached HEAD situation. Why? because HEAD is supposed to be a pointer to tip/head commit of a branch not to any earlier commit(s).

- When working with Git, only one branch can be checked out at a time - and this is what's called the "HEAD" branch. Often, this is also referred to as the "active" or "current" branch.

- Git makes note of this current branch in a file located inside the Git repository, in .git/HEAD. (This is an internal file, so it should not be manually manipulated!)
  If you wonder what exactly this file contains, you can simply have its contents printed on the command line:

```shell
$ cat .git/HEAD
ref: refs/heads/master
```

- In rare cases, the HEAD file does NOT contain a branch reference, but a SHA-1 value of a specific revision. This happens when you checkout a specific commit, tag, or remote branch. Your repository is then in a state called "Detached HEAD".

### Initialization Realted

- configure email: `git config --global user.email useremail`

- configure name: `git config --global user.name username`

- `git init path` creates .git in path directory. `git init` creates .git in current directory.

- To clone a repository from github: `git clone https://www.github.com/username/repo-name`

### To clone a project which is on local machine to another on local machine as well

- `git clone source-project-path destination-project-path`

- a better way to go in destination folder and:

- `git clone source-project-path new-name-for-cloned-project` note only new name not the path because you are already in destination folder. This will clone all remote tracking branches but only the currently active branch.

- in order to clone all local branches as well use --mirror option like:

- `git clone --mirror source-project-path new-name-for-cloned-project`

- You may need to initialize git whether by `git init` or by vscode initialize git repository button. You also need to make an initial commit

-

- Run `npm install` after cloning any Nodejs project (from local machine or from a remote url) to install dependencies given in package.json and package-lock.json.

### Staging Related

- To list status of modified and staged file: `git status`
- To stage a file: `git add filename`
- To stage all modified files: `git add .`
- To un-stage a file: `git reset filename`
- To unstage all files: `git reset`
- To unmodify all changes: `git reset --hard`

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

- If the repository doesn't belong to user and he has no write-access then he has to copy the repository in his account on Github by 'forking' it. Once
  forked the original is referred to as 'upstream'. The user now clone his copy of upstream to his local machine and works as usual.

- forking is available on Github but it is not available on BitBucket. Only direct collaborators allowed.

### Git Clone details

- When you clone a repository through Git it clones a repository into a newly created directory, creates remote-tracking branches for each branch in the cloned repository (can be listed using git branch -r), `and creates and checks out an initial branch that is forked from the cloned repository’s currently active branch`. It looks like we only have access to the main branch locally and that we have to remotely checkout the other branches. The Git already has tracking information for all the remote branches following the clone. We can access any of the branches with a simple checkout `git checkout branchname`.

- if you want other than remote's currently active branch then use `git clone --branch <branchname> <remote-repo-url>`. It will create RTB for all branches of remote but checks out the specified branch in local workspace.

- if you reall like to clone only one branch (ond RTB for only that branch) then use:
  `git clone --branch <branchname> --single-branch <remote-repo-url>` . Note `--branch` can be replaced by the short `-b`

### Push related

- the push first argument is 'remotename' (usually 'origin') and second is the 'branch to be pushed'
- To push changes to origin: `git push origin branchname` (on remote branch will be created if not there)
- you don't need to be in the branch being pushed.
- To push all branches: `git push --all origin`
- git push command will only be successful if it can do a fast-forward merge with the remote branch(es). i.e. if there are no conflicts.
- you can force a push by `git push origin branchname --force` but it is not recommended.

### Fetch and Remote Tracking Branches

- The git fetch command downloads objects to the local machine without overwriting existing local code in the current branch. The command pulls a record of remote repository changes, allowing insight into progress history before adjustments. Git isolates the fetched content from the local code. Therefore, the fetch provides a safe way to review the information before committing to your local branch.

- `git fetch <options> <remote name> <branch name>` By default all branches of a remote are fetched. If remote is not given "origin" is used.

- to fetch from all remotes use --all option.

- use `git fetch --help` to get details of fetch command

- Beside local branches, there is a set of copies of remote branches ('remote tracking branches (RTB)') in user's local git repository

- local branches references are stored in `.git/refs/heads` and RTB references are stored in `.git/refs/remotes`

- You can list RTB by `git branch -r`

- when you clone from a repo from Github, Git’s clone command automatically names it (i.e. the repo) "origin" for you, pulls down all its data, creates a pointer to where its "main" branch is, and names it origin/main locally. Git also gives you your own local master branch starting at the same place as origin’s main branch. From here the "origin/main" and local "main" can be modified differently.

- as long as you stay out of contact with your origin server, your origin/master pointer doesn’t move.

- RTB are updated with the `git fetch` command.

- When you `git fetch origin` then git synchronizes with origin and moves your origin/main pointer to its new, more up-to-date position. Note `fetch` does not update/synchronize the loacal "main" with `fetch` command. The `fetch` will not modify your working directory at all. It will simply get the data for you and you need to use the `merge` command to bring working directory up to date.

- The `pull` commanad execute `fetch` and `merge` in one shot.

- Checking out a local branch from a remote-tracking branch automatically creates what is called a “tracking branch” (and the branch it tracks is called an “upstream branch”). Tracking branches are local branches that have a direct relationship to a remote branch. If you’re on a tracking branch and type git pull, Git automatically knows which server to fetch from and which branch to merge in.

- The git pull command is only useful when there is already a local branch to merge the changes into. What about a branch that exists on the remote, but doesn't have a corresponding local branch yet?

- The git checkout --track command can be used to create a new local branch based on the remote branch, and to set the local branch's upstream correctly so that git pull will do the right thing in future.

- When you clone a repository, it generally automatically creates a main branch that tracks origin/main. However, you can set up other tracking branches if you wish — ones that track branches on other remotes, or don’t track the main branch.

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

# Rough Stuff
