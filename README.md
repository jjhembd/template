# Template

Basic structure for a new module

## Building a new module:
0. Make sure you have GPG signing set up. Check that you have a key
   ```bash
   # gpg --list-keys
   ```
   If not, generate one. Make sure to remember your passphrase!
   ```bash
   # gpg --gen-key
   ```
   Now make sure Git can use it. It needs an environment variable. To check:
   ```bash
   # echo $GPG_TTY
   ```
   It should be something like /dev/tty1. If not, go to your ~/.bashrc, add
   the following line, and restart all your terminals:
   ```bash
   # export GPG_TTY=$(tty)
   ```
   Now make sure NPM will sign Git tags when bumping the version. Execute
   ```bash
   # npm get sign-git-tag
   ```
   If not true, set it globally:
   ```bash
   # npm config set sign-git-tag true --global
   ```
1. Recreate the folder structure as in this directory.
   Note: some (e.g. Leaflet) put examples/ inside docs/, presumably
   because you can point GitHub Pages to docs/.
   Put main JS file in src/main.js (as per rollup.config. Some use index.js?)
2. Write a README.md !! NOTE that the first line (separated by two blank lines)
   will become the "description" in the package.json
3. Initialize Git ($ git init). Don't forget to copy the .gitignore file
4. Create the repository on GitHub (DON'T add .gitignore or license), add the
   remote origin in Git:
   ```bash
   # git remote add origin https://github.com/\<username>/\<module name>.git
   ```
   and track the branch:
   ```bash
   # git branch --set-upstream-to origin/master
   ```
5. Initialize NPM (`npm init`). Pay attention to:
   - entry point: in dist folder
   - keywords
6.  Modify the package.json as follows: (TODO: automate this)
   - Set directories to an empty set
7. Install default dev dependencies from the template package.json:
   ```bash
   # npm install
   ```

## TODO
- Figure out peer dependencies
- Update ~/.npm-init.js to get a better npm init process. See
  https://devdocs.io/npm/getting-started/using-a-package.json
  Maybe see https://docs.npmjs.com/cli/init
- Test git pull? or fork? to start a new module from this template
- Figure out how to update versions: in package.json, git tags, etc
  See Leaflet's build/publish.sh ? Note: uses rollup-plugin-git-version
  OR check https://docs.npmjs.com/cli/version.html
