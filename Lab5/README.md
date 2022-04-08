# Lab 5: Using PnP Reusable Controls

The PnP Reusable Controls provide you with a set of reusable React controls that can be used in SPFx solutions. These controls were written by super-smart and really good looking members in the community.

## Exercise 1: Scaffold your web part and make it faster

1. From your command prompt, go to your working folder.
1. Create a new folder called `using-pnp-controls`. You can use the File Explorer or type `md using-pnp-controls`
1. Change your current folder by using `cd using-pnp-controls`
1. Once in your new fancy folder, launch the yeoman generator by typing `yo @microsoft/sharepoint`
1. When prompted for a solution name, leave the default (**using-pnp-controls**), followed by <kbd>Enter</kbd>
1. When prompted what type of client you'd like to build, select **WebPart**
1. When prompted for a Web Part name, enter **PnP Controls**.
1. When prompted for a framework, select **React**
1. Wait for the solution to be scaffolded.

## Exercise 2: Detecting known vulnerabilities

1. Once your solution is scaffolded, note the number of vulnerabilities listed (e.g.: **found 112 vulnerabilities (16 low, 53 moderate, 40 high, 3 critical**)
1. Test that your web part works by running `gulp serve --nobrowser` and visiting your workbench.
1. Stop `gulp serve`
1. Type `npm audit fix`
1. If you are lucky, the system may automatically fix known exploits, but most likely it will not (especially if you are using the latest version of SPFx). It will, however, report all known vulnerabilities and and show you how to fix them -- if applicable.
1. If `npm audit fix` fixed vulnerabilities, test that the solution still works by using `gulp serve --nobrowser` again

## Exercise 3: Brute Force removing known vulnerabilities

When you ran `npm audit`, you may have noticed that it recommends running `npm audit fix --force`.

It may be tempting to always run `npm audit fix --force` to force updates, but doing so will often completely break your solution or -- as is the case with the current version of your solution -- it may fix only one or two vulnerabilities and may not be worth your time.

If you choose to do so, please make sure to backup your code before you do.

1. Stop `gulp serve`
1. Type `npm audit fix --force`
1. Once completed, run `gulp serve --nobrowser` again to verify that your updated dependencies don't break your solution.

You'll notice that it does not fix much... the proper process to fix dependencies is to patch every vulnerability manually by following the steps listed at https://go.npm.me/audit-guide

Please note that when you build and package your solution for production, the system will remove all unused dependencies (something that is called tree shaking), along with the associated vulnerabilities.

It may be wiser to use code scanning features provided by GitHub or  Azure DevOps.

## Exercise 3: Add the PnP Reusable Controls library

To get started you have to install the following dependency to your project: `@pnp/spfx-controls-react`.

1. Enter the following command to install the dependency to your project:

```bash
npm install @pnp/spfx-controls-react
```

## Exercise 4: Add the WebPartTitle component

1. In the `PnPControls.tsx` file, located under `src/webparts/pnPControls/components/PnPControls.tsx`, find the space after the last `import` and before the class (line 5, most likely)
1. Import the `WebPartTitle` by adding the following line of code:

   ```typescript
   import { WebPartTitle } from "@pnp/spfx-controls-react/lib/WebPartTitle";
   ```

1. In the `render()` method, below the `<section>` element, and before the `welcome` `<div>` (around line 19), insert the following code:

   ```typescript
   <WebPartTitle displayMode={this.props.displayMode}
              title={this.props.title}
              updateProperty={this.props.updateProperty} />
   ```

1. In the same folder, open the `IPnPControlsProps` and add the following import statement on line 1:

   ```typescript
   import { DisplayMode } from '@microsoft/sp-core-library';
   ```

1. In the `IPnPControlsProps` class, add the following code below `userDisplayName`. but before the class close (`}`)

   ```typescript
   title: string;
   displayMode: DisplayMode;
   updateProperty: (value: string) => void;
   ```

1. Open the `PnPControlsWebPart.ts` and find the `IPnPControlsWebPartProps` interface (around line 15) and add the following code below the `description: string;` line:

   ```typescript
   title: string;
   ```

1. Find the `render()` method. Just below `PnPControls, {` and before `description`, paste the following code:

   ```typescript
   title: this.properties.title,
    displayMode: this.displayMode,
    updateProperty: (value: string) => {
      this.properties.title = value;
    },
   ```

1. From the command prompt, run `gulp serve --nobrowser`
1. 1. When the web part is ready, refresh the page. You should see a new editable web part title. 
1. Try leaving the title as is (empty) and switch the page to **Preview** mode; the title component should be invisible.
1. Switch the page back to **Edit** mode, edit the title to anything you want, and switch again to **Preview** mode to see the title in action.

## Exercise 5: Fast serve and test

1. Stop `gulp serve`
1. From the terminal or your command prompt type `npm i -g spfx-fast-serve`
1. Once completed, type `spfx-fast-serve`
1. When prompted to do so, type `npm install`
1. Once completed, run `npm run serve`



## Exercise 6: Adding a Placeholder