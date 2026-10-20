# Exercise 2 - Integrate Business Content

In this exercise, you will first explore the admin environment of SAP Build Work Zone, standard edition. You will then check the connectivity to an SAP S/4HANA Public Cloud system using the Channel Manager, assign a content channel and roles to your site, explore the federated content in the Content Manager, and check the result in runtime to see how business apps appear in your site.

> [!NOTE]
> Content federation in SAP Build Work Zone allows you to pull in roles including all apps, spaces, pages, and catalogs from connected backend systems (such as SAP S/4HANA or SAP SuccessFactors) and surface them to users in a unified, role-based experience. From a user perspective, this means a single place to start the working day, regardless of how many backend systems an organization runs.

---

## <a id="exercise-21-admin-environment"></a> Exercise 2.1 - Get to Know the Admin Environment

### What you'll achieve
After completing these steps you will understand the admin environment of SAP Build Work Zone, standard edition, and know where to manage site content.

---

### Steps

1. **Leave the Site settings** — go back to the **Site Directory** by clicking the link in the breadcrumb.

   ![Site Settings with the Site Directory breadcrumb link highlighted](images/Image_02_0010.png)

2. **Understand the admin areas** — in the left-hand navigation, you now see the areas **Site Directory**, **Content Manager**, **Channel Manager**, **Import Monitor**, and **Settings**.

   ![Site Directory with all admin areas in the left-hand navigation highlighted](images/Image_02_0020.png)

---

Here is a summary of what administrators can do in these different tools:

**Site Directory**
Lists all Work Zone sites in your subaccount. You already used it in the last exercise. From here you create new sites, manage site settings, transport sites, and launch a site in runtime.

**Content Manager**
The central place for creating and managing all content items — pages, spaces, roles, and apps. This is where you create new content and manage what is available in your subaccount. You will use it in Exercise 3.

**Channel Manager**
Manages the connections to backend content providers. This is where you trigger content updates and review the federated content available from each connected system. This is the area you will be using in this exercise.

**Import Monitor**
Helps administrators track past and running imports.

**Settings**
Manage features that affect all the sites in a subaccount, e.g. notification settings, custom domains, and others.

---

## <a id="exercise-22-get-to-know-the-channel-manager"></a> Exercise 2.2 - Get to Know the Channel Manager and Learn About Federation

### What you'll achieve
After completing these steps you will understand how the Channel Manager works and what federation means in the context of SAP Build Work Zone.

---

Content federation follows a simple flow:

1. An **S/4HANA administrator** defines the **exposure scope**: which roles to expose, and which navigation structures to include: **spaces and pages** (the modern paradigm), **groups** (the classic tile-group layout), or both. Each exposed role carries its full content: all apps and catalogs plus the selected structure entities.
2. A **Work Zone administrator** creates a **content channel** that points to the S/4HANA system.
3. When the channel is **synchronized**, all exposed roles and their content become available in Work Zone and can be assigned to sites and users.

The key benefit: **content ownership stays in the backend system**. Roles, apps, and navigation structures are defined and maintained where S/4HANA administrators know best — Work Zone simply consumes what is exposed.

### Steps

1. **Navigate to Channel Manager** — in the left-hand menu, click **Channel Manager**.

   ![Site Directory with Channel Manager highlighted in the left-hand navigation](images/Image_02_0030.png)

2. **Review the configured channels** — you will see at least three channels:

   **HTML5 Apps**: When you subscribe to SAP Build Work Zone, standard edition, this provider is created automatically. It starts empty — any app deployed to SAP BTP is added to it automatically, making it available to surface in your site.

   **SAP S/4HANA Cloud**: This channel connects to an SAP S/4HANA Cloud, public edition system and federates role-based content (roles, catalogs, apps, spaces, and pages) into Work Zone. The connection is backed by destinations configured in SAP BTP cockpit.

   **Demo Generic Package**: This channel was used to bring UI integration cards into the system. UI integration cards are lightweight, embeddable content snippets that can display live data from backend services directly on a Work Zone page. You will work with these cards later in this exercise.

   ![Channel Manager showing the four configured content channels](images/Image_02_0040.png)

3. **Check the Status column** — note whether each channel is active and when it was last synchronized.

