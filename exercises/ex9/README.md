# Exercise 9 - Create, Package, and Deploy Your Own UI Integration Card

In this exercise, you will enrich your workpage with a UI integration card that you configure yourself. UI integration cards are compact, data-rich components that display live information from business systems directly on a Work Zone page — without the user needing to open a full application. You will get a card from the Card Explorer, give it a unique ID, then use SAP Business Application Studio to wrap it in a content package, upload it to Work Zone, and add it to your page.

> [!NOTE]
> UI integration cards are based on the open SAP UI5 card standard. They can show lists, tables, objects, and analytical data from any OData or REST service. Cards are defined entirely by a `manifest.json`. A **content package** is a ZIP file that bundles one or more cards together with the access roles that control who can see them — it is the deployment unit for Work Zone. SAP Business Application Studio (BAS) provides tooling to validate and build content packages.

---

## Before You Start — Create Your Dev Space in Business Application Studio

Starting a dev space takes a few minutes. Kick it off now so it is ready when you reach Exercise 9.3.

1. Open **SAP Business Application Studio** - open (in a new window shift + left click) 👉  <a href="https://an4-a8rlu183.eu10cf.applicationstudio.cloud.sap/index.html" target="_blank">SAP Business Application Studio</a>.

2. Click **Create Dev Space**. 

3. **Select Dev Space type** - Enter a name, e.g. **MyCard_xxx** with xxx being your participant ID. Keep the **SAP Fiori** selection, because this type of dev space already contains the Developer Tools for SAP Build Work Zone out of the box which will allow you to package your Content Package in Exercise 9.3. Then click **Create Dev Space**.

Your dev space is created and now starting.

---

## <a id="exercise-91-card-explorer"></a> Exercise 9.1 (Optional) - Explore the Card Explorer

### What you'll achieve
After completing this optional exercise you will be familiar with the Card Explorer and understand the basic structure of a UI integration card manifest.

---

The Card Explorer is an interactive playground for UI integration cards. It lets you preview different card types and inspect and edit a card's `manifest.json` side-by-side.

### Steps

