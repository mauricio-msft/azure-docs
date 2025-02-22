---
title: Connect your GCP account to Microsoft Defender for Cloud
description: Monitoring your GCP resources from Microsoft Defender for Cloud
author: memildin
ms.author: memildin
ms.date: 02/08/2021
ms.topic: quickstart
ms.service: security-center
manager: rkarlin
ms.custom: ignite-fall-2021
---

#  Connect your GCP accounts to Microsoft Defender for Cloud

[!INCLUDE [Banner for top of topics](./includes/banner.md)]

With cloud workloads commonly spanning multiple cloud platforms, cloud security services must do the same.

Microsoft Defender for Cloud protects workloads in Azure, Amazon Web Services (AWS), and Google Cloud Platform (GCP).

Onboarding your GCP accounts into Defender for Cloud, integrates GCP Security Command and Microsoft Defender for Cloud. Defender for Cloud thus provides visibility and protection across both of these cloud environments to provide:

- Detection of security misconfigurations
- A single view showing Defender for Cloud recommendations and GCP Security Command Center findings
- Incorporation of your GCP resources into Defender for Cloud's secure score calculations
- Integration of GCP Security Command Center recommendations based on the CIS standard into the Defender for Cloud's regulatory compliance dashboard

In the screenshot below you can see GCP projects displayed in Defender for Cloud's overview dashboard.

:::image type="content" source="./media/quickstart-onboard-gcp/gcp-account-in-overview.png" alt-text="3 GCP projects listed on Defender for Cloud's overview dashboard" lightbox="./media/quickstart-onboard-gcp/gcp-account-in-overview.png":::


## Availability

|Aspect|Details|
|----|:----|
|Release state:|General availability (GA)|
|Pricing:|Requires [Microsoft Defender for servers](defender-for-servers-introduction.md)|
|Required roles and permissions:|**Owner** or **Contributor** on the relevant Azure Subscription|
|Clouds:|:::image type="icon" source="./media/icons/yes-icon.png"::: Commercial clouds<br>:::image type="icon" source="./media/icons/no-icon.png"::: National/Sovereign (Azure Government, Azure China 21Vianet)|
|||

## Connect your GCP account

Create a connector for every organization you want to monitor from Defender for Cloud.