4. **Inspect the SAP S/4HANA Cloud properties** — click the **pencil icon** on the **S4HANA Public Cloud** channel to open its properties. The key fields to note are:

   - **Provider ID / Name**: unique identifier for this channel
   - **Design Time Destination**: the BTP destination used to fetch roles and content metadata from the backend
   - **Runtime Destination**: the destination used when users actually launch apps (can differ from design time)
   - **Automatically add all content items to subaccount**: it is recommended to set this to *On* to avoid manual selection steps. This setting is planned to be removed in a future release.

   Click **Cancel** to close the properties without making changes.

   ![Edit Content Provider dialog for the S4HANA Public Cloud channel with Cancel highlighted](images/Image_02_0050.png)

5. **Open the content report** — click the **report icon** on the **S4HANA Public Cloud** channel. You see the *Last Update Status* showing the content entities that were changed during the last update of the content channel. This view might be empty.

   ![View Last Updates Status of S4HANA Public Cloud content report](images/Image_02_0060.png)

6. **View the exposed content** — to see the full exposed content, i.e. all the roles, catalogs, and apps that have been federated from the S/4HANA system and are available to assign to your site, click **Content Item Summary**. You can see how many roles, apps etc. were exposed. Click **Close**.


   ![S4HANA Public Cloud content report showing federated content counts by category](images/Image_02_0065.png)


> [!NOTE]
> Content channels need to be set up by an administrator with the appropriate backend connectivity in place. These channels were preconfigured for this session, but you will later add a content package.

---

## <a id="exercise-23-assign-content"></a> Exercise 2.3 - Assign Roles and Content Packages to Your Site

### What you'll achieve
After completing these steps, selected roles from the SAP S/4HANA Cloud channel and two content packages will be assigned to your Work Zone site, making the corresponding apps available to users with the right role.

---

In this exercise you assign individual roles from the S/4HANA channel to your site rather than the full content channel.

> [!NOTE]
> Assigning individual roles rather than the full S/4HANA channel keeps the registered content set smaller, which makes the initial role activation on your site noticeably faster.

---

### Steps

1. **Open your site settings** — navigate to **Site Directory** and open the settings of your site by clicking the cog icon again.

   ![Site Directory with the cog icon highlighted on the site card](images/Image_02_0120.png)

   ![Site Settings with Role Assignments highlighted in the left-hand navigation](images/Image_02_0130.png)

2. **Open the Roles tab** — in the **Role Assignments** section, make sure you are on the **Roles** tab. Click **Edit** to switch to edit mode.

3. **Assign the S/4HANA roles** — in the search field, type **AD165** and click the **Search icon**. This filters to the SAP S/4HANA roles that were created specifically for this session. Assign all of them by turning their switches to **On**.

   ![Role Assignments — Display Assign Channels button](images/Image_02_0135.png)

4. **Assign two further channels** — switch to the **Content Channels** tab (you do not need to save yet) and click **Assign Channels**. 

   ![Role Assignments — Display Assign Channels button](images/Image_02_0140.png)

5. **Select content packages with UI Integration cards** — assign the two content channels:
   - **Demo Generic Package**
   - **TechEd Employee Services Package**

   They contain UI integration cards that you will use later to enrich a page you are creating.

6. **Save your changes** — click Save and confirm the *Information* pop-up with **OK**.

   ![Role Assignments showing the S4HANA Public Cloud channel and the packages assigned, with Go to Site and Edit highlighted](images/Image_02_0150.png)

---

## <a id="exercise-24-explore-content-manager"></a> Exercise 2.4 - Explore Federated Content in the Content Manager

### What you'll achieve
After completing these steps you will have seen how federated content from the SAP S/4HANA Cloud channel appears in the Content Manager, and you will understand the structure of a federated role.

---

Assigning the full S/4HANA content channel brings in an entire SAP S/4HANA system's worth of roles, apps, and navigation structures — Work Zone registers all of it in the background, which can take a moment. You will now explore the federated content in the Content Manager so that by the time you open the site in runtime, the assignment will be fully in effect.

The Content Manager gives administrators a unified view of all content items available in the subaccount — whether created manually or pulled in from a connected backend. You can use the **Provider** filter in the header to narrow the list to content from a specific channel, which makes it easy to verify what has been federated and to inspect individual items.

### Steps

1. **Navigate to Content Manager** — in the left-hand menu, click **Content Manager**.

   ![Channel Manager with Content Manager highlighted in the left-hand navigation](images/Image_02_0070.png)

