# GIT Notes

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

- Remotes are simply an alias that store the URL of repositories. You can see what URL belongs to each remote by using `git remote -v`

- 'remote' is just a word in Git commands. 'remote', in git-speak, refers to any remote repository, such as your GitHub or another git server.

- When you do git push -u origin master, what it means is "push everything from my local master to the remote named origin".
  The structure of this command is, of course, more general - the more general form is "git push -u <remote> <branch>",
  which will push the branch named branch to the designated remote, creating it at the far end if the remote doesn't already have it (that's what the -u flag does).

- You can have multiple remotes. Usually for a primary 'remote repository' the alias 'origin' is used. Of course multiple remotes we have to use multiple aliases.

- If we do not define aliases for 'remotes' then we will need to write full url of remotes in Git commands that interact with remote repositories.
