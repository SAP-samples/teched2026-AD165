# Exercise 3 - Create a Work Zone Page and Space

In this exercise, you will create a custom workpage and organize it within a space, which is the main navigation concept in SAP Build Work Zone sites. You will then assign the space and page to a pre-configured custom role so that the right users can access it when they visit the site.

> [!NOTE]
> In SAP Build Work Zone sites (as opposed to workspaces), **spaces** provide the top-level navigation structure, and **pages** contain the actual content — widgets, cards, and apps. A space can group multiple related pages together. Spaces and pages are assigned to roles, which controls who can see them.

## <a id="exercise-31-create-a-new-page"></a> Exercise 3.1 - Create a New Page

After completing these steps you will have created a new workpage with a basic layout that is ready for content.

1. In the SAP Build Work Zone Administration Console, navigate to **Pages** in the left-hand menu.

2. Click **+ New Page** and give your page a meaningful name (e.g. **My Overview Page ###**, replacing ### with your participant number).

3. The page editor opens. Add a section to the page using the **+ Add Section** button and select **Freestyle** as the layout.

4. Add a **Text** widget to the section by clicking **Add Content** and selecting the text widget from the widget gallery. Enter a short welcome message of your choice.

5. Click **Save** to save your page.

> [!TIP]
> You will add more content (UI integration cards) to this page in Exercise 4. For now, a simple text widget is enough to get started.

## <a id="exercise-32-create-a-space"></a> Exercise 3.2 - Create a Space and Assign the Page

After completing these steps, your page will be organized inside a space that can be surfaced in the site navigation.

1. Navigate to **Spaces** in the left-hand menu of the Administration Console.

2. Click **+ New Space** and give it a name (e.g. **My Space ###**, replacing ### with your participant number).

3. Inside the space editor, click **+ Add Page** and select the page you created in Exercise 3.1.

4. Save the space.

## <a id="exercise-33-add-to-a-custom-role"></a> Exercise 3.3 - Add the Space to a Pre-Configured Custom Role

After completing these steps, the space will be visible to users who have the custom role assigned, making it accessible when they open your site.

1. Navigate to **Roles** in the left-hand menu.

2. Open the pre-configured custom role that your instructor has pointed out (e.g. **TechEd Participants**).

3. In the role editor, go to the **Spaces** tab and click **+ Assign Space**.

4. Select the space you created in Exercise 3.2 and confirm the assignment.

5. Save the role.

6. Navigate back to **Site Directory** and click **Preview** on your site to verify that the space appears in the site navigation for a user with this role.

## Summary

You have created a custom workpage and organized it in a space, then assigned the space to a pre-configured custom role. The page is now accessible to users with that role.

Continue to - [Exercise 4 - Add UI Integration Cards](../ex4/README.md)