2. **Filter by content provider** — in the Content Manager header, open the **Provider** filter and select **S4HANA Public Cloud**. The list now shows only the roles that were federated from the S/4HANA system.

   ![Content Manager with the provider filter dropdown open and SAP S/4HANA Cloud highlighted](images/Image_02_0080.png)

   ![Content Manager filtered to S4HANA Public Cloud showing all federated roles, with Warehouse Clerk highlighted](images/Image_02_0090.png)

3. **Inspect a federated role** — locate one of the federated roles (e.g. **Warehouse Clerk**) and click on it to open the role details.

4. **Review the assigned content** — in the role editor, check the **Apps** and **Spaces** tabs to see which apps and spaces are included in this role. You can also click an app in the list to view more details. Note that these items are read-only — federated content can only be modified in the originating backend system.

   ![Warehouse Clerk role showing the Apps tab with a pop-up app detail and the Spaces tab highlighted](images/Image_02_0100.png)

   ![Warehouse Clerk role on the Spaces tab showing one assigned space, with the Content Manager breadcrumb highlighted](images/Image_02_0110.png)

> [!NOTE]
> Content items that come from a backend channel are marked with the provider name. They cannot be edited in Work Zone — any changes to roles, apps, or spaces must be made in the SAP S/4HANA system and then re-exposed via the channel.

---

## <a id="exercise-25-preview-your-site"></a> Exercise 2.5 - Open Your Site in Runtime

### What you'll achieve
After completing these steps you will have explored the Work Zone standard runtime experience with federated S/4HANA content.

---

### Steps

1. **Open the site** — navigate to **Site Directory** and click the **Go to Site** on your site's tile to open your site in runtime. The site opens in a new tab.

   ![Site Directory with Go to Site link](images/Image_02_0155.png)

2. **Check the custom logo** — notice the logo you added in Exercise 1.2 displayed in the shell bar.

   ![Work Zone runtime site showing the custom cat logo and the user profile icon highlighted](images/Image_02_0160.png)

3. **Explore Settings** — click the user icon in the shell bar to open the user menu and select **Settings**.

   ![User profile menu open with the Settings option highlighted](images/Image_02_0170.png)

In the **Language and Region** area, users can select their preferred language from the list you configured in Exercise 1.3. Adjust the language if you like, then close the settings by clicking **Save** or **Cancel**. 

> [!NOTE]
> If you want, you can adjust the language to explore the feature. When you are done, we recommend switching back to English — this will make it easier to follow the remaining exercise steps.


   ![User Settings dialog open on the Language and Region page](images/Image_02_0180.png)

4. **Browse the federated spaces** — in the top navigation menu, all entries come from spaces that belong to the S/4HANA roles you assigned to your site in Exercise 2.4. Click the little arrow next to some of them to see the pages assigned to this space.

   ![Work Zone runtime showing the Purchasing space navigation menu open with the Overview page highlighted](images/Image_02_0190.png)


> [!NOTE]
> You only see these spaces because the corresponding roles have been assigned to your user upfront. There are two prerequisites for content to become available to a specific user in a site:
> 1. The content needs to be assigned to a role that is assigned to the user.
> 2. The content needs to be assigned to a role that is assigned to the site.

5. **Launch an app** — On the **Overview** page in the **Purchasing** space, click on **Monitor Purchase Order Items**. It opens in a new browser tab — this behavior is defined by the content exposure in the S/4HANA system.

   ![Purchasing Overview page with the Monitor Purchase Order Items tile highlighted](images/Image_02_0200.png)

6. **Display data** — in the app, select **EUR** as the *Display Currency* because this is a mandatory field. Type EUR directly into the entry field — the value help may take a moment to load after the page opens, so typing is faster. Then click **Go** to see the list of open purchase order items.

   ![Monitor Purchase Order Items app with EUR entered as the display currency and the Go button highlighted](images/Image_02_0210.png)

7. **Navigate back** — close the browser tab to return to your Work Zone site.

---

## Summary

You explored the admin environment of SAP Build Work Zone, standard edition. You connected your Work Zone instance to business content from an S/4HANA system using the Channel Manager, assigned a content channel and roles to your site, explored the federated content in the Content Manager, and saw the federated apps appear in runtime.

Continue to - [Exercise 3 - Create a Work Zone Page and Space](../ex3/README.md)
