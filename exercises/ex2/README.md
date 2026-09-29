# Exercise 2 - Integrate Business Content

In this exercise, you will connect your Work Zone site to business content from backend systems using the Channel Manager. You will learn about content federation, assign a content channel and roles to your site, and then preview the result to see how business apps appear in your site.

> [!NOTE]
> Content federation in SAP Build Work Zone allows you to pull in apps, roles, and catalogs from connected SAP backend systems (such as SAP S/4HANA or SAP SuccessFactors) and surface them to users in a unified, role-based experience — without duplicating any configuration.

## <a id="exercise-21-get-to-know-the-channel-manager"></a> Exercise 2.1 - Get to Know the Channel Manager and Learn About Federation

After completing these steps you will understand how the Channel Manager works and what federation means in the context of SAP Build Work Zone.

1. In the SAP Build Work Zone Administration Console, navigate to **Channel Manager** in the left-hand menu.

2. Review the list of configured content channels. Each channel represents a connection to a backend system from which apps and roles can be federated.

3. Select one of the available channels and explore its details:
   - **Status**: shows whether the channel is active and the last time it was synchronized
   - **Content**: lists the roles and catalogs available from this backend

4. Click **Fetch Updated Content** (or the equivalent refresh action) to make sure the content from the channel is up to date.

> [!NOTE]
> Content channels need to be set up by an administrator with the appropriate backend connectivity in place. In this session, the channels are pre-configured for you.

## <a id="exercise-22-assign-content"></a> Exercise 2.2 - Assign a Content Channel or Single Roles to Your Site

After completing these steps, selected business content from a backend system will be assigned to your Work Zone site, making the corresponding apps available to users with the right role.

1. Navigate to **Site Directory** and open the settings of your site.

2. Go to the **Roles** section (or **Content Channels** — your instructor will guide you on the exact navigation based on your system version).

3. Assign the pre-configured content channel **or** select specific roles from the available backend roles and assign them to your site.

4. Save your changes.

> [!TIP]
> Assigning a full content channel brings in all roles and apps from that channel. Assigning individual roles gives you more fine-grained control over what appears in your site.

## <a id="exercise-23-preview-your-site"></a> Exercise 2.3 - Preview Your Site

After completing these steps, you will have seen how the federated business apps appear in your site.

1. Navigate back to **Site Directory** and click **Preview** on your site.

2. Open the **Applications** section (if available) to see the business apps that have been surfaced from the backend system.

3. Note how the apps are organized by catalog and how role-based access ensures that only relevant apps are shown to the right users.

## Summary

You have connected your Work Zone site to business content from a backend system using the Channel Manager. You assigned a content channel and roles to your site and saw the federated apps appear in the site preview.

Continue to - [Exercise 3 - Create a Work Zone Page and Space](../ex3/README.md)
