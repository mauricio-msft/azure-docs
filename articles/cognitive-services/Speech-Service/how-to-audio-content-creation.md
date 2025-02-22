---
title: Audio Content Creation - Speech service
titleSuffix: Azure Cognitive Services
description: Audio Content Creation is an online tool that allows you to customize and fine-tune Microsoft's text-to-speech output for your apps and products.
services: cognitive-services
author: PatrickFarley
manager: nitinme
ms.service: cognitive-services
ms.subservice: speech-service
ms.topic: conceptual
ms.date: 01/31/2020
ms.author: pafarley
---

# Improve synthesis with the Audio Content Creation tool

[Audio Content Creation](https://aka.ms/audiocontentcreation) is an easy-to-use and powerful tool that lets you build highly natural audio content for a variety of scenarios, like audiobooks, news broadcasts, video narrations, and chat bots. With Audio Content Creation, you can fine-tune text-to-speech voices and design customized audio experiences in an efficient and low-cost way.

The tool is based on [Speech Synthesis Markup Language (SSML)](speech-synthesis-markup.md). It allows you to adjust text-to-speech output attributes in real time or batch synthesis, such as voice characters, voice styles, speaking speed, pronunciation, and prosody.

You can have easy access to more than 150 pre-built voices across 60+ different languages, including the state-of-the-art neural TTS voices, and your custom voice if you have built one.

See the [video tutorial](https://youtu.be/ygApYuOOG6w) for Audio Content Creation.

## How to Get Started?

Audio Content Creation is a free tool, but you will pay for the Azure Speech service you consume. To work with the tool, you need to log in with an Azure account and create a speech resource. For each Azure account, you have monthly free speech quotas which include 500,000 characters for Neural TTS voices (per month), 5 million characters for standard and custom voices (per month), and 1 custom voice endpoint hosting service (per month). The monthly allotted amount is usually enough for a small content team of around 3-5 people. Here are the steps for how to create an Azure account and get a speech resource.

### Step 1 - Create an Azure account

To work with Audio Content Creation, you need to have a [Microsoft account](https://account.microsoft.com/account) and an [Azure account](https://azure.microsoft.com/free/ai/). Follow these instructions to [set up the account](./overview.md#try-the-speech-service-for-free).

[Azure portal](https://portal.azure.com/) is the centralized place for you to manage your Azure account. You can create the speech resource, manage the product access, and monitor everything from simple web apps to complex cloud deployments.

### Step 2 - Create a Speech resource

After signing up for the Azure account, you need to create a Speech resource under your Azure account to access Speech services. View the instructions for [how to create a Speech resource](./overview.md#create-the-azure-resource).

It takes a few moments to deploy your new Speech resource. Once the deployment is complete, you can start the Audio Content Creation journey.

 > [!NOTE]
   > If you plan to use neural voices, make sure that you create your resource in [a region that supports neural voices](regions.md#neural-and-standard-voices).

### Step 3 - Log into the Audio Content Creation with your Azure account and Speech resource

1. After getting the Azure account and the Speech resource, you can log into [Audio Content Creation](https://aka.ms/audiocontentcreation) by clicking **Get started**.
2. The home page lists all the products under Speech Studio. Click **Audio Content Creation** to start.
3. The **Welcome to Speech Studio** page will appear to you to set up the speech service. Select the Azure subscription and the Speech resource you want to work on. Click **Use resource** to complete the settings. When you log into the Audio Content Creation tool for the Next time, we will link you directly to the audio work files under the current speech resource. You can check your Azure subscriptions details and status in [Azure portal](https://portal.azure.com/). If you do not have available speech resource and you are the owner or admin of an Azure subscription, you can also create a new Speech resource in Speech Studio by clicking **Create a new resource**. If you are a user role for a certain Azure subscription, you may not have the permission to create a new speech resource. Please contact your admin to get the speech resource access. 
4. You can modify your Speech resource at any time with the **Settings** option, located in the top nav.
5. If you want to switch directory, please go the **Settings** or your profile to operate. 

## How to use the tool?

This diagram shows the steps it takes to fine-tune text-to-speech outputs. Use the links below to learn more about each step.

:::image type="content" source="media/audio-content-creation/audio-content-creation-diagram.jpg" alt-text="A diagram of the steps it takes to fine-tune text-to-speech outputs":::

1. Choose the speech resource you want to work on.
2. [Create an audio tuning file](#create-an-audio-tuning-file) using plain text or SSML scripts. Type or upload your content in to Audio Content Creation.
3. Choose the voice and the language for your script content. Audio Content Creation includes all of the [Microsoft text-to-speech voices](language-support.md#text-to-speech). You can use standard, neural, or your own custom voice.
   > [!NOTE]
   > Gated access is available for Custom Neural Voices, which allow you to create high-definition voices similar to natural-sounding speech. For additional details, see [Gating process](./text-to-speech.md).

4. Select the content you want to preview and click the **play** icon (a triangle) to preview the default synthesis output. Please note that if you make any changes on the text, you need to click the **Stop** icon and then click **play** icon again to re-generate the audio with changed scripts. 
5. Improve the output by adjusting pronunciation, break, pitch, rate, intonation, voice style, and more. For a complete list of options, see [Speech Synthesis Markup Language](speech-synthesis-markup.md). Here is a [video](https://youtu.be/ygApYuOOG6w) to show how to fine-tune speech output with Audio Content Creation.
6. Save and [export your tuned audio](#export-tuned-audio). When you save the tuning track in the system, you can continue to work and iterate on the output. When you're satisfied with the output, you can create an audio creation task with the export feature. You can observe the status of the export task and download the output for use with your apps and products.

## Create an audio tuning file

There are two ways to get your content into the Audio Content Creation tool.

**Option 1:**

1. Click **New** > **file** to create a new audio tuning file.
2. Type or paste your content into the editing window. The characters for each file is up to 20,000. If your script is longer than 20,000 characters, you can use Option 2 to automatically split your content into multiple files.
3. Don't forget to save.

**Option 2:**

1. Click **Upload** to import one or more text files. Both plain text and SSML are supported. If your script file is more than 20,000 characters, please split the file by paragraphs, by character or by regular expressions.
3. When you upload your text files, make sure that the file meets these requirements.

   | Property | Value / Notes |
   |----------|---------------|
   | File format | Plain text (.txt)<br/> SSML text (.txt)<br/> Zip files aren't supported |
   | Encoding format | UTF-8 |
   | File name | Each file must have a unique name. Duplicates aren't supported. |
   | Text length | Character limitation of the text file is 20,000. If your files exceed the limitation, please split the files with the instructions in the tool. |
   | SSML restrictions | Each SSML file can only contain a single piece of SSML. |

**Plain text example**

```txt
Welcome to use Audio Content Creation to customize audio output for your products.
```

**SSML text example**

```xml
<speak xmlns="http://www.w3.org/2001/10/synthesis" xmlns:mstts="http://www.w3.org/2001/mstts" version="1.0" xml:lang="en-US">
    <voice name="Microsoft Server Speech Text to Speech Voice (en-US, ChristopherNeural)">
    Welcome to use Audio Content Creation <break time="10ms" />to customize audio output for your products.
    </voice>
</speak>
```

## Export tuned audio

After you've reviewed your audio output and are satisfied with your tuning and adjustment, you can export the audio.

1. Click **Export** to create an audio creation task. **Export to Audio Library** is recommended as it supports the long audio output and the full audio output experience. You can also download the audio to your local disk directly, but only the first 10 minutes are available.
2. Choose the output format for your tuned audio. A list of supported formats and sample rates is available below.
3. You can view the status of the task on the **Export task** tab. If the task fails, see the detailed information page for a full report.
4. When the task is complete, your audio is available for download on the **Audio Library** tab.
5. Click **Download**. Now you're ready to use your custom tuned audio in your apps or products.

**Supported audio formats**

| Format | 16 kHz sample rate | 24 kHz sample rate |
|--------|--------------------|--------------------|
| wav | riff-16khz-16bit-mono-pcm | riff-24khz-16bit-mono-pcm |
| mp3 | audio-16khz-128kbitrate-mono-mp3 | audio-24khz-160kbitrate-mono-mp3 |

## How to add/remove Audio Content Creation users?

If more than one user wants to use Audio Content Creation, you can grant user access to the Azure subscription and the speech resource. If you add a user to an Azure subscription, the user can access all the resources under the Azure subscription. But if you only add a user to a speech resource, the user will only have access to the speech resource, and cannot access other resources under this Azure subscription. A user with access to the speech resource can use Audio Content Creation.

The user need to prepare a [Microsoft account](https://account.microsoft.com/account). If the user do not have a Microsoft account, create one with just a few minutes. The user can use the existing email and link as a Microsoft account, or creat a new outlook email as Microsoft account.


### Add users to a speech resource

Follow these steps to add a user to a speech resource so they can use Audio Content Creation.

1. Search for **Cognitive services** in the [Azure portal](https://portal.azure.com/), select the speech resource that you want to add users to.
2. Click **Access control (IAM)**. Select **Add** > **Add role assignment (Preview)** to open the Add role assignment pane. 
1. On the **Role** tab, select the **Cognitive Service User** role. If you want to give the user ownership of this speech resource, you can select the **Owner** role.
1. On the **Members** tab, type in user's email address and select the user in the directory. The email address must be a **Microsoft account**, which is trusted by Azure active directory. Users can easily sign up a [Microsoft account](https://account.microsoft.com/account) using a personal email address. 
1. On the **Review + assign** tab, select **Review + assign** to assign the role.
1. The user will receive an email invitation. Accept the invitation by clicking **Accept invitation** > **Accept to join Azure** in the email. Then the user will be redirected to the Azure portal. The user does not need to take further action in the Azure portal. After a few moments, the user is assigned the role at the speech resource scope, and will have the access to this speech resource. If the user didn't receive the invitation email, you can search the user's account under "Role assignments" and go inside the user's profile. Find "Identity" -> "Invitation accepted", and click **(manage)** to resend the email invitation. You can also copy the invitation link to the users. 
1. The user now visits or refreshes the [Audio Content Creation](https://aka.ms/audiocontentcreation) product page, and sign in with the user's Microsoft account. Select **Audio Content Creation** block among all speech products. Choose the speech resource in the pop-up window or in the settings at the upper right of the page. If the user cannot find available speech resource, check if you are in the right directory. To check the right directory, click the account profile in the upper right corner, and click **Switch** besides the "Current directory". If there are more than one directory available, it means you have access to multiple directories. Switch to different directories and go to settings to see if the right speech resource is available. 

    :::image type="content" source="media/audio-content-creation/add-role-first.png" alt-text="Add role dialog":::


Users who are in the same speech resource will see each other's work in Audio Content Creation studio. If you want each individual user to have a unique and private workplace in Audio Content Creation, please [create a new speech resource](#step-2---create-a-speech-resource) for each user and give each user the unique access to the speech resource.

### Remove users from a speech resource

1. Search for **Cognitive services** in the Azure portal, select the speech resource that you want to remove users from.
2. Click **Access control (IAM)**. Click the **Role assignments** tab to view all the role assignments for this speech resource.
3. Select the users you want to remove, click **Remove** > **Ok**.
    :::image type="content" source="media/audio-content-creation/remove-user.png" alt-text="Remove button":::

### Enable users to grant access

If you want one of the users to give access to other users, you need to give the user the owner role for the speech resource and set the user as the Azure directory reader.
1. Add the user as the owner of the speech resource. See [how to add users to a speech resource](#add-users-to-a-speech-resource).
    :::image type="content" source="media/audio-content-creation/add-role.png" alt-text="Role Owner field":::
2. In the [Azure portal](https://portal.azure.com/), select the collapsed menu in the upper left. Click **Azure Active Directory**, and then Click **Users**.
3. Search the user's Microsoft account, and go to the user's detail page. Click **Assigned roles**.
4. Click **Add assignments** -> **Directory Readers**. If the button "Add assignments" is grayed out, it means that you do not have the access. Only the global administrator of this directory can add assignment to users.

## See also

* [Long Audio API](./long-audio-api.md)

## Next steps

> [!div class="nextstepaction"]
> [Speech Studio](https://speech.microsoft.com)
