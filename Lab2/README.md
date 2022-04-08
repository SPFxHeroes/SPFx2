# Lab 2: Working with multiple versions of Node

## Exercise 1: Find a sample

1. Using your browser, go to http://aka.ms/spfx-webparts
1. In the **Samples by Framework**, search for **Upgrade me** and select it to open the `README.md` file associated to that sample
1. Find the link titled **Download this as a Zip file** and download the Zip file.
1. Extract the Zip file to your working folder.
1. Open a command prompt in that folder, and type `npm install`
1. If you don't run into any errors, run `gulp build`.
1. Scream in horror because of all the error messages you'll get. That's expected!

## Exercise 2: Finding what's going on

1. Go back to https://github.com/pnp/sp-dev-fx-webparts/tree/main/samples/react-upgrade-me and take a look at the compatibility section.
1. You'll need a version of Node that is compatible with SPFx 1.4.1.
1. Using the [SPFx compatibility matrix](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/compatibility), find which version of Node.js is compatible with SPFx 1.4.1. If there are multiple versions of Node.js compatible, we recommend always using the latest version compatible.
1. Go to <https://nodejs.org/en/download/releases/> and look for the last version of Node.js with a major version number matching the version you identified in the previous step. For example, if you found that SPFx 1.4.1 is compatible with Node 6 and 8, look for the latest version of Node starting with `Node.js 8.` (because 8 is the latest compatible version). For the rest of this lab, we'll assume that the version you will use is `8.17.0`

## Exercise 3: Install Node.js v8.x.x

1. Using an *administrator command prompt*, type `nvm install 8.17.0`.
1. Once install type `nvm use 8.17.0`.

## Exercise 4: Build the web part

1. Type `npm install`
1. Type `gulp build` 
1. If you didn't get an error, you successfully were able to build an older version of SPFx!

## Exercise 4: Go back to your previous version of Node

1. From the command prompt, type `nvm list`
1. Find the latest version of Node installed (14.x.x)
1. Type `nvm use 14.x.x` where `14.x.x` is the version of Node you found in the previous step.

> Note: You may want to make note of the version of Node.js used in this lab because we'll use it later.
