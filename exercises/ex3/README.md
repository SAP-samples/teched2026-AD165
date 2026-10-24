# Exercise 3 - Create a Work Zone Page and Space

In this exercise, you will create a custom page and organize it in a space to make it visible in the site navigation, then assign it to a role so the right users can access it. You will create an entry page for employees with some self services and some purchaser specific cards.

> [!NOTE]
> In SAP Build Work Zone sites, **spaces** provide the top-level navigation structure, and **pages** contain the actual content — cards and apps. A space can group multiple related pages together. Spaces and pages are assigned to roles, which controls who can see them.

---

<a id="exercise-31-create-a-new-page"></a>
## Exercise 3.1 - Create a New Page

### What you'll achieve
By completing these steps, you've built a Work Zone page that brings employee self-service apps and purchasing cards together in one place. This is the same approach you'd use to consolidate content from multiple sources — different backend systems, custom apps deployed on SAP BTP, or any combination of both. The cards surface key information directly on the page, so users get what they need at a glance — without having to navigate somewhere else first.

---

### Steps

1. **Navigate to Content Manager** — go back to the browser tab with your Work Zone administration environment. If you are still on the *Role Assignments* tab, first navigate back to the *Site Directory* via the breadcrumb to see the left-hand menu. Then click **Content Manager**.

   ![Navigate to Site Directory via breadcrumb](images/Image_03_0010.png)

2. **Create a new page** — in the Content Manager, click **Create** and select **Page**. The page editor opens.

   ![Create a new Page in Content Manager](images/Image_03_0020.png)

3. **Enter a title** — enter a meaningful title (e.g. **Welcome**), and enter your participant number as description, so you will be able to find your page easily later. If you want, you can also add a longer description. The title will become visible on top of the new page and in the menu, in case there is more than one page assigned to the respective page.

   ![Enter page title and description, then click Add Section](images/Image_03_0030.png)

4. **Add a first section** — click **Add Section** and enter the header **Purchasing Insights**.

   ![Section with Purchasing Insights header and Add Content button](images/Image_03_0040.png)

5. **Find cards and tiles** — click **Add Content** in the section. This opens the **App Finder** which allows you to add both tiles and cards to your page.

6. **Add cards** — move the switch on top of the App Finder to **Cards** and click the card **Unacknowledged POs** to add it. You get back to the page view and see the card in a preview display without data.

   ![Switch to Cards in App Finder and select Unacknowledged POs](images/Image_03_0050.png)

   To add another card, click the **+** sign right of your card to add a new column and do the same steps to add the **Posted Invoice in Current Period** card in addition. Do not forget to switch to **Cards** in the *App Finder*.

   ![Click the + sign to add a new column](images/Image_03_0060.png)

   ![Both cards added to the Purchasing Insights section](images/Image_03_0070.png)

7. **Add a second section** — add a new section by clicking the **+** sign below the current section, leave the header empty and add the cards **Purchasing Trends** and **Supplying by Departments**.

   ![Second section with Purchasing Trends and Supplying by Departments cards](images/Image_03_0080.png)

8. **Add another cell for tiles** — click the **+** sign to the right of the *Supplying by Departments* card again. This time, you will add some dynamic tiles. Use the search to add the tiles for the following apps **Operational Supplier Evaluation**, **Off-Contract Spend**, and **Overdue Purchase Order Items**. You can find them and click their checkbox one by one. After selecting all tiles, click the **Add(3)** button in the lower right corner.

   ![Search for tiles and select them, then click Add(3)](images/Image_03_0090.png)

9. **Save your page.**

   ![Saved page overview in Content Manager](images/Image_03_0110.png)

> [!TIP]
> If you still have time at the end of the session, you can add your own UI integration card to this page in Exercise 8 (Optional).

---

<a id="exercise-32-create-a-space"></a>
## Exercise 3.2 - Create a Space and Assign the Page

### What you'll achieve
After completing these steps your page will be organized inside a space that can be surfaced in the site navigation.

---

### Steps

1. **Create a new space** — use the breadcrumb to navigate back to the Content Manager, click **Create** and select **Space**.

   ![Create a new Space in Content Manager](images/Image_03_0120.png)

2. **Enter a title** — give the space a title (e.g. **Get Started**) and add your participant number to the **Description** to allow you to find the space easily. The title will be displayed in the menu of the site.

> [!TIP]
> You can enter a Sort Priority which determines in which position the space will be displayed. You can keep the default value 0.0 to display your space to the left of the federated spaces. SAP S/4HANA spaces created from SAP delivered space templates have positive sort priority values if not customized differently.

3. **Assign the page** — in the lower part of the screen, you see the available **Pages**. Identify the page you created in Exercise 3.1 (search for your participant number ### if needed) and turn the switch for your page to **On** in the *Assignment Status* column.

4. **Save the space.**

   ![New space with title, description, and page assigned](images/Image_03_0130.png)

---

<a id="exercise-33-add-to-a-custom-role"></a>
## Exercise 3.3 - Add the Space to a Pre-Configured Custom Role

### What you'll achieve
After completing these steps the space will be visible to users who have the custom role assigned, making it accessible when they open your site.

---

Because you do not have access to the BTP cockpit in this workshop, a custom role has been preconfigured for you and already assigned to your user.

---

### Steps

1. **Navigate to Content Manager** — go back to the Content Manager using the breadcrumb.

2. **Open the custom role** — find the pre-configured custom role that has been created for your user and click it. The role is called **Purchaser Custom Role + \<your participant number\>**. You can search for your participant number, or use the **All Items** filter to restrict the list to roles only.

   ![Search for your custom role in Content Manager](images/Image_03_0140.png)

3. **Switch to Edit Mode** — click the **Edit** button.

   ![Open the custom role and click Edit](images/Image_03_0150.png)

4. **Assign the space** — go to the **Spaces** tab and assign the space you created in Exercise 3.2 by turning its switch to **On** in the *Assignment Status* column.

5. **Save the role.**

   ![Spaces tab with Get Started space assigned, then save](images/Image_03_0160.png)

---

<a id="exercise-34-assign-role-to-site"></a>
## Exercise 3.4 - Assign the Custom Role to Your Site

### What you'll achieve
After completing these steps the custom role will be assigned to your site, making the space visible to users who have that role.

---

For content to appear in the site, the role it is assigned to must also be assigned to the site itself. You do this in the Site Settings.

### Steps

1. **Open the site settings** — navigate to **Site Directory** and open the settings of your site.

   ![Navigate to Site Directory](images/Image_03_0170.png)

   ![Open site settings from the Site Directory](images/Image_03_0180.png)

2. **Open the Role Assignments section** — go to the **Role Assignments** section and make sure you are on the **Roles** tab. You see a long list of roles assigned to your site. 

3. **Switch to Edit mode** — click the **Edit** button.

   ![Role Assignments](images/Image_03_0190.png)

4. **Assign the custom role** — enter your *participant number* into the search field to find the **Purchaser Custom Role + \<your participant number\>** and turn its switch to **On** in the *Assignment Status* column.

5. **Save your changes.**

   ![Assign the custom role in Role Assignments and save](images/Image_03_0195.png)

6. **Verify in the site** — click **Go to Site** on your site and confirm that the new space appears in the site navigation. Since the space is the first one in the menu, you immediately see the page you created.

   ![Click Go to Site](images/Image_03_0200.png)

   ![The Get Started space appears in the site navigation with your page content](images/Image_03_0210.png)

---

## Summary

You created a page, organized it in a space, assigned the space to a role, and assigned that role to your site so it appears in the site navigation for the right users.

Continue to - [Exercise 4 - Enable My Space](../ex4/README.md)
