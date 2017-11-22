---
---

# Prerequisites
You will need to install a number of programs and create several accounts before you can start building apps with Orizuru.

### Node.js
Check if you already have it by running the following command on the command line.
This command should return a valid version number, e.g. `v8.9.1`.
```shell
node -v
```

If you don't have it, get it [here](https://nodejs.org/en/).

### NPM
Check if you already have it by running the following command on the command line.
This command should return a valid version number, e.g. `v5.5.1`.
```shell
npm -v
```

NPM is bundled with Node.js.
If you don't have it, install a more recent version of Node.js.

### Heroku CLI
Check if you already have it by running the following command on the command line.
This command should return a valid version number, e.g. `heroku-cli/6.14.38-9bfc11a (darwin-x64) node-v9.2.0`.
```shell
heroku -v
```

If you don't have it, get it [here](https://devcenter.heroku.com/articles/heroku-cli).

### SFDX CLI
Check if you already have it by running the following command on the command line.
This command should return a valid version number, e.g. `sfdx-cli/6.0.16-3780698 (darwin-x64) node-v8.6.0`.
```shell
sfdx -v
```

If you don't have it, get it [here](https://developer.salesforce.com/tools/sfdxcli).

### Heroku Account
If you don't have one, sign up for one [here](https://signup.heroku.com/).

Check if you are logged into your account in the Heroku CLI by running the following command on the command line.
This command should list your Heroku applications.
If you are not logged in, the Heroku CLI will prompt you to enter your username and password. Do so.
```shell
heroku apps
```

### SFDX Environment Hub
Sign up for a trial [here](https://developer.salesforce.com/promotions/orgs/dx-signup).

### Orizuru Tools
Check if you already have it by running the following command on the command line.
This command should return a valid version number, e.g. `FinancialForceDev Orizuru Version: 1.1.0 Copyright (c) 2017 FinancialForce.com, inc.  All rights reserved.`.
```shell
orizuru -v
```

If you don't have it, run the following on the command line:
```shell
npm install @financialforcedev/orizuru-tools --global
```
