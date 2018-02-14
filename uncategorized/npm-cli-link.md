# npm link

## [doc page](https://docs.npmjs.com/cli/link)

`npm link` is useful when you are developing packages and want to test your
package without publishing it to the npm repository.

Assuming you have a directory `packages` with repos of packages you are developing
and a `projects` directory with projects that need to consume your package:
```bash
cd ~/workspace/packages/my-package #git repo of package
npm link
cd ~/workspace/projects/my-project #git repo of project
npm link package-name
```
This creates a symbolic link in `node_modules` to your package repo.

In the poject code you can now
```javascript
require('my-package');
```
