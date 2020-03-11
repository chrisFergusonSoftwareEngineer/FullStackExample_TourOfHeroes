# Introduction
This is the mechanism for user interaction.

This is a modified copy of Angular's Tour of Heroes: Part 6 (https://angular.io/tutorial/toh-pt6).  With the main modification being the omission of the InMemoryDbService.  Instead, the Hero Service (and other DB API calls) are configured to point to the REST API.

# Developer Setup

## Prerequsites
1. Must have Node installed: https://nodejs.org/en/
  a. May want to install Node Version Manager instead of Node directly: https://github.com/nvm-sh/nvm
2. Must have Angular CLI installed: https://angular.io/guide/setup-local

## Setup
1. In terminal, navigate into the AngularTourOfHeroes directory.
2. Run the install command: `npm install`
3. Run the Angular Serve command: `ng serve`
4. Open a Google Chrome browser and navigate to `localhost:4200`

## Debugging
These steps may be useful if you would like to debug using Visual Studio Code.

Note, you need the Chrome Debugger extension in VS Code to use this: msjsdiag.debugger-for-chrome

Add the following configuation to your launch.json file:

```
        {
            "type": "chrome",
            "request": "launch",
            "name": "Angular Tour Of Heroes (localhost:4200)",
            "url": "http://localhost:4200",
            "webRoot": "${workspaceFolder}/FrontEndGui/AngularTourOfHeroes"
        }
```