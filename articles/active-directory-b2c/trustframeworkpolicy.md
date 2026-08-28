---
title: TrustFrameworkPolicy - Azure Active Directory B2C  
description: Specify the TrustFrameworkPolicy element of a custom policy in Azure Active Directory B2C.

author: kengaderdus
manager: CelesteDG

ms.service: entra-id

ms.topic: reference
ms.date: 01/23/2024
ms.author: kengaderdus
ms.subservice: b2c


#Customer intent: As a developer creating custom policies for Azure Active Directory B2C, I want to understand the structure and elements of the TrustFrameworkPolicy XML files, so that I can define the necessary attributes, elements, and references for my policies.

---

# TrustFrameworkPolicy
[!INCLUDE [active-directory-b2c-end-of-sale-notice-b](../../includes/active-directory-b2c-end-of-sale-notice-b.md)]

[!INCLUDE [active-directory-b2c-advanced-audience-warning](../../includes/active-directory-b2c-advanced-audience-warning.md)]

* custom policy
  * == >1 ".xml" / 
    * are | hierarchical chain
    * == policy's elements
      * _Examples:_ claims schema, claims transformations, content definitions, claims providers, technical profiles, user journey, and orchestration steps

* `<TrustFrameworkPolicy/>`
  * == 1 policy
  * 's attributes
    * == | <TrustFrameworkPolicy>
    
      | Attribute                   | Required  | Description                                                                                                                                                                                                                |
      |-----------------------------|-----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
      | PolicySchemaVersion         | Yes       | The schema version that is to be used to execute the policy. The value must be `0.3.0.0`                                                                                                                                   |
      | TenantObjectId              | No        | Azure AD B2C tenant's UID                                                                                                                                                                                                  |
      | TenantId                    | Yes       | The unique identifier of the tenant to which this policy belongs.                                                                                                                                                          |
      | PolicyId                    | Yes       | The unique identifier for the policy. This identifier must be prefixed by *B2C_1A_*                                                                                                                                        |
      | PublicPolicyUri             | Yes       | The URI for the policy, which is combination of the tenant ID and the policy ID.                                                                                                                                           |
      | DeploymentMode              | No        | Possible values: `Production`, or `Development`. `Production` is the default. Use this property to debug your policy. For more information, see [Collecting Logs](troubleshoot-with-application-insights.md).              |
      | UserJourneyRecorderEndpoint | No        | The endpoint that is used for logging. The value must be set to `urn:journeyrecorder:applicationinsights` if the attribute exists. For more information, see [Collecting Logs](troubleshoot-with-application-insights.md). |

  * 's elements
    * == children elements
    
      | Element                               | Occurrences  | Description |
      |---------------------------------------|--------------| ----------- |
      | BasePolicy                            | 0:1          | The identifier of a base policy. |
      | [BuildingBlocks](buildingblocks.md)   | 0:1          | The building blocks of your policy. |
      | [ClaimsProviders](claimsproviders.md) | 0:1          | A collection of claims providers. |
      | [UserJourneys](userjourneys.md)       | 0:1          | A collection of user journeys. |
      | [SubJourneys](subjourneys.md)         | 0:1          | A collection of sub journeys. |
      | [RelyingParty](relyingparty.md)       | 0:1          | A definition of a relying party policy. |

    * `<BasePolicy>`
      * allows
        * inherit a policy -- from -- ANOTHER policy
      * 's elements
        
        | Element | Occurrences | Description |
        | ------- | ----------- | --------|
        | TenantId | 1:1 | The identifier of your Azure AD B2C tenant. |
        | PolicyId | 1:1 | The identifier of the parent policy. |

    * [active-directory-b2c-advanced-audience-warning](../../includes/active-directory-b2c-custom-policy-occurrence.md)]
