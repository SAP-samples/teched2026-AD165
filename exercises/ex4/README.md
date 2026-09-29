# Exercise 4 - Add UI Integration Cards

In this exercise, you will enrich your workpage with UI integration cards. UI integration cards are compact, data-rich components that display live information from business systems directly on a Work Zone page — without the user needing to open a full application. You will upload a card package, add a card to your page, and preview the result in the site.

> [!NOTE]
> UI integration cards are based on the open SAP UI5 card standard. They can show lists, tables, objects, and analytical data from any OData or REST service. Cards can be developed and packaged using the SAP UI5 Tooling and then imported into Work Zone via the Content Manager.

## <a id="exercise-41-upload-a-card-package"></a> Exercise 4.1 - Upload a Card Package

After completing these steps, a card package will be available in the Work Zone Content Manager and ready to be added to pages.

1. Download the card package provided by your instructor (a `.zip` file containing the card bundle).

2. In the SAP Build Work Zone Administration Console, navigate to **Content Manager**.

3. Click **+ New** and select **UI Integration Card**.

4. In the upload dialog, click **Browse** and select the `.zip` card package you downloaded.

5. Click **Upload**. The card package is validated and imported. You should see the new card appear in the content manager list.

> [!IMPORTANT]
> If the upload fails with a validation error, check that you are uploading the correct `.zip` file as provided by your instructor.

## <a id="exercise-42-use-a-card-on-your-page"></a> Exercise 4.2 - Use a Card on Your Page

After completing these steps, one of the imported cards will appear on the page you created in Exercise 3.

1. Navigate to **Pages** in the Administration Console and open the page you created in Exercise 3.1.

2. Click the pen icon to enter edit mode.

3. In the section you created earlier, click **Add Content** and select **Card** from the widget gallery.

4. In the card picker, search for the card you uploaded in Exercise 4.1 and select it.

5. The card is added to your page. You may resize or reposition it by dragging within the section.

6. Click **Save** to save your changes.

## <a id="exercise-43-preview-the-site"></a> Exercise 4.3 - Preview the Site

After completing these steps you will have seen your card rendering live data on your page.

1. Navigate to **Site Directory** and click **Preview** on your site.

2. Navigate to the space and page you created in Exercise 3.

3. The card you added should be visible and displaying data from the backend service it is connected to.

4. Interact with the card (e.g. click on an item if the card supports navigation) and explore its behavior.

## Summary

You have uploaded a UI integration card package, placed a card on your custom workpage, and confirmed that it displays live data in the site preview.

Continue to - [Exercise 5 - Enable My Space](../ex5/README.md)
