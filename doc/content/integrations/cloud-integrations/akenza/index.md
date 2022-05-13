---
title: "akenza"
description: ""
weight: 
aliases: ["/integrations/cloud-integrations/akenza-core/akenza-setup", "/integrations/cloud-integrations/akenza-core/tts-setup", "/integrations/cloud-integrations/akenza-core"]
---

[akenza](https://akenza.io/) is an IoT platform designed to help you develop your own smart solutions. It connects your sensors, manages the connectivity layer, processes your data and makes it accessible to your cloud application. 

<!--more-->

Two available methods of connecting {{% tts %}} with akenza are described in this guide:

- [Creating the integration on akenza]({{< relref "#creating-the-integration-on-akenza" >}})
- [Instantiating a Webhook template on {{% tts %}}]({{< relref "#instantiating-a-webhook-template-on-the-things-stack" >}})

## Prerequisites

1. A [user account on akenza](https://auth.akenza.io/login).

## Create an organization and a workspace on akenza

When you first log in to your akenza account, you will be presented with a wizard to create your organization. Fill in the **Organization Name** and optionally other fields, then click the **Create organization** button.

{{< figure src="create-org.png" alt="Creating an organization" >}}

Next, create your first workspace. Fill in the **Workspace Name** and click the **Create workspace** button.

{{< figure src="create-workspace.png" alt="Creating a workspace" >}}

Finish with the **Finalize setup** button.

Now, choose the preferred integration method out of those that are explained in the intro of this guide, and keep reading for further steps.

## Creating the integration on akenza

Choose the **Import existing LoRa Devices** option to continue. This is equivalent to navigating to the **Integrations** tab on the left hand menu in your akenza workspace.

{{< figure src="import-lora-devices.png" alt="Import LoRa devices" >}}

Next step is to create the integration, so hit the **+ Create Integration** button.

In the **Connectivity provider** menu, choose **{{% tts %}}**. 

{{< figure src="connectivity-provider.png" alt="Choosing connectivity provider" >}}

To configure {{% tts %}} integration, you first have to choose the host, i.e. {{% tts %}} cluster, depending on your region.

Then, choose the desired **Authentication** method. If you choose the **Application ID / API Key** authentication for example, you will need to provide your {{% tts %}} application ID in the **Application ID** field. You will also need to provide an **API key** from {{% tts %}} that you have previously created in your {{% tts %}} application.

{{< figure src="tts-integration.png" alt="Set up The Things Stack integration" >}}

Finally, just fill in the **Integration name**, click **Next** and finish with **Done** button.

After this process is completed, the initial synchronization will start, and after a few minutes (depending on how many devices your {{% tts %}} application contains), the devices will automatically become available on akenza.

Navigate to the **Assets** tab on the left hand menu in akenza to manage your devices. Select a desired device to see its **Connectivity Details** or to send a **Downlink** to it.

To observe uplinks coming from your devices, navigate to the **Logs** tab on the left hand menu.

{{< figure src="observe-uplink.png" alt="Observing uplinks" >}}

## Instantiating a Webhook template on {{% tts %}}

Choose the **Connect your first device** option to continue. This is equivalent to navigating to the **Data Flows** tab on the left hand menu in your akenza workspace.

Next step is to create a data flow on akenza, so hit the **+ Create Data Flow** button.

Out of list of connectors, choose to **Connect a device over HTTP**.

{{< figure src="http-connector.png" alt="HTTP connector" >}}

Finish with **Save Data Flow** and providing its **Name**.

When you have created a data flow, it's time to create a device. Note that you can skip steps to create a device if you check the **Create Device with this Data Flow** box while creating the data flow.

Navigate to the **Assets** tab on the left hand menu and hit the button to start with device creation.

In the **Basic Information** step, give your device a name and click **Next**. In the **Data Processing** step you can just click **Next**.

In the **Connectivity Parameters** step, you need to give your device a **Device ID**. You can generate the ID, but it's good to use your device's DevEUI from {{% tts %}} to be able to easily identify it later.

Finish with the **Create device** button. Find and select your device under **Assets** to see your its details, message logs, etc.

Select the **API-Configuration** tab to obtain the uplink secret (highlighted in the image below). Copy the uplink secret's value for further steps (excluding `secret=`).

{{< figure src="uplink-secret.png" alt="Obtaining akenza uplink secret" >}}

Now, when you have set up everything needed on akenza, you need to instantiate the **akenza** Webhook template in {{% tts %}}.

Name your Webhook integration in the **Webhook ID** field. 

Fill in the **Uplink Secret** field with the uplink secret value you copied from akenza in the previous step.

{{< figure src="instantiate-webhook-template.png" alt="Instantiating akenza Webhook template" >}}

Finish with creating the integration by clicking the **Create akenza webhook** button.

Next time your device sends an uplink to {{% tts %}}, you will be able to see it in the **Logs** tab on the left hand menu in akenza.
