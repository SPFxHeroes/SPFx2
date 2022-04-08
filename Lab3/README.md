# Lab 3: Building a web part

Let's build a web part!!!!!

## Exercise 1: Scaffold your web part

1. From your command prompt, go to your working folder.
1. Create a new folder called `spfx-next-level`. You can use the File Explorer or type `md spfx-next-level`
1. Change your current folder by using `cd spfx-next-level`
1. Once in your new fancy folder, launch the yeoman generator by typing `yo @microsoft/sharepoint`
1. When prompted for a solution name, leave the default (**spfx-next-level**), followed by <kbd>Enter</kbd>
1. When prompted what type of client you'd like to build, select **WebPart**
1. When prompted for a Web Part name, enter **My Events**.
1. When prompted for a framework, select **React**
1. Wait for the solution to be scaffolded.
1. Go to your web browser, and navigate to your Microsoft 365 Dev Tenant (e.g.: `https://yourdevtenant.sharepoint.com`).
1. To view the workbench, navigate to `/_layouts/15/workbench.aspx`
1. You should get an error saying that your web part isn't running... let's fix that!
1. Type `gulp serve`.
1. You should get a warning saying:

    ```console
    Warning - [spfx-serve] When serving in HTTPS mode, a PFX cert path or a cert path and a key path must be provided, or a dev certificate must be generated and trusted. If a SSL certificate isn't provided, a default, self-signed certificate will be used. Expect browser security warnings.
    ```

## Exercise 2: Install the self-signed certificate

1. Run `gulp trust-dev-cert`
1. When prompted, accept the certificate by selecting **Yes**
1. Launch your web part by typing `gulp serve --nobrowser`
1. Wait for a message saying `Finished subtask 'reload'`
1. Go back to your workbench and refresh the page. Your web part should be available to add to your browser.
1. Test the web part. When you're done, go back to your command prompt and hit <kbd>CTRL</kbd>+<kbd>C</kbd> until it asks you if you want to **Terminate batch job (Y/N)?**. Select **y**

## Exercise 3: Customize the web part

1. From the command prompt, type `code .` to open Visual Studio Code (code) in the current folder (.)
1. Launch the terminal window by hitting <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>`</kbd>.
1. From the terminal, type `gulp serve --nobrowser`
1. Try to find in the code where it says "Welcome to SharePoint" and replace it for "My Events".
1. Refresh the browser to see if your results are correct.

## Exercise 4: Use SPFx Fast Serve

SPFx Fast Serve changes how you serve your web part while developing it so that you don't have to wait as long for the web part to rebuild every time you change it.

1. From the terminal or your command prompt type `npm i -g spfx-fast-serve`
1. Once completed, type `spfx-fast-serve`
1. When prompted to do so, type `npm install`
1. Once completed, run `npm run serve`
1. Try to find in the code that you changed earlier (where it says **My Events** and replace it for **My Events -- Faster**.
1. Refresh the browser if necessary to see if your results are correct.

## Exercise 5: Build a web part using SPFx 1.4.1

SPFx 1.4.1 is compatible with SharePoint 2019. Let's show you how to configure your workstation to generate SPFx 1.4.1 solutions without affecting your SPFx 1.14.1 environment.

1. From your command prompt, go to the root of your working folder.
1. Create a new folder called `spfx-next-level141`. You can use the File Explorer or type `md spfx-next-level141`
1. Change your current folder by using `cd spfx-next-level141`
1. Using an administrator command prompt, type `nvm use 8.17.0`
1. Because you installed a new version of Node, you'll need to re-install the SPFx dependencies. To do so, type: `npm install gulp-cli yo --global`
1. To install the SPFx 1.4.1 generator, type `npm i @microsoft/generator-sharepoint@1.4.1 --global`
1. Once in your new version (by which I mean *older*) of the Yeoman generator in installed, launch the yeoman generator by typing `yo @microsoft/sharepoint`
1. When prompted for a solution name, leave the default (**spfx-next-level141**), followed by <kbd>Enter</kbd>
1. When prompted to choose a SharePoint version, pick the only choice that's available (and ask yourself why you're even prompted to do so?)
1. When prompted about adding the solution to all sites, select **N** followed by <kbd>Enter</kbd>
1. When prompted about requiring special permissions, select **N** followed by <kbd>Enter</kbd>
1. When prompted what type of client you'd like to build, select **WebPart**
1. When prompted for a Web Part name, enter **My Events 1.4.1**.
1. Provide a description, if you wish. For example **Hugo made me this**
1. When prompted for a framework, select **React**
1. Wait for the solution to be scaffolded.
1. Go to your web browser, and navigate to your Microsoft 365 Dev Tenant (e.g.: `https://yourdevtenant.sharepoint.com`).
1. To view the workbench, navigate to `/_layouts/15/workbench.aspx`
1. You should get an error saying that your web part isn't running... let's fix that!
1. Type `gulp serve`.
1. Once you are bored with playing with the web part, you may stop the `gulp serve` and type `nvm use 14.x.x` (where `14.x.x` is the previous version of Node.js you were using -- you *did* make note of the version number before, didn't you?)
