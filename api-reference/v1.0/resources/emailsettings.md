---
title: "emailSettings resource type"
description: "Defines the settings for emails sent using Lifecycle Workflows."
author: "AlexFilipin"
ms.localizationpriority: medium
ms.prod: "governance"
doc_type: resourcePageType
---

# emailSettings resource type

Namespace: microsoft.graph

Defines the email settings for emails sent from Lifecycle Workflows

## Properties
|Property|Type|Description|
|:---|:---|:---|
|senderDomain|String|The domain from which the email is being sent from.|
|useCompanyBranding|Boolean|Identifies if a customer is using company branding or not.|

## Relationships
None.

## JSON representation
The following is a JSON representation of the resource.
<!-- {
  "blockType": "resource",
  "@odata.type": "microsoft.graph.emailSettings"
}
-->
``` json
{
  "@odata.type": "#microsoft.graph.emailSettings",
  "senderDomain": "String",
  "useCompanyBranding": "Boolean"
}
```
