How to create and deploy a Webpack app on Github Pages

1.  Create an empty repository on GitHub with any "reponame"
    really empty no README.md file, .gitignore file, LICENSE file, or any other files.

2.  Create a Webpack app on local machine:
    appname can be any name or same as reponame. I prefer same names.

3.  Install the gh-pages package as a "dev-dependency" of the your react app:

    "npm install gh-pages --save-dev"

4.  In package.json add "homepage" property:

        "homepage": "http://github-username.github.io/reponame"    ( note no ".git" with reponame)

    for msaudagar and "hackernews" the above becomes:
    "homepage": "http://msaudagar.github.io/hackernews"

5.  In package.json's "scripts" propery add following 2 items:

    "deploy": "npm run build && gh-pages -d dist"

    (this assumes that the build folder is named "dist" )

6.  Note that new versions of create-react-app automatically create a git repository. If it is not created the areate a git repository in the app's folder using:
    "git init"

7.  run following to connect local git repository to "remote" (the one created in step-1):

        "git remote add origin https://github.com/username/repo-name.git"

    for msaudagar and "react-calculator.git" the above becomes:
    "git remote add origin https://github.com/msaudagar/react-calculator.git"

7a. if a remote is already connected to some origin and you like to connect it to current local git repository then first remove existing connection by:
"git remote rm origin"
then use the command given above e.g.: "git remote add origin https://github.com/msaudagar/react-calculator.git"

8.  Generate a production build of your app, and deploy it to GitHub Pages by simply running following script:

        "npm run deploy"

    ( it will create a "dist" directory in local app with transpiled code and the same command will deploy content of "dist" to github in the repository that was created in step-1)

Steps 1 through 8 will will only transfer the "dist" content to your github reponame. The source contents are not transferred. 9. You can "push" the source contents by following commands:

$ git add .
$ git commit -m "Commit Message"
$ git push -u origin master
(for new versions of GIT (on your machine) "master" is changed to "main"). If your machine still has old GIT then use "master"
(note initially do use these command)

for pushing all branches
$ git push --all origin

Note that 'origin' is the alias for a 'remote' repository ('origin is actually the url of a remote repository)

10. Every time you when you make edits to your local files you need run "npm run deploy" so that ne "build" is created and deployed to remote.

11. As usual for saving the edits (changes) locally use "commit" changes and to sync with "remote" use "push"
    c. push changes

12. just as reminder the website github creates for the app is (it is written by you in package.json):

        "http://github-username.github.io/reponame"

    for msaudagar and "hackernews.git" the above becomes:
    "http://msaudagar.github.io/hackernews"
