# Lab 4: Consuming Graph

## Exercise 1: Authorize the web part

1. If you're still running your web part, hit <kbd>CTRL</kbd>+<kbd>C</kbd> until prompted to stop.
1. In your `MyEventsWebPart.ts`, add the following line to pass the web part's context to the component:

    ```typescript
      MyEvents,
          {
            description: this.properties.description,
            // BEGIN: Add this line
            context: this.context
            // END
          }
    ```

2. Yes, you'll get some errors. That's fine.
1. Just above where you entered new code, look for `IMyEventsProps.ts` and <kbd>CTRL</kbd>-Click on it to open the definition
1. Just above the `export interface IMyEventsProps`, paste:

```typescript
import { WebPartContext } from '@microsoft/sp-webpart-base';
```

1. Below the `description: string;` add `context: WebPartContext`.

## Exercise 2: SPFx Fast Serve

1. From the terminal or your command prompt type `npm i -g spfx-fast-serve`
1. Once completed, type `spfx-fast-serve`
1. When prompted to do so, type `npm install`
1. Once completed, run `npm run serve`

## WRITE EVENTS IN CALENDAR

> You thought you were finished, didn't you?

## Exercise 3: Get Graph Permissions

1. From your **dev tenant browser** profile, go to https://developer.microsoft.com/en-us/graph/graph-explorer
1. Select **Sign-in to Graph Explorer**
1. Search for **All events in my calendar**
1. Click on **Run query**
1. You should receive events (you did create events, right?). You may also get permission denied.
1. Select **Modify permissions**
1. Select the **Calendars.Read** and grant permissions

## Exercise 4: Add Calendar.Read permissions to the manifest

1. From Visual Studio Code, go to `config\package-solution.json`
1. Under `"isDomainIsolated": false`, add the following code (don't forget to add a `,` at the end of the line above (e.g: `false,`))

    ```json
    "webApiPermissionRequests": [
      {
        "resource": "Microsoft Graph",
        "scope": "Calendars.Read"
      }
    ],
    ```

1. Build your web part using `gulp build`
1. Bundle your web part using `gulp bundle --ship`
1. Package your web part using `gulp package-solution --ship`
1. Upload the `spfx-next-level.sppkg` file, found in `sharepoint\solution` to your app catalog (most likely located at `https://yourtenant.sharepoint.com/sites/appcatalog/AppCatalog`)
1. Go to your tenant's SharePoint Admin Portal (e.g.: `yourtenant-admin.sharepoint.com`)
1. Under **Advanced** > **API Access** look for a request to approve `Calendars.Read`. Select it and select **Approve**.