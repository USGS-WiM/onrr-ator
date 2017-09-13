# onrr-ator

> [Yeoman](http://yeoman.io) generator for scaffolding html5/javascript web mappinng apps.  Allows for use of [ESRI](https://developers.arcgis.com/javascript/) as the mapping API.   It uses npm for dependency injection and gulp as its task runner.


## Generator installation

#### 1.  Install required software (see Getting Started above before proceeding)
[node.js](https://nodejs.org)  
[git](https://windows.github.com/)

#### 2.  Install yeoman
This will install the following packages globally (to your "C:\Users\%user%\AppData\Roaming\npm\node_modules" folder.)  This can be done from any command prompt

```bash
npm install -g yo
```

#### 3.  Clone 'onrr-ator' repo
Create a local copy of the generator

```bash
git clone https://github.com/USGS-WiM/onrr-ator.git
```

#### 4.  Create symbolic link for onrr-ator inside the onrr-ator folder
This 'tricks' node into thinking your onrr-ator is a globally installed node module in this location: "C:\Users\%user%\AppData\Roaming\npm\node_modules"

```bash
cd onrr-ator
npm install
npm link
```

#### 5.  Run the generator to create a new app
Create a new folder for the generated app and run the generator

```bash
md new-app
cd new-app
yo onrr
```

## Updating the generator source and dependencies

#### 1.  Get latest code from github
```bash
cd onrr-ator
git pull origin master
```
#### 2.  Update dependencies
```bash
npm update
```

---
## Editing the generator itself
The process described below is for making edits to the actual generator code, i.e. the source from which all generated apps will be generated. Exercise caution, as these edits will affect all future generations.

###1. Ensure that your local repo of generator-wim is up-to-date
run a pull  from the upstream at your local repo directory to retrieve latest from the org repo at [USGS-WiM/onrr-ator](https://github.com/USGS-WiM/onrr-ator).
```bash
cd onrr-ator
git pull origin master
```

If you have conflicts after you pull the latest code, it is recommended to install and configure a windows mergetool for git.   [p4merge](http://www.perforce.com/product/components/perforce-visual-merge-and-diff-tools) seems to work OK.  [Here is some help](https://www.perforce.com/perforce/doc.current/manuals/p4v/merging_files.html) on using it to compare diffs from git.  The commands to set it up with git:
```bash
git config --global merge.tool p4merge
git config --global mergetool.p4merge.cmd "C:\\Users\\%username%\\Perforce\\p4merge.exe \"$BASE\" \"$LOCAL\"
\"$REMOTE\" \"$MERGED\""
```

 For good housekeeping, follow up your upstream pull with a push to your personal account repo so it is in sync with the org repo at [USGS-WiM/onrr-ator](https://github.com/USGS-WiM/onrr-ator).

```bash
git push origin master
```

###2. Generate a new app instance for development

Create a new directory for generator code development. Something like "onrr-ator-dev" is recommended. You only need to do this the first time. You can always generate an app there later which will overwrite older code.

in your generator dev directory, run the yeoman command with the alias for the onrr-ator
```bash
yo onrr
```
follow the prompts, and eventually you will have app code in your dev directory, whose contents should now contain the follwoing files:
```bash
node_modules src .gitignore .jshintrc gulpfile.js package.json
```

###3. Develop
**You can now make edits and do development on the files in the src directory.** When ready to test, run the gulp watch command to view the app in the browser using a  lightweight node-js webserver environment.
```bash
gulp watch
```
This connection is live and will update automatically as changes are made to code. To execute other commands, you will need to escape the active webserver with `CTRL + C`

###4. Do a test build
When satisfied with your changes, test them in the build environment by running the build command. Currently, the base gulp command is configured to default to "gulp build".
```bash
gulp
```
This will create a build folder including minified and combined dependency libraries. Open the app from the build folder as a final test of your changes.

###5. Create a new branch in 'onrr-ator'
Create a new branch of the cloned repo that will contain your changes
```bash
git checkout -b 'branch-name'
```

###6. Copy changes from test instance back to the onrr-ator repo
Copy content from your edited files into their counterparts in the local onrr-ator repo. Files are located at `onrr-ator/app/templates` and can be identified by the leading underscore in their names. E.g. "_index.html", "_core.js" and "_main.css"

###7. Submit new branch back to USGS-WiM 'onrr-ator' repo
```bash
git add .
git commit -m 'message describing your updates'
git push origin 'new_branch_name'
```
