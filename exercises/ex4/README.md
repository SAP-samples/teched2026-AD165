# Exercise 4 - Add UI Integration Cards

In this exercise, you will enrich your workpage with UI integration cards. UI integration cards are compact, data-rich components that display live information from business systems directly on a Work Zone page — without the user needing to open a full application. You will upload a card package, add a card to your page, and preview the result in the site.

> [!NOTE]
> UI integration cards are based on the open SAP UI5 card standard. They can show lists, tables, objects, and analytical data from any OData or REST service. Cards can be developed and packaged using the SAP UI5 Tooling and then imported into Work Zone via the Content Manager. For users, they eliminate the round-trip of opening a full application just to check a single piece of status information.

---

## <a id="exercise-41-card-explorer"></a> Exercise 4.1 (Optional) - Explore the UI Cards in Card Explorer

### What you'll achieve
After completing this optional exercise you will be familiar with the Card Explorer and understand the basic anatomy of a UI integration card.

---

The Card Explorer is an interactive playground for UI integration cards. It lets you preview different card types, inspect and edit the card's `manifest.json` side-by-side, and see how data, actions, configuration, and filters change a card.

![UI Cards Explorer website](./images/02_01_0010.png)

---

### Steps

1. **Open the Card Explorer** — right-click the link and select **Open in New Tab**: [Card Explorer](https://sapui5.hana.ondemand.com/test-resources/sap/ui/integration/demokit/cardExplorer/webapp/index.html#/explore/list). The page has three main areas: left navigation (Card Types and Card Features), a live preview in the center, and the `manifest.json` editor on the right.

2. **Skim the card types** — in the left navigation, browse the available types: **List**, **Object**, **Table**, **Analytical**, **Calendar**, **Timeline**, **WebPage**, **Component**, and **Adaptive**. These map to the `sap.card/type` field in the manifest.

3. **Inspect a List card** — open **Card Types > List**, review how the card renders in the preview, then inspect the manifest on the right.

4. **Understand the manifest anatomy** — note the key sections:
   - **`sap.app`** — card identity: `id`, `type`, `title`, and `applicationVersion`
   - **`sap.card/type`** — the card type (e.g. `List`)
   - **`sap.card/header`** — title, subtitle, icon
   - **`sap.card/data`** — where the card fetches data (REST request URL, method, headers, path binding)
   - **`sap.card/content`** — how to render the data (item template for List cards)
   - **`sap.card/configuration`** — host-configurable parameters, destinations, and filters

5. **Explore card features** — browse **Card Features** in the left navigation (Data, Actions, Configuration, Filters) to see how each is expressed in the manifest.

<details>
<summary>Minimal List card manifest (reference)</summary>

```json
{
  "sap.app": {
    "id": "com.example.cards.samplelist",
    "type": "card",
    "title": "Sample List Card",
    "applicationVersion": { "version": "1.0.0" }
  },
  "sap.card": {
    "type": "List",
    "header": {
      "title": "Orders",
      "subtitle": "Recent",
      "icon": { "src": "sap-icon://product" }
    },
    "data": {
      "request": {
        "url": "https://example.com/api/orders",
        "method": "GET",
        "headers": { "Accept": "application/json" }
      },
      "path": "/items"
    },
    "content": {
      "item": {
        "title": "{OrderName}",
        "description": "{Customer}",
        "info": "{Status}",
        "actions": [
          { "type": "Navigation", "parameters": { "url": "{Link}" } }
        ]
      },
      "maxItems": 5
    },
    "footer": {
      "paginator": { "pageSize": 5 }
    },
    "configuration": {
      "parameters": { "region": { "value": "EMEA" } }
    }
  }
}
```
</details>

---

## <a id="exercise-42-upload-a-card-package"></a> Exercise 4.2 - Upload a Card Package

### What you'll achieve
After completing these steps a card package will be available in the Content Manager and ready to be added to pages.

---

Before a UI Integration Card can be uploaded to Work Zone standard edition, it must be part of a **Content Package** — a ZIP file that bundles content artifacts such as cards together with the role assignments that control who can see them. Creating one requires SAP Business Application Studio, which is outside the scope of this session, so we have pre-configured the package for you.

### Steps

1. Open the card packages folder in a new browser tab (`Right Click` + `Open link in new tab`) 👉 [CardPackages](https://github.com/SAP-samples/teched2026-AD165/blob/main/exercises/ex4/samples).

2. Download the "ContentPackage###.zip" file where ### is your participant ID using the github "Download Raw file" icon.

3. **Open the Channel Manager** — in the left-hand navigation, click **Channel Manager**.

4. **Add a new Content Package** — click **Add** and select **Content Package**.

5. **Select the ZIP file** — in the upload dialog, click **Browse** and select the `.zip` card package you downloaded.

6. **Select the Runtime destination** — select S4HANA_RT as runtime destination.

7. **Save** — click **Save**. The card package is validated and imported. You should see the new package appear in the Content Channels list.

> [!IMPORTANT]
> If the upload fails with a validation error, check that you are uploading the correct `.zip` file as provided by your instructor.

---

## <a id="exercise-43-use-a-card-on-your-page"></a> Exercise 4.3 - Use a Card on Your Page

### What you'll achieve
After completing these steps the imported card will appear on the page you created in Exercise 3.

---

### Steps

1. **Open your page** — Navigate to the Content Manager, find and open the page you created in Exercise 3.1.

2. **Enter edit mode** — click the **Edit** button to enter edit mode.

3. **Add the card** — in the **Purchasing Insights** section, click the **+** sign at the right of the section. Then click **Add Content**. 

4. **Pick the card** — in the App Finder, select **Cards**, search for the card you uploaded in Exercise 4.2 and select it.

Notice that it automatically resizes to give an aligned view. If you want you can resize the columns by dragging the line separating them or reposition your card by dragging it to another cell within the section.

6. **Save your changes.**

---

## <a id="exercise-44-preview-the-site"></a> Exercise 4.4 - Preview the Site

### What you'll achieve
After completing these steps you will have seen your card rendering live data on your page.

---

### Steps

1. **Open the site** — navigate to **Site Directory** and click the **Go to Site** icon on your site.

2. **Navigate to your page** — go to the space and page you created in Exercise 3.

3. **Verify the card** — the card you added should be visible and displaying data from the backend service it is connected to.

4. **Interact with the card** — click on the card header to navigate into the connected app.

---

## Summary

You uploaded a UI integration card package, placed a card on your custom page, and confirmed that it displays live data in the site.

Continue to - [Exercise 5 - Enable My Space](../ex5/README.md)
