---
---

# Building Your First App

## Introduction
In under 5 minutes, you can build your own Node.js Heroku application connected to the Lightning Platform.
Make sure you have completed all of the [prerequisites](/docs/prerequisites/).

Don't worry if you're unfamiliar with Node.js, this tutorial will walk you through the important parts of the code!

## Create the Workspace
1. Create an empty directory - in this example we have created the directory `orizuru-tutorial`.
1. Open the command line and navigate to the new empty directory.<br>
    From here on out, whenever you're asked to run a command, ensure you run it from the command line in this directory.

## Use a Template
1. Run the command:
    ```shell
    orizuru setup init
    ```
1. You will be asked to choose a template. Choose the `web-worker-template`.
1. All Node.js apps need a [package.json](https://docs.npmjs.com/files/package.json), which describes the shape of the application.
    * The tools will create one for you, by asking you some details about your project.
    * It will guess appropriate answers for each question, so just press Enter on each question to accept the default suggestions.
        * The questions will look like this:
            > ? package name: *(orizuru-tutorial)* <br>
            > ? version: *(1.0.0)* <br>
            > ? description: <br>
            > ? git repository: <br>
            > ? keywords: <br>
            > ? author: <br>
            > ? license: *(ISC)*

Congratulations, you've built your Orizuru first app!

You'll notice that your empty directory isn't so empty now - let's take a closer look at the newly generated files and directories.

|Path|Description|
|----|-----------|
|.vscode/|Hidden directory containing configuration files for VisualStudio Code, the recommended IDE for working with Orizuru|
|src/apex/|Source code for the Lightning Platform component of your app|
|src/node/|Source code for the Heroku component of your app|
|.gitignore|Tells git to exclude certain files/directories from source control - see the [docs](https://git-scm.com/docs/gitignore) for more detail|
|.jsbeautifyrc|Tells [JS Beautify](https://www.npmjs.com/package/js-beautify) the conventions to follow when automatically formatting source code, such as javascript or json files|
|.salesforcedx.yaml|Tells the [SFDX one-click deploy button](https://deploy-to-sfdx.com/repo) how to deploy your app to a new scratch org|
|app.json|Tells Heroku about how to build your app, such as which add-ons to install and the number and type of each dyno|
|package.json|Describes the Node.js app|
|Procfile|Tells Heroku about the entry points into the Heroku component of your app|
|sfdx-project.json|Tells SFDX about how to build the Lightning Platform component of your app|

## Deploy Your App
1. You deploy apps to Heroku using git.
    So let's turn the current workspace into a git repository.
    * Run the following commands:
        ```shell
        git init
        git add .
        git commit -am "Initial commit"
        ```
    * This should log out something like the following
        > Initialized empty Git repository in /path/to/orizuru-tutorial/.git/ <br>
        > [master (root-commit) 4514a8d] Initial commit 41 files changed, 2036 insertions(+) <br>
        > create mode 100644 .gitignore <br>
        > create mode 100644 .jsbeautifyrc <br>
        > ...
1. Now let's deploy to Heroku and the Lightning Platform. Run the following command:
    ```shell
    orizuru deploy
    ```
1. You will be asked which Heroku app to deploy to. You can either create a new one, or choose an existing one.<br>
    If you are part of any Heroku enterprise teams, you can create an app in that team.<br>
    For this tutorial, choose `<<Create new Heroku App>>`.
1. Heroku will create a new app, with a random name, in this case `evening-badlands-29385`.<br>
    The tools will push the code up to Heroku. Heroku will detect that it's a Node.js project, install the packages it depends on and start running the app.
1. Great! You've got your Heroku app up, and running. If you want to, you can look at it in your [Heroku Dashboard](https://dashboard.heroku.com).
1. Next, you'll deploy to the Lightning Platform.<br>
    The tools will generate a public and private key pair, which will be used for OAuth authentication between the two components of your app.
    * Again, you'll be asked questions and you can just press Enter to accept the default suggestion.
        * The questions will look like this:
        > ? Country Name (2 letter code) *GB* <br>
        > ? State or Province Name (full name) *Some-State* <br>
        > ? Locality Name (eg, city) <br>
        > ? Organization Name (eg, company) *FinancialForce* <br>
        > ? Organizational Unit Name (eg, section) <br>
        > ? Common Name (e.g. server FQDN or YOUR name) *test@test.com*
1. The tools will open a web browser on the Salesforce login page. Login to your Environment Hub. Once you've successfully logged in, you can close the browser.
1. You will be asked which scratch org to deploy to. You can either create a new one, or choose an existing one.
    For this tutorial, choose `<<Create new SFDX scratch org>>`.
    This will deploy the source code, and assign permission sets to the current user.
1. Now you will be asked to create a [Connected App](https://developer.salesforce.com/page/Connected_Apps).
    * Again, you'll be asked questions and you can just press Enter to accept the default suggestion.
        * The questions will look like this:
        > Create Connected App<br>
        >  You are about to be asked to enter information that will be incorporated into your connected app. <br><br>
        > ? Connected App Name *Orizuru* <br>
        > ? Connected App Email *test@test.com* <br><br>
        > Update Heroku config variables
    * The new Connected App will be pushed to your scratch org.
    * The corresponding `JWT_SIGNING_KEY` will be pushed up to your Heroku app as a config variable.
1. The sample app uses a Named Credential to specify the URL of the Heroku app.
    * Again, you'll be asked questions and you can just press Enter to accept the default suggestion.
        * The questions will look like this:
        > Create Named Credential <br>
        > ? Named Credential Name *Orizuru*
1. Finally, the tools will open your scratch org in a web browser.

Congratulations, you've deployed your first Orizuru app!

But before you get too carried away, you need to some manual post-install steps.
Sorry, but Salesforce don't allow us to do this programmatically (at least, not yet)!

### Manual Post-install Steps
1. In the scratch org's Setup, type 'Manage Connected Apps' into the Quick Find search box.
1. Click on Manage Connected Apps in the sidebar. Here you'll see the connected app we prepared earlier.
1. Click on the Edit button next to the Orizuru connected app.
1. In the **OAuth policies** section, change **Permitted Users** from *All users may self-authorize* to *Admin approved users are pre-authorized*.
    * Ok the popup that warns you that currently logged in users will be denied access - there won't be any.
1. Press the Save button at the bottom of the Connected App page.
1. Back on the Manage Connected App page, click on the name of the Connected App.
1. In the **Permission Sets** section, press the **Manage Permission Sets** button.
1. Tick the checkbox next to the OrizuruAdmin permission set, which is already assigned to the current user, then press Save.

## Try it out
TODO

## Make it your own
TODO
