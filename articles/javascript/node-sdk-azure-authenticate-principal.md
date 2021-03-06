---
title: Create an Azure service principal with Node.js
description: Learn how to use service principal authentication on Azure with Node.js and JavaScript
ms.topic: how-to
ms.date: 09/30/2020
ms.custom: devx-track-js
---

# Create an Azure service principal for Node.js

When an app needs to access resources, you can set up an identity for the app and authenticate the app with its own credentials. This identity is known as a *service principal*. Essentially, you create keys for your Azure Active Directory account that you provide to the SDK to authenticate rather than requiring user intervention or username/password.

The service principal approach enables you to:
- Assign permissions to the app identity that are different than your own permissions. Typically, these permissions are restricted to exactly what the app needs to do.
- Use a certificate for authentication when running an unattended script.

This topic shows you three techniques for creating a service principal.

- Azure portal
- Azure CLI 2.0

[!INCLUDE [chrome-note](includes/chrome-note.md)]

## Create a service principal using the Azure portal

Follow the steps outlined in the topic,
[Use portal to create an Azure Active Directory application and service principal that can access resources](/azure/active-directory/develop/howto-create-service-principal-portal), to generate the service principal.

## Create a service principal using the Azure CLI 2.0

Creating a service principal using the [Azure CLI 2.0](/cli/azure/install-az-cli2) can be accomplished with the following steps:

1. Download the [Azure CLI 2.0](/cli/azure/install-az-cli2).

2. Open a terminal window and type the command `az login` to start the login process.

3. Calling `az login` results in a URL and a code. Browse to the specified URL, enter the code, and login with your Azure identity (this may happen automatically if you're already logged in). 
You'll then be able to access your account via the CLI.

4. Get your subscription and tenant ID using the `az account list` command. You will need these when working with any of the Azure packages. The following shows an example of the output of this command:

	```shell
	{
	"cloudName": "AzureCloud",
	"id": "<subscriptionId>",
	"isDefault": true,
	"name": "<subscriptionName>",
	"registeredProviders": [],
	"state": "Enabled",
	"tenantId": "<tenantId>",
		"user": {
			"name": "hello@example.com",
			"type": "user"
		}
	}
    ```

5. Follow the steps outlined in the topic,
[Create an Azure service principal with the Azure CLI](/cli/azure/create-an-azure-service-principal-azure-cli), to generate the service principal. The JSON object in the output will contain the information you would need to authenticate with Azure.


## Using the service principal

Once you have a service principal, follow the [Authenticate with the Azure management modules for JavaScript](./node-sdk-azure-authenticate.md) topic for how to a create credentials object which you can use to authenticate your client with Azure Active Directory.