1. **Open the Card Explorer** — right-click and select **Open in New Tab**: [Card Explorer](https://sapui5.hana.ondemand.com/test-resources/sap/ui/integration/demokit/cardExplorer/webapp/index.html#/explore/list). The page has three areas: left navigation (card types), a live preview in the center, and the `manifest.json` editor on the right.

2. **Skim the card types** — in the left navigation, browse: **List**, **Object**, **Table**, **Analytical**, **Calendar**, and others. These map to the `sap.card/type` field in the manifest.

3. **Understand the manifest anatomy** — in any List card example, note the key sections:
   - **`sap.app`** — card identity: `id`, `type`, `title`, `applicationVersion`
   - **`sap.card/type`** — the card type (e.g. `List`)
   - **`sap.card/header`** — title, subtitle, icon
   - **`sap.card/data`** — where the card fetches its data
   - **`sap.card/content`** — how to render the data. Most card types in the Card Explorer use static mock data, but in *Card Features > Data*, you can learn how to consume data from a real system via a BTP destination.  

---

## <a id="exercise-92-get-card"></a> Exercise 9.2 - Edit and Download Your Card from the Card Explorer

### What you'll achieve
After completing these steps you will have a card manifest with a unique ID ready to be added to a content package.

---

### Steps

1. **Check the List card in the Card Explorer** — make sure you selected the list card in the menu on the left and that you can see the manifest JSON code on the right side.

2. **Edit the card ID** — in the editor panel on the right, find the `"id"` field inside `"sap.app"` and change its value to `"teched.ad165.card###"` (replace `###` with your participant number). This is the **only required change** and makes sure your card ID does not conflict with other participants.

   Before:
   ```json
   "sap.app": {
		"id": "card.explorer.highlight.list.card",
    ...
   ```
   After:
   ```json
   "sap.app": {
		"id": "teched.ad165.card000",
    ...
   ```


3. (Optional) **Edit the card title and subtitle** — find the `"configuration"` section inside `"sap.card"` and change the `"title"` value under parameters to a new title including your participant number. If you want, change the subtitle as well. 


   Before:
   ```json
   "configuration": {
			"editor": "dt/Configuration",
			"parameters": {
				"title": {
					"value": "List Card with Top 4 Products"
				},
				"subtitle": {
					"value": "These are the top sellers this month"
				},
				"maxItems": {
					"value": 4
				}
			}
		},
   ```
   After:
   ```json
   		"configuration": {
			"editor": "dt/Configuration",
			"parameters": {
				"title": {
					"value": "Products Low in Stock xxx"
				},
				"subtitle": {
					"value": "Urgent reordering required"
				},
				"maxItems": {
					"value": 4
				}
			}
		},
   ```

> [!TIP]
The "configuration" section declares customizable parameters (like search filters or preset business values, e.g. a cost center) exposed to administrators during page creation.

4. **Download the card** — click the **download link** (↓) above the manifest editor to download the card sample. Select **Bundle as card.zip** from the dropdow and save it somewhere you can find it (e.g. your Desktop). The ZIP contains the `manifest.json` and supporting files for the card. 

5. **Extract the zip** to a folder of your choice.


---

## <a id="exercise-93-bas-package"></a> Exercise 9.3 - Create a Content Package in SAP Business Application Studio

### What you'll achieve
After completing these steps you will have a `package.zip` content package ready to upload to Work Zone.

---

By now your BAS dev space should be running. Click its name to open it.

### Steps

#### Create the project

1. **Open the Get Started page** — your Dev Space should now be running. Click the name of your Dev Space to access it. In case, you receive a pop-up about Tracing, just confirm with **OK**. 

Business Application studio opens on the **Get Started** tab. If it is not visible, go to **Help** → **Get Started**.

2. **Create a new project from template** — click **New Project from Template**.

3. **Select the Content Package template** — Click the **Content Package** tile. You might need to scroll to see it. Then click **Start**.

4. **Fill in the project details** — enter the following values, then click **Finish**:

   | Field | Value |
   |---|---|
   | Project Name | `ContentPackage###` |
   | Namespace | `ns` |
   | Title | `TechEd AD165 Package ###` |
   | Subtitle | `AD165` |
   | Include Content Samples | `True` |

   Replace `###` with your participant number. BAS creates the project and opens it.

---

#### Edit the package manifest

8. **Replace the entire contents** of `content.json` with the following. Replace `###` with your participant number.

   `content.json` tells the content package builder what to include in the ZIP. Each entry declares one artifact: here a **role** (the access role that controls who sees the card) and a **card** (your UI integration card). The `src` block tells the builder where to find the source files — both point to the `demo/src` folder you will create in the next step.

   ```json
   {
     "role-###": {
       "type": "role",
       "src": { "from": "./demo/src", "content": "role.json" }
     },
     "card-###": {
       "type": "card",
       "src": {
         "from": "./demo/src",
         "path": "./",
         "build": "",
         "package": "",
         "manifest": "src/manifest.json"
       }
     }
   }
   ```

   Save the file (**Ctrl+S**).

---

#### Add the card files

In steps 9–11 you place the actual card and role source files into the project. The builder you run in step 12 will pick them up from here and pack them into the ZIP. You will create the `demo/src` folder structure, drop in the card manifest from Exercise 9.2, and add a role definition that links the role to your card.

9. **Create the folder structure** — in the Explorer panel on the left:
   - Right-click the project root → **New Folder** → name it `demo`
   - Right-click `demo` → **New Folder** → name it `src`

10. **Add the card manifest** — in the `demo/src` folder:
    - Right-click `src` → **New File** → name it `manifest.json`
    - Open the file and paste the card manifest JSON you edited in Exercise 9.2 (from your downloaded manifest.json or directly from the Card Explorer editor if it is still open).
    - Make sure the `"id"` in `"sap.app"` is still `"teched.ad165.card###"`.
    - Save the file (**Ctrl+S**).

11. **Add the role definition** — in the same `demo/src` folder:
    - Right-click `src` → **New File** → name it `role.json`
    - Paste the following content. Replace `###` with your participant number.

    ```json
    {
      "_version": "3.2.0",
      "identification": {
        "id": "ns.ContentPackage###.sm",
        "title": "TechEd AD165 Role ###",
        "entityType": "role"
      },
      "payload": {
        "cards": [
          { "id": "teched.ad165.card###" }
        ]
      }
    }
    ```

    Save the file (**Ctrl+S**).

---

#### Build the package

12. **Build the content package** — in the Explorer panel, right-click the **`manifest.json` in the project root** (the package manifest, not the one inside `demo/src`). Select **Content Package: Package**.

13. **Locate the ZIP file** — when the build completes, find `package.zip` in your browser's **Downloads** folder. Rename it to `ContentPackage###.zip`.

> [!IMPORTANT]
> If the **Content Package: Package** option does not appear in the right-click menu, the "Development Tools for SAP Build Work Zone" extension is not enabled in your dev space. Stop the dev space, enable the extension (click Edit on the dev space), restart it, and try again.

---

## <a id="exercise-94-upload"></a> Exercise 9.4 - Upload the Content Package

### What you'll achieve
After completing these steps your card package will be available in the Content Manager, ready to be placed on a page.

---

### Steps

1. **Open the Channel Manager** — in the Work Zone administration environment, click **Channel Manager** in the left-hand navigation.

2. **Add a new Content Package** — click **Add** and select **Content Package**.

3. **Select your ZIP** — in the upload dialog, click **Browse** and select `ContentPackage###.zip`.

4. **Select the Runtime destination** — select **S4HANA_RT** as the runtime destination.

5. **Save** — click **Save**. Work Zone validates and imports the package. You should see it appear in the Content Channels list with the name *TechEd AD165 Package ###*. Note that this can sometimes take some time. 

6. While you are waiting, please ask one of your instructors already now to assign **TechEd AD165 Role ###** to your user. This is required for the card to be visible later after adding it to your page.

> [!IMPORTANT]
> If the upload fails with a validation error, verify that: (1) you right-clicked the package root `manifest.json` (not the card manifest in `demo/src`) to build; (2) all `###` placeholders were replaced with your participant number; and (3) the card `id` `teched.ad165.card###` matches in the card manifest and the role.json.

---

## <a id="exercise-95-add-to-page"></a> Exercise 9.5 - Add the Card to Your Page

### What you'll achieve
After completing these steps your card will appear on the page you built in Exercise 3.

---

### Steps

1. **Open your page** — navigate to the **Content Manager**, find and open the page you created in Exercise 3.1.

2. **Enter edit mode** — click the **Edit** button.

3. **Add the card** — click the **+** sign in any section on your page, then click **Add Content**.

4. **Find your card** — in the App Finder, select **Cards** and search for your participant number **###**. Select **My Card ###** (or the title you set in Exercise 9.2).

5. **Save your changes.**

---

## <a id="exercise-96-assign-role"></a> Exercise 9.6 - Assign the Package Role to Your Site

### What you'll achieve
After completing these steps the role from your package will be assigned to your site, making the card visible to users who have that role.

---

### Steps

1. **Open your site settings** — navigate to **Site Directory** and open your site settings by clicking the cog icon.

2. **Open Role Assignments** — in the left-hand navigation, click **Role Assignments** and confirm you are on the **Roles** tab.

3. **Switch to Edit mode** — click the **Edit** button.

4. **Find your role** — search for your participant number `###`. You should see **TechEd AD165 Role ###**.

5. **Assign the role** — toggle its switch to **On** in the *Assignment Status* column.

6. **Save your changes.**


---

## <a id="exercise-97-preview"></a> Exercise 9.7 - Preview Your Site

### What you'll achieve
After completing these steps you will see your card live in the site.

---

### Steps

1. **Open the site** — navigate to **Site Directory** and click the **Go to Site** icon on your site.

2. **Navigate to your page** — go to the space and page from Exercise 3.

3. **Verify the card** — your card should be visible on the page.

4. **Interact with the card** — click on items or the card header to verify the navigation behaviour defined in the manifest.

---

## Summary

You edited a card in the Card Explorer, used SAP Business Application Studio to wrap it in a content package, uploaded the package via the Channel Manager, placed it on your page, and assigned the access role. You have now completed the full card development-to-deployment lifecycle.

Return to - [Main README](../../README.md)
