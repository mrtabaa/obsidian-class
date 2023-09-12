**Git using VS-Code tool**
[How to use Git inside of VSCode - 2020](https://www.youtube.com/watch?v=F2DBSH2VoHQ)

**IMPORTANT NOTE:**
Make sure the name of your project and repository match!

##### INSTALLATION:
1. Install
```bash
sudo dnf install git
```
2. Restart VS-Code
##### Set Global User
Set Email
```bash
git config --global user.name 'Reza Taba'
```

Set Name
```bash
git config --global user.email '<mrtabaa@gmail.com>'
```

Unser Email or Name
```bash
git config --global --unset user.name
```

See set values:
```bash
git config --list
```

Reset configs
```bash
rm ~/.gitconfig
```
##### GIT COMMANDS using Terminal:

1. Remove Client's git folder/files
2. Put [.gitignore](https://github.com/mrtabaa/HealthApp/blob/dotnet6/.gitignore) in your project's root folder
3. **git init :** Sets the desired folder as the initialized folder to work on.
4. Commit as First setup message
5. Push first git OR Publish to github

NOTE: 
Name the repo exactly the same as the project root folder

Back to [Project Steps](obsidian://open?vault=Advance%20Class&file=Programming%2F0%20-%20Project%20Steps)

-------------------------------------

**Verbs/Commands:**

LOCAL
**stage** a change with **+** sign
**unstage** a change with **-** sign
**commit** a **staged change** to git. Message is important

INTERNET
**push** commits to GitHub server
**pull** commits from GitHub server
**clone** the whole repository to your computer

-------------------------------------


**IF USING TERMINAL/CMD/BASH**

###### DOWNLOAD
```bash
git clone https://github.com/user-name/proj-name.git
```
 
###### RESTORE DELETED FILES (Unstaged)
```bash
git restore .
```

###### Login to github
[Reza's solution - Stack Overflow](https://stackoverflow.com/a/77085369/3944285)

###### ADD TO STAGE
* Make sure you have no .git folder in your project's sub-directories!

Adds index.html file to stage
```bash
git add index.html 
```

Adds all the html files only to stage
```bash
git add *.html 
```

Adds all files of the folder at once using **dot**
```bash
git add .
```
###### REMOVE FROM STAGE

Removes the file from stage
```bash
git rm --cached index.html
```

Removes all files from stage with **dot** and **-r**
```bash
git rm --cached . -r
```

###### STATUS OF STAGE

Shows the status the stage (files, changes, etc.).
```bash
git status
```
###### COMMIT COMMENTS
```bash
git commit
```
Enter **Esc + :wq** to exit from commit if commit was used without **-m** flag.
**OR**
Commit a message for your changes.
```bash
git commit -m 'this is my message'
```

###### BRANCH

Creates a new branch called **login** so we don't change the final codes of the **master** branch.
```bash
git branch login
```
Go to **login** branch
```bash
git checkout login 
```

Merges all the codes of **login** with **master** for final release.
```bash
git merge login
```

###### REMOTE
```bash
git remote add origin https://github.com/mrtabaa/mosh-example.git
```

Removes the origin remote
```bash
git remote rm origin
```

Shows all remote repositories.
```bash
git remote
```

###### UPLOAD TO Files ONLY
Uploades data to the remote repository under `master` branch.
```bash
git push -u origin master
```

We can use **push** from now on to upload.
```bash
git push
```

###### UPLOAD TO GITHUB PAGES using JavaScript
1. Install ghp uploader
```bash
npm install -g angular-cli-ghpages 
```

2. Upload to GitHubPage
```bash
ng build --prod --base-href="https://mrtabaa.github.io/project-name/"
```

3. If getting running scripts is disabled on this system Run this in terminal
```bash
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope CurrentUser
```

4. Now upload the page
```bash
ngh --dir dist/project-name
```

Or set this shortcut in **package.json**

```ts
"deploy:gh": "ng build --prod --base-href='https://mrtabaa.github.io/project-name/' && ngh --dir dist/project-name",
```

5. Then 
```bash
npm run deploy:gh
```

###### IGNORE / EXCLUDE

**To ignore files/folders from staging:** [Watch this video](https://youtu.be/SWYqp7iY_Tc?t=1092)

NOTE:
Under GitHub Pages settings, change the folder from /root to /docs
###### Deploy:
[Deploy the angular application on GitHub](https://www.youtube.com/watch?v=wElk1W1BJ2o)