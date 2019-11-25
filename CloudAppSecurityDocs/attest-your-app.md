---
title: Attest your apps - Cloud App Security | Microsoft Docs
description: This article provides instructions for attesting your apps in Cloud App Security.
keywords: ''
author: shsagir
ms.author: shsagir
manager: shsagir
ms.date: 6/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.prod: ''
ms.service: cloud-app-security
ms.technology: ''
ms.assetid: 3536c0a5-fa56-4931-9534-cc7cc4b4dfb0
ms.reviewer: reutam
ms.suite: ems
ms.custom: seodec18
ms.openlocfilehash: 2ab3cd3c8a25ba9aab9ddf5639d393786fbbb5bd
ms.sourcegitcommit: 094bb42a198fe733cfd3aec79d74487672846dfa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/24/2019
ms.locfileid: "74460769"
---
# <a name="attest-your-app"></a>Atestar seu aplicativo

Microsoft Cloud App Security enables you to attest your app, so that you make sure that the compliance and security details we use to rate your app in our Cloud App Catalog are up to date.

Whether your app is already listed in the Cloud App Catalog, or it's new, submit a [self-attestation questionnaire](https://go.microsoft.com/fwlink/?linkid=2106624). For details on the self-attestation process, contact casfeedback@microsoft.com.

Follow the service attributes described below to successfully complete the submission of the questionnaire:

| Campo | Info category | Tipo | Valores aceitos | Description |
|------|-------|------|---------|----------|
| Nome do aplicativo | Geral | Cadeia de caracteres | Free text | The name for your application as it should appear in the Cloud App Catalog. |
| Description | Geral | Cadeia de caracteres | Free text | Short explanation of what your application enables users to do or achieve. |
| Category| Geral | Cadeia de caracteres | Close list - provided in questionnaire | Classification of the app according to the field to which it relates. |
| Matriz | Geral | Código do país | Close list - provided in questionnaire | The country of the provider's headquarters.|
| Data center| Geral | Country code array* | Close list - provided in questionnaire (Multi selection) | The country in which your data center resides (can be multiple locations) |
| Hosting company | Geral | Cadeia de caracteres | Free text | The name of the company that provides server hosting for the app. |
| Founded | Geral | Inteiro | YYYY (no later than 2019) | The year in which the provider was founded. |
| Holding | Geral | Cadeia de caracteres | Private, Public | Displays whether the provider is a publicly or privately held company |
| App domain | Geral | URL array* | Free text | The list of domains that are used to interact with the service (for example, 'teams.microsoft.com' for Microsoft Teams) |
| Terms of service | Geral | URL | Free text | Does this app provide a set of regulations that users must agree to follow in order to use the app? |
| Privacy policy | Geral | URL | Free text | A link to a legally binding document relating to how this provider handles customer, client, or employee information gathered as part of the app. |
| Logon URL | Geral | URL array* | Free text | The URL through which users log on to the app. |
| Fornecedor | Geral | Cadeia de caracteres | Free text | The name of the vendor who provides this app. |
| Tipos de dados | Geral | Cadeia de caracteres | Close list - provided in questionnaire | Which data types can be uploaded by the user to the app?|
| Homepage | Geral | URL | Free text | The provider's home page URL. |
| Disaster recovery plan | Geral | Booliano | True, False | Does this app have a disaster recovery plan that includes a backup and restore strategy? |
| Latest breach | Segurança | Data | MMM-dd-YYYY | Most recent incident in which sensitive, protected, or confidential data owned by the app was viewed, stolen, or used by an individual unauthorized to do so. |
| Data-at-rest encryption method | Segurança | Cadeia de caracteres | Close list - provided in questionnaire | The type of encryption of data-at-rest performed on the app. |
| Autenticação Multifator | Segurança | Booliano | True, False | Does this app support multi-factor authentication solutions? |
| IP address restriction | Segurança | Booliano | True, False | Does this app support restriction of specific IP addresses by the app? |
| User audit trail | Segurança | Booliano | True, False | Does this app support availability of audit trail per user account? |
| Admin audit trail | Segurança | Booliano | True, False | Does this app support availability of an admin audit trail in the app? |
| Data audit trail | Segurança | Booliano | True, False | Does this app support availability of a data audit trail in the app? |
| User can upload data | Segurança | Booliano | True, False | Does this app support user uploaded data? |
| Classificação de dados | Segurança | Booliano | True, False | Does this app enable the option for classification of the data uploaded to the app? |
| Lembrar senha | Segurança | Booliano | True, False | Does this app enable the option for remembering and saving user passwords in the app? |
| User-roles support | Segurança | Booliano | True, False | Does this app support distribution of users by roles and levels of permission? |
| File sharing | Segurança | Booliano | True, False | Does this app include features that allow file sharing between users? |
| Valid certificate name | Segurança | Booliano | True, False | Does the server provide an SSL certificate matching the domain name? |
| Certificado confiável | Segurança | Booliano | True, False | Does the server provide a trusted SSL certificate (not expired, verified, and trusted signature chain, etc.)? |
| Encryption protocol | Segurança | Cadeia de caracteres | Close list - provided in questionnaire | The latest version of Transport Layer Security (TLS) encryption protocol supported between user endpoint and app provider. If the server's certificate is non-existent or not valid, encryption is considered unsupported.|
| Heartbleed patched | Segurança | Booliano | True, False | Is the SSL implementation of the server patched for the Heartbleed bug to reduce vulnerability? |
| HTTP security headers: Strict-Transport-Security | Segurança | Booliano | True, False | Are HTTP Strict-Transport-Security headers implemented by the app on its website? |
| HTTP security headers: Content-Security-Policy | Segurança | Booliano | True, False | Are HTTP Content-Security-Policy headers implemented by the app on its website? |
| HTTP security headers: X-Frame-Options | Segurança | Booliano | True, False | Are HTTP X-Frame-Options headers implemented by the app on its website? |
| HTTP security headers: X-Content-Type-Options | Segurança | Booliano | True, False | Are HTTP X-Content-Type-Options headers implemented by the app on its website? |
| HTTP security headers: X-XSS-Protection | Segurança | Booliano | True, False | Are HTTP X-XSS-Protection headers implemented by the app on its website? |
| Supports SAML | Segurança | Booliano | True, False | Does this app support the SAML standard for exchanging authentication and authorization data? |
| Protected against DROWN | Segurança | Booliano | True, False | Are the application servers protected from DROWN attacks? |
| Penetration Testing | Segurança | Booliano | True, False | Does this app carry out penetration testing to detect and assess network vulnerabilities? |
| Requires user authentication | Segurança | Booliano | True, False | Does this app require authentication and disallow anonymous use? |
| Password policy: Password length limit | Segurança | Booliano | True, False | Does this app enforce a length limit on password creation? |
| Password policy: Character combination | Segurança | Booliano | True, False | Does this app enforce a character combination on password creation? |
| Password policy: Change password period | Segurança | Booliano | True, False | Does this app enforce users to reset their password periodically? |
| Password policy: Password history and reuse | Segurança | Booliano | True, False | Does this app disallow the reuse of old passwords? |
| Password policy: Personal information use | Segurança | Booliano | True, False | Does this app disallow the use of personal information in passwords? |
| Password policy | Segurança | Booliano | True, False | Does this app enforce a password policy that complies with best practices? |
| FINRA | Conformidade | Booliano | True, False, N/A | Does this app comply with FINRA, a standard set for not-for-profit organizations authorized by Congress that regulates and enforces the enhancement of investor safeguards and market integrity? |
| FISMA | Conformidade | Booliano | True, False, N/A | Does this app comply with FISMA, the US legislation that defines a comprehensive framework to protect government information, operations and assets within federal agencies, against threats? |
| GAAP | Conformidade | Booliano | True, False, N/A | Does this app comply with GAAP, a collection of commonly-followed accounting rules and standards for financial reporting? |
| HIPAA | Conformidade | Booliano | True, False, N/A | Does this app comply with HIPAA, the US legislation that sets standards for protecting the confidentiality and security of individually identifiable health information? |
| ISAE 3402 | Conformidade | Booliano | True, False, N/A | Does this app comply with ISAE 3402, the global standard providing assurance that a service organization has appropriate controls in place? |
| ISO 27001 | Conformidade | Booliano | True, False, N/A | Is this app ISO 27001 certified, a certificate given to companies upholding internationally recognized guidelines and general principles for initiating, implementing, maintaining, and improving information security management within an organization? |
| ITAR | Conformidade | Booliano | True, False, N/A | Does this app comply with ITAR, regulations controlling the export and import of defense-related articles and services found on the US Munitions List? |
| SOC 1 | Conformidade | Booliano | True, False, N/A | Does this app comply with SOC 1, reporting on controls at a service organization which are relevant to user entities' internal control over financial reporting? |
| SOC 2 | Conformidade | Booliano | True, False, N/A | Does this app comply with SOC 2, reporting on non-financial processing based on one or more of the Trust service criteria on security, privacy, availability, confidentiality, and processing integrity? |
| SOC 3 | Conformidade | Booliano | True, False, N/A | Does this app comply with SOC 3, reporting based on the Trust service criteria, that may be distributed freely and only contain management's assertion that they have met the requirements of the chosen criteria? |
| SOX | Conformidade | Booliano | True, False, N/A | Does this app comply with SOX, US legislation aimed at protecting shareholders and the general public from accounting errors and frauds, as well as improving the accuracy of corporate disclosures? |
| SP 800-53 | Conformidade | Booliano | True, False, N/A | Does this app comply with SP80053, recommended security controls for federal information systems and organizations? |
| SSAE 16 | Conformidade | Booliano | True, False, N/A | Does this app comply with the SSAE 16 standard for auditing a service organization's internal compliance controls and reporting processes? |
| PCI DSS version | Conformidade | Cadeia de caracteres | 1, 2, 3, 3.1, 3.2, N/A | The version of the PCI-DSS protocol supported by this app. |
| ISO 27018 | Conformidade | Booliano | True, False, N/A | Does this app comply with ISO 27018, which establishes commonly accepted controls and guidelines for processing and protecting Personally Identifiable Information (PII) in a public cloud computing environment? |
| GLBA | Conformidade | Booliano | True, False, N/A | Does this app comply with the Gramm-Leach-Bliley Act (GLBA), which requires financial institutions to establish standards for protecting the security and confidentiality of customers' personal information? |
| FedRAMP level | Conformidade | Cadeia de caracteres | High, Moderate, Low, N/A | The level of the FedRAMP-compliant solution provided by this app. |
| CSA STAR level | Conformidade | Cadeia de caracteres | Self-assessment, Certification, Attestation, C-STAR assessment, Continuous monitoring, N/A | The level of CSA STAR program at which the app is certified |
| Defesa de Privacidade | Conformidade | Booliano | True, False, N/A | Does this app comply with the EU-US Privacy Shield Framework, which imposes stronger obligations on US companies to protect Europeans' personal data? |
| ISO 27017 | Conformidade | Booliano | True, False, N/A | Does this app comply with ISO 27017, which establishes commonly accepted controls and guidelines for processing and protecting user information in a public cloud-computing environment? |
| COBIT | Conformidade | Booliano | True, False, N/A | Does this app comply with COBIT, which sets best practices for the governance and control of information systems and technology, and aligns IT with business principles? |
| COPPA | Conformidade | Booliano | True, False, N/A | Does this app comply with COPPA, which defines requirements on website and online services operators that provide content to children under 13 years of age? |
| FERPA | Conformidade | Booliano | True, False, N/A | Does this app comply with FERPA, a federal law that protects the privacy of student education records? |
| GAPP | Conformidade | Booliano | True, False, N/A | Does this app comply with GAPP, a collection of commonly-followed rules that address privacy risks in an organization? |
| HITRUST CSF | Conformidade | Booliano | True, False, N/A | Does this app comply with HITRUST CSF, a set of controls that harmonizes the requirements of information security regulations and standards? |
| Jericho Forum Commandments | Conformidade | Booliano | True, False, N/A | Does this app follow Jericho Forum Commandments, a set if principles to be observed when architecting systems for secure operation in de-perimeterized environments? |
| ISO 27002 | Conformidade | Booliano | True, False, N/A | Does this app comply with ISO 27002, which establishes common guidelines for organizational information security standards and information security management practices? |
| FFIEC | Conformidade | Booliano | True, False, N/A | Does this app comply with the Federal Financial Institutions Examination Council’s guidance on the risk management controls necessary to authenticate services in an Internet banking environment? |
| Propriedade dos dados | Legal | Booliano | True, False | Does this app fully preserve the user's ownership of uploaded data? |
| DMCA | Legal | Booliano | True, False | Does this app comply with the Digital Millennium Copyright Act (DMCA), which criminalizes any attempt to unlawfully access copyrighted material? |
| Política de retenção de dados | Legal | Booliano | True, False | What is the app’s policy for user data retention after account termination? |
| GDPR readiness statement | Legal | URL | Free text | A link to your website, when relevant, relating how this provider plans to handle GDPR compliance. |
| GDPR - Right to erasure | Legal | Booliano | True, False, N/A | Does this app stop processing and delete an individual’s personal data upon request? |
| GDPR - Report data breaches | Legal | Booliano | True, False, N/A | Does this app report data breaches to supervisory authorities and individuals affected by the breach, within 72 hours of breach detection? |
| GDPR - Impact assessment | Legal | Booliano | True, False, N/A | Does this app conduct data protection impact assessments to identify risk to individuals? |
| GDPR - Secure cross border data control | Legal | Booliano | True, False, N/A | Does this app securely transfer data across borders? |
| GDPR - Data protection officer | Legal | Booliano | True, False, N/A | Does this app appoint a data protection officer to oversee data security strategy and GDPR compliance? |
| GDPR - Right to object | Legal | Booliano | True, False, N/A | Does this app provide individuals with the ability to object to the processing of their personal data in certain circumstances? |
| GDPR - Right to access | Legal | Booliano | True, False, N/A | Does this app provide individuals with the ability to know, upon request, what personal data a company is using and how it is being used? |
| GDPR - Right to data Portablility | Legal | Booliano | True, False, N/A | Does this app provide individuals with the ability to obtain and reuse their personal data for their own purposes across different services upon request? |
| GDPR - Right to be informed | Legal | Booliano | True, False, N/A | Does this app inform individuals of the appropriate safeguards it takes when personal data is transferred to a non-EU country or to an international organization? |
| GDPR - Right to restriction of processing | Legal | Booliano | True, False, N/A | Does this app provide individuals with the ability to block or suppress processing of personal data? |
| GDPR - Rights related to automated decision making | Legal | Booliano | True, False, N/A | Does this app provide individuals with the ability to choose not to be subject to a decision that is based solely on automated processing? This includes profiling, which may have legal ramifications. |
| GDPR - lawful basis for processing | Legal | Booliano | True, False, N/A | Does this app process personal data lawfully in accordance with consent, contract, legal obligation, vital interests, legitimate interests, special category, data, and criminal offense data? |
| GDPR - Right to rectification | Legal | Booliano | True, False, N/A | Does this app provide individuals with the ability to rectify their personal data? The controller must respond to all requests from its data subjects within one month. |


\* Fields of type *Array* should be separated with semicolon (;).

## <a name="next-steps"></a>Próximas etapas 
[Atividades diárias para proteger seu ambiente de nuvem](daily-activities-to-protect-your-cloud-environment.md)

[!INCLUDE [Open support ticket](includes/support.md)] 

