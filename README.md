# Steps to Reproduce

1. Install WSL 2: https://docs.microsoft.com/en-us/windows/wsl/install-win10
2. Install Webstorm on Windows, i.e. `choco install webstorm`
3. Install Node and Yarn on WSL, i.e. with NVM:
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
nvm install --lts
npm install -g yarn
```
4. Clone this repo: `git clone https://github.com/mr-perseus/yarn-berry-websotrm-issue-demo.git`
5. Install dependencies, check that lodash works:
```
cd yarn-berry-websotrm-issue-demo
yarn install
yarn start
# [ [ 1, 3 ], [ 2, 4 ] ]
```
6. Open project in WebStorm.
7. Languages & Frameworks -> Node.js and NPM: Set Node interpreter to the WSL one, manually set Yarn to \\wsl$\<LINUX_DISTRIBUTION>\home\<User>\.nvm\versions\node\<Version>\lib\node_modules\yarn (This is another issue: https://youtrack.jetbrains.com/issue/WEB-47164)

# Expected Result
- In `package.json`, the loadsh dependency should be seen as installed.
- In `index.js`, there should be intellisense on require('lodash')

# Actual Result
- In `package.json`, it says "The lodash package is not installed".
- In `index.js`, there is no intellisense on "lodash".
