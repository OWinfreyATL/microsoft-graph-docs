---
title: "Update workflow (lifecycle workflow)"
description: "Update the properties of a workflow object."
author: "AlexFilipin"
ms.localizationpriority: medium
ms.prod: "governance"
doc_type: apiPageType
---

# Update workflow (lifecycle workflow)

Namespace: microsoft.graph.identityGovernance

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update the properties of a [workflow](../resources/identitygovernance-workflow.md) object.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type|Permissions (from least to most privileged)|
|:---|:---|
|Delegated (work or school account)|LifecycleWorkflows.ReadWrite.All|
|Delegated (personal Microsoft account)|Not supported.|
|Application|LifecycleWorkflows.ReadWrite.All|

For delegated scenarios, the admin needs one of the following [Azure AD roles](/azure/active-directory/users-groups-roles/directory-assign-admin-roles#available-roles):

- Global administrator
- Lifecycle workflows administrator

## HTTP request

<!-- {
  "blockType": "ignored"
}
-->
``` http
PATCH /identityGovernance/lifecycleWorkflows/workflows/{workflowId}
```

## Request headers

|Name|Description|
|:---|:---|
|Authorization|Bearer {token}. Required.|
|Content-Type|application/json. Required.|

## Request body

[!INCLUDE [table-intro](../../includes/update-property-table-intro.md)]

|Property|Type|Description|
|:---|:---|:---|
|description|String|Describes the purpose of the workflow for administrative use.|
|displayName|String|A unique string that identifies the workflow.|
|isEnabled|Boolean|A boolean value that denotes whether the workflow is set to run or not.|
|isSchedulingEnabled|Boolean|A Boolean value that denotes whether scheduling is enabled or not. |


## Response

If successful, this action returns a `204 No Content` response code.

## Example 1: Update a task within a workflow

### Request

The following is an example of a request.

<!-- {
  "blockType": "request",
  "name": "lifecycleworkflows_update_workflow"
}
-->
``` http
PATCH https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/workflows/156ce798-1eb6-4e0a-8515-e79f54d04390
Content-Type: application/json
Content-length: 454

{
    "description": "Configure new hire tasks for onboarding employees on their first day",
    "displayName": "Australia Onboard new hire employee",
    "isEnabled": true,
    "isSchedulingEnabled": false
}
```

### Response

<!-- {
  "blockType": "response",
  "truncated": true,

}
-->
``` http
HTTP/1.1 204 No Content
```

## Example 2: Customize an email sent out by a task

### Request

The following is an example of a request

``` http
PATCH https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/workflows/156ce798-1eb6-4e0a-8515-e79f54d04390
Content-Type: application/json


{
    "description": "Configure new hire tasks for onboarding employees on their first day",
    "displayName": "Australia Onboard new hire employee",
    "isEnabled": true,
    "isSchedulingEnabled": false,
    "arguments": [
       {
        "name": "cc",
        "value": "b47471b9-af8f-4a5a-bfa2-b78e82398f6e, a7a23ce0-909b-40b9-82cf-95d31f0aaca2"
        },
        {
        "name": "customSubject",
        "value": "Welcome to the organization {{userDisplayName}}!"
        },
        {
        "name": "customBody",
        "value": "Welcome to our organization {{userGivenName}} {{userSurname}}. \nFor more information, reach out to your manager {{managerDisplayName}} at {{managerEmail}}."
        },
        {
        "name": "locale",
        "value": "en-us"
        }, 
]
}
```

### Response

<!-- {
  "blockType": "response",
  "truncated": true,

}
-->
``` http
HTTP/1.1 204 No Content
```
