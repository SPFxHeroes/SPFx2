# Lab 1: Getting Your Environment Ready

## Exercise 1: Configure Windows workstation for development purpose

This step will configure your workstation as a development workstation by configuring the least privileges required to be able to work well with SPFx development.

1. From your Windows desktop, use the **Start menu** and search for `Use developer features`
1. On the **Privacy & Security > For developers** page, under **Developer Mode**, look for **Install apps from any source, including loose files**
1. If the setting is not already **on**, toggle the setting to **on**
1. Scroll to the **PowerShell** section
1. Under **Change execution policy to allow local PowerShell scripts to run without signing...**, select **Apply**.


## Exercise 2: Install Node Version Manager

Node Version Manager will allow you to install multiple versions of Node.js on your workstation. 

1. If you already have **Node.js** installed, uninstall it from **Add/remove programs**
1. Verify that you do not have a folder called `Nodejs` under `c:\program files`. If you find such a folder, please uninstall it.
1. Using your browser, navigate to https://github.com/coreybutler/nvm-windows/releases and look for `nvm-setup.zip` and download it.
1. Once downloaded, unzip the file
1. From the unzipped folder, launch `nvm-setup.exe` and follow the instructions to install NVM. Use all the default options.
    > NOTE: If you do not have administrative access to your workstation, try using `nvm-noinstall.zip` instead and follow the instructions within the `.zip` file.
1. Confirm that NVM is installed by launching **Command Prompt** and change your current directory to a temporary location (e.g.: `c:\temp`) by entering `cd c:\temp`, followed by <kbd>Enter</kbd>.
1. Type `nvm`, followed by <kbd>Enter</kbd>
1. If get an error message, try restarting your computer; otherwise, you should see help for NVM.

## Exercise 3: Install Node.js 

1. Using the same command prompt window, type: `nvm install 14.18.2`, followed by <kbd>Enter</kbd>
1. You may get prompted to accept changes. This is expected.
1. Once installation is complete, type `nvm use 14.18.2`, followed by <kbd>Enter</kbd>. If you get prompted to accept the changes, please do so.
    > NOTE: If you get an error, try launching an administrative command prompt and repeat the steps above.
1. When the operation is complete, verify your current version of Node.js by entering `node -v`, followed by <kbd>Enter</kbd>. It should display `v14.18.2`.

## Exercise 4:  Install Gulp

[Gulp](https://gulpjs.com) is a JavaScript-based task runner used to automate repetitive tasks. The SharePoint Framework build toolchain uses Gulp tasks to build projects, create JavaScript bundles, and the resulting packages used to deploy solutions.

1. Enter the following command to install the Gulp CLI: `npm install gulp-cli -g`, followed by <kbd>Enter</kbd>.
1. This will take a little bit of time. Now is a good time to stretch your legs.
1. Once completed, you can verify that Gulp is installed by entering `gulp -v`, followed by <kbd>Enter</kbd>. It should display:

   ```console
    CLI version: 2.3.0
    Local version: 4.0.2
    ```z

> Note: You may not see a `Local version` if you're not currently in a project folder. That's ok!

## Exercise 5: Install Yeoman

[Yeoman](https://yeoman.io/) helps you kick-start new projects, and prescribes best practices and tools to help you stay productive. SharePoint client-side development tools include a Yeoman generator for creating new web parts. The generator provides common build tools, common boilerplate code, and a common playground website to host web parts for testing.

1. From the command prompt, enter the following command to install Yeoman: `npm install yo -g`, followed by <kbd>Enter</kbd>.
1. To verify your installation, type `yo`, followed by <kbd>Enter</kbd>.
1. If you see **Allo! What would you like to do?**, use your arrow keys to select **Get me out of here!** and hit <kbd>Enter</kbd>.

## Exercise 6: Install Yeoman SharePoint generator

The Yeoman SharePoint web part generator helps you quickly create a SharePoint client-side solution project with the right toolchain and project structure.

To install the SharePoint Framework Yeoman generator globally:
1. From the command prompt, enter the following command: `npm install @microsoft/generator-sharepoint -g`, followed by <kbd>Enter</kbd>.
1. A bazillion years later, when the installation is complete, enter `yo`, followed by <kbd>Enter</kbd>.
1. When prompted **Allo! What would you like to do?**, verify that **@microsoft/sharepoint** is listed under **Run a generator**. 
1. Using your arrow keys, select **Get me out of here!**. We still have a few things to install to make sure you have all the best SPFx development tools at your disposal.

## Exercise 7: Install TypeScript

> Not needed for SPFx development, but used for this lab.

1. From the command prompt, enter the following command: `npm install -g typescript`, followed by <kbd>Enter</kbd>.
1. Don't panic, the installation is very quick. You might even believe that there was an error, but if you see **Updated 1 package in x.xxxs**, you were successful.
1. When the installation is complete, enter `tsc --version`, followed by <kbd>Enter</kbd>. You should see **Version 4.5.2**.

## Exercise 8: Install CLI for Microsoft 365

1. From the command prompt, enter the following command: `npm i -g @pnp/cli-microsoft365`, followed by <kbd>Enter</kbd>.
1. When the installation is complete, enter `m365`, followed by <kbd>Enter</kbd>.
1. If it doesn't scream at you, you are good!

## Exercise 9: Install essential Visual Studio Code extensions

1. Launch **Visual Studio Code**.
1. Open the **Extensions** activity bar (or by enterping <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>X</kbd>)
1. From the search box, type `SPFx Essentials` and wait for search results to appear.
1. From the list of search results, select **SPFx Essentials** by **Elio Struyf**.
1. From the **SPFx Essentials** page, select **Install**.
1. Repeat the steps 3-5 with the following extensions:
    1. **GitHub Repositories**
    1. **Live Server**
    1. **Live Share**
    1. **GitHub Copilot**

## Exercise 10: Create your own Dev Tenant

Go to http://aka.ms/o365devprogram and follow the steps to create your own tenant. Use a name for yourself -- not your company name. For example, I used **Tahoe Ninjas**, not **Microsoft**.

Follow the steps to create your tenant. We'll use the tenant in later labs.

In our next lab, we'll apply everything we've done so far to create a web part.