When connecting your GCP accounts to specific Azure subscriptions, consider the [Google Cloud resource hierarchy](https://cloud.google.com/resource-manager/docs/cloud-platform-resource-hierarchy#resource-hierarchy-detail) and these guidelines:

- You can connect your GCP accounts to Defender for Cloud in the *organization* level
- You can connect multiple organizations to one Azure subscription
- You can connect multiple organizations to multiple Azure subscriptions
- When you connect an organization, all *projects* within that organization are added to Defender for Cloud

Follow the steps below to create your GCP cloud connector. 

### Step 1. Set up GCP Security Command Center with Security Health Analytics

For all the GCP projects in your organization, you must also:

1. Set up **GCP Security Command Center** using [these instructions from the GCP documentation](https://cloud.google.com/security-command-center/docs/quickstart-scc-setup).
1. Enable **Security Health Analytics** using [these instructions from the GCP documentation](https://cloud.google.com/security-command-center/docs/how-to-use-security-health-analytics).
1. Verify that there is data flowing to the Security Command Center.

The instructions for connecting your GCP environment for security configuration follow Google's recommendations for consuming security configuration recommendations. The integration leverages Google Security Command Center and will consume additional resources that might impact your billing.

When you first enable Security Health Analytics, it might take several hours for data to be available.


### Step 2. Enable GCP Security Command Center API

1. From Google's **Cloud Console API Library**, select each project in the organization you want to connect to Microsoft Defender for Cloud.
1. In the API Library, find and select **Security Command Center API**.
1. On the API's page, select **ENABLE**.

Learn more about the [Security Command Center API](https://cloud.google.com/security-command-center/docs/reference/rest/).


### Step 3. Create a dedicated service account for the security configuration integration

1. In the **GCP Console**, select a project from the organization in which you're creating the required service account. 

    > [!NOTE]
    > When this service account is added at the organization level, it'll be used to access the data gathered by Security Command Center from all of the other enabled projects in the organization. 

1. In the **Navigation menu**, Under **IAM & admin** options, select **Service accounts**.
1. Select **CREATE SERVICE ACCOUNT**.
1. Enter an account name, and select **Create**.
1. Specify the **Role** as **Defender for Cloud Admin Viewer**, and select **Continue**.
1. The **Grant users access to this service account** section is optional. Select **Done**.
1. Copy the **Email value** of the created service account, and save it for later use.
1. In the **Navigation menu**, Under **IAM & admin** options, select **IAM**
    1. Switch to organization level.
    1. Select **ADD**.
    1. In the **New members** field, paste the **Email value** you copied earlier.
    1. Specify the role as **Defender for Cloud Admin Viewer** and then select **Save**.
        :::image type="content" source="./media/quickstart-onboard-gcp/iam-settings-gcp-permissions-admin-viewer.png" alt-text="Setting the relevant GCP permissions.":::


### Step 4. Create a private key for the dedicated service account
1. Switch to project level.
1. In the **Navigation menu**, Under **IAM & admin** options, select **Service accounts**.
1. Open the dedicated service account and select Edit.
1. In the **Keys** section, select **ADD KEY** and then **Create new key**.
1. In the Create private key screen, select **JSON**, and then select **CREATE**.
1. Save this JSON file for later use.


### Step 5. Connect GCP to Defender for Cloud
1. From Defender for Cloud's menu, select **Cloud connectors**.
1. Select add GCP account.
1. In the onboarding page, do the following and then select **Next**.
    1. Validate the chosen subscription.
    1. In the **Display name** field, enter a display name for the connector.
    1. In the **Organization ID** field, enter your organization's ID. If you don't know it, see [Creating and managing organizations](https://cloud.google.com/resource-manager/docs/creating-managing-organization).
    1. In the **Private key** file box, browse to the JSON file you downloaded in [Step 4. Create a private key for the dedicated service account](#step-4-create-a-private-key-for-the-dedicated-service-account).


### Step 6. Confirmation

When the connector is successfully created and GCP Security Command Center has been configured properly:

- The GCP CIS standard will be shown in the Defender for Cloud's regulatory compliance dashboard.
- Security recommendations for your GCP resources will appear in the Defender for Cloud portal and the regulatory compliance dashboard 5-10 minutes after onboard completes:
    :::image type="content" source="./media/quickstart-onboard-gcp/gcp-resources-in-recommendations.png" alt-text="GCP resources and recommendations in Defender for Cloud's recommendations page":::


## Monitoring your GCP resources

As shown above, Microsoft Defender for Cloud's security recommendations page displays your GCP resources together with your Azure and AWS resources for a true multi-cloud view.

To view all the active recommendations for your resources by resource type, use Defender for Cloud's asset inventory page and filter to the GCP resource type in which you're interested:

:::image type="content" source="./media/quickstart-onboard-gcp/gcp-resource-types-in-inventory.png" alt-text="Asset inventory page's resource type filter showing the GCP options"::: 


## FAQ - Connecting GCP accounts to Microsoft Defender for Cloud

### Can I connect multiple GCP organizations to Defender for Cloud?
Yes. Defender for Cloud's GCP connector connects your Google Cloud resources at the *organization* level. 

Create a connector for every GCP organization you want to monitor from Defender for Cloud. When you connect an organization, all projects within that organization are added to Defender for Cloud.

Learn about the Google Cloud resource hierarchy in [Google's online docs](https://cloud.google.com/resource-manager/docs/cloud-platform-resource-hierarchy).


### Is there an API for connecting my GCP resources to Defender for Cloud?
Yes. To create, edit, or delete Defender for Cloud cloud connectors with a REST API, see the details of the [Connectors API](/rest/api/securitycenter/connectors).

## Next steps

Connecting your GCP account is part of the multi-cloud experience available in Microsoft Defender for Cloud. For related information, see the following page:

- [Connect your AWS accounts to Microsoft Defender for Cloud](quickstart-onboard-aws.md)
- [Google Cloud resource hierarchy](https://cloud.google.com/resource-manager/docs/cloud-platform-resource-hierarchy)--Learn about the Google Cloud resource hierarchy in Google's online docs
