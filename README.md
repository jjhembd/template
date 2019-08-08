# Template

Basic structure for a new module

## Building a new module
0. Make sure you have GPG signing set up. Check that you have a key
   ```bash
   gpg --list-keys
   ```
   If not, generate one. Make sure to remember your passphrase!
   ```bash
   gpg --gen-key
   ```
   Now make sure Git can use it. It needs an environment variable. To check:
   ```bash
   echo $GPG_TTY
   ```
   It should be something like /dev/tty1. If not, go to your ~/.bashrc, add
   the following line, and restart all your terminals:
   ```bash
   export GPG_TTY=$(tty)
   ```
   Now make sure NPM will sign Git tags when bumping the version. Execute
   ```bash
   npm get sign-git-tag
   ```
   If not true, set it globally:
   ```bash
   npm config set sign-git-tag true --global
   ```
1. Recreate the folder structure as in this directory.
   Note: some (e.g. Leaflet) put examples/ inside docs/, presumably
   because you can point GitHub Pages to docs/.
   Put main JS file in src/main.js (as per rollup.config. Some use index.js?)
2. Write a README.md !! NOTE that the first line (separated by two blank lines)
   will become the "description" in the package.json
3. Initialize Git ($ git init). Don't forget to copy the .gitignore file
4. Create the repository on GitHub (DON'T add .gitignore or license), and add
   the remote origin in Git:
   ```bash
   git remote add origin https://github.com/\<username>/\<module name>.git
   ```
5. Initialize NPM (`npm init`). Pay attention to:
   - entry point: in dist folder
   - keywords
6. Modify the package.json to set "directories" to an empty set
7. Install default dev dependencies from the template package.json:
   ```bash
   npm install
   ```
8. Save your work! The first push command has a `-u` flag to set up tracking
   of the remote branch
   ```bash
   git add *
   git add .gitignore
   git commit -a
   git push -u origin master
   ```

## Maintenance
Make sure to commit your work regularly! The recommended command is
```bash
git commit -a
```
This will initiate a dialog where you can enter the commit message. The
message should always begin with a one-line short message (<80 characters), 
starting with an imperative verb. Any further details should be separated from
the short message by a blank line.

When you have something working, you can make it a *version* so users can
make it a fixed dependency for their projects. That way, any new changes you
make to the module will never break their code, unless they specifically ask
for your new version.

To create/update a version, use the [npm version] command. The package.json
includes a `postversion` script which will automatically take care of the
relevant Git push commands.

All version numbers should follow the [Semantic Versioning] standard.

[npm version]: https://docs.npmjs.com/cli/version
[Semantic Versioning]: https://semver.org/

## TODO
- Automate the correction of the "directories" property in the package.json
- Figure out peer dependencies
- Update ~/.npm-init.js to get a better npm init process. See
  https://devdocs.io/npm/getting-started/using-a-package.json
  Maybe see https://docs.npmjs.com/cli/init
- Test git pull? or fork? to start a new module from this template
