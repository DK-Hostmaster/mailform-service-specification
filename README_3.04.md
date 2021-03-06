# DK Hostmaster Mailform Service Specification

Public specification for the DK Hostmaster mailform domain registration service.

2016/12/28
Revision: 3.0

# Table of Contents

<!-- MarkdownTOC -->

- [Introduction](#introduction)
- [About this Document](#about-this-document)
  - [Document History](#document-history)
- [The .dk Registry in Brief](#the-dk-registry-in-brief)
- [Mail-form Service](#mail-form-service)
- [The Form](#the-form)
  - [Form Keys](#form-keys)
- [General advice concerning completion of the application form](#general-advice-concerning-completion-of-the-application-form)
- [Submission of the application form](#submission-of-the-application-form)
- [Resources](#resources)
  - [Mailing list](#mailing-list)
  - [Issue Reporting](#issue-reporting)

<!-- /MarkdownTOC -->

<a name="introduction"></a>
# Introduction

This documentation describes the version 3.04, for newer revisions please see:

  * [Version 4.00][README_4.00.md]
  * [Version 5.00][README.md]

<a name="about-this-document"></a>
# About this Document

This specification describes version 3 (3.X.X) of the service and version 3.XX of the form implementations. Future releases will be reflected in updates to this specification, please see the document history section below.

Any future extensions and possible additions and changes to the implementation are not within the scope of this document and will not be discussed or mentioned throughout this document.

This document is owned and maintained by DK Hostmaster A/S and must not be distributed without this information.

All examples provided in the document are fabricated or changed from real data to demonstrate commands etc. any resemblence to actual data are coincidental.

Printable version can be obtained via [this link](https://github.com/DK-Hostmaster/mailform-service-specification/blob/master/README.md), using the gitprint service.

<a name="document-history"></a>
## Document History

* 3.0 2016-12-28
  * Documentation migrated from proprietary text/HTML files to dedicated Github repository

<a name="the-dk-registry-in-brief"></a>
# The .dk Registry in Brief

DK Hostmaster is the registry for the ccTLD for Denmark (dk). The current model used in Denmark is based on a sole registry, with DK Hostmaster maintaining the central DNS registry.

<a name="mail-form-service"></a>
# Mail-form Service

The DK Hostmaster mail-form service is a service offered to external parties offering registration of danish domain names on the ccTLD .dk to registered registrars.

The service requires the use of and possible development of client-side software and integration. This is beyond the scope of this specification as the API and other assets for assisting in this are the primary object of this document.

In addition to the assets, DK Hostmaster aims to assist client, users and developers of client software with integration towards DK Hostmaster and therefore provide facilities to ease this integration.

<a name="the-form"></a>
# The Form

The top of the form reads [`CPAI`]. The 4 letters describe 4 columns that continue down the form. They stand for:

* **C**ompany (Danish: Virksomhed)
* Danish **P**ublic sector organisation (Danish: Offentlig virksomhed)
* **A**ssociation (Danish: Forening)
* **I**ndividual (Danish: Privatperson)

The columns determine how the individual sections are to be filled in. If, for example, the registrant is a company, then column **'C'** must be used for section 4. If the billing contact is a Danish public sector organisation, then **'P'** must be used when filling in section 6.

Field 2c must, only contain an 'N'.

Field 2d concerns the billing contact and may be used only if the billing contact is a Danish public sector organisation that is to be invoiced via the Danish OIOXML/UBLXML standard. Field 2e also concerns the billing contact, but may be used by anyone requiring a purchase order number on future invoices relating to the domain name.

Fields 2d and 2e are not included in section 6 because the electronic account code (Danish: DimensionsKontoStreng) and purchase order number will be linked with the individual domain name and not the billing contact's user ID. If the billing contact is changed, the electronic account code and purchase order number will therefore be removed from the domain name.

The other fields in sections 1, 2 and 3 are not associated with any specific user type.

If section 5 is not filled in, section 4 will automatically be copied into section 5.

If section 6 is not filled in, section 5 will automatically be copied into section 6.

DK Domain Version Number: 3.04en
Field types [CPAI]

| Field                           | C | P | A | I | Description |
| ------------------------------- |---|---|---|---|-------------|
| **Registrar section**           |   |   |   |   |             |
| 1a. Registrar ID                | + | + | + | + | Unique id for the registrar submitting the form |
| 1b. Registrar's reference       | * | * | * | * | Optional ID for identification by the registrar |
| **Domain name section**         |   |   |   |   |             |             
| 2a. Domain name                 | + | + | + | + | Application domain name |
| 2b. Registration period (years) | + | + | + | + | `1`, `2`, `3` or `5` years |
| 2c. VID (VIP domain name)       | + | + | + | + | Can only be `N` |
| 2d. Billing contact's PO-number | * | * | * | * | Optional purcharse order number |
| 2e. Electronic account code     | - | * | - | - | EAN-number for eletronical billing, only applicable for public organisations |
| **Name servers section**        |   |   |   |   |             |
| 3a. Name                        | + | + | + | + | Mandatory name server |
| 3b. IP address                  | ^ | ^ | ^ | ^ | IP address |
| 3c. Name                        | + | + | + | + | Mandatory name server |
| 3d. IP address                  | ^ | ^ | ^ | ^ | IP address |
| 3e. Name                        | * | * | * | * | Optional extra nameserver |
| 3f. IP address                  | ^ | ^ | ^ | ^ | IP address |
| 3g. Name                        | * | * | * | * | Optional extra nameserver |
| 3h. IP address                  | ^ | ^ | ^ | ^ | IP address |
| 3i. Name                        | * | * | * | * | Optional extra nameserver |
| 3j. IP address                  | ^ | ^ | ^ | ^ | IP address |
| 3k. Name                        | * | * | * | * | Optional extra nameserver |
| 3l. IP address                  | ^ | ^ | ^ | ^ | IP address |
| 3m. Name                        | * | * | * | * | Optional extra nameserver |
| 3n. IP address                  | ^ | ^ | ^ | ^ | IP address |
| **Registrant contact section**  |   |   |   |   | The registrant section can either be filled in as a user-id or a complete set of data | 
| 4.  User ID                     | ! | ! | ! | ! | Existing user-id |
| 4a. User type                   | + | + | + | + | User type `C` (company), `P` Public Organisation, `A` Association or `I` individual |
| 4b. Company/Organisation        | + | + | + | - | Name of company, Organisation or Association |
| 4c. VAT number                  | + | + | * | - | VAT/CVR number |
| 4e. Person                      | - | - | - | + | Name of individual |
| 4f. Address 1                   | + | + | + | + | Mandatory address field |
| 4g. Address 2                   | * | * | * | * | Optional address field |
| 4h. Address 3                   | * | * | * | * | Optional address field |
| 4i. Postal code                 | + | + | + | + | Mandatory zip/postal code |
| 4j. City                        | + | + | + | + | Mandatory city name |
| 4k. Country code                | + | + | + | + | Mandatory two-letter country code ([ISO-3166-1][ISO-3166-1]) |
| 4l. E-mail address              | + | + | + | + | Mandatory e-mail address |
| 4m. Phone number                | + | + | + | + | Mandatory phone number |
| 4n. Fax number                  | * | * | * | * | Optional fax/facsimile number |
| **Administrator contact section** |   |   |   |   | The administrator contact section can either be filled in as a user-id or a complete set of data, if not filled in data from the above Registrant contact section will be used |
| 5.  User ID                     | ! | ! | ! | ! | Existing user-id |
| 5a. User type (CPAI)            | + | + | + | + | User type `C` (company), `P` Public Organisation, `A` Association or `I` individual |
| 5b. Company/Organisation        | + | + | + | - | Name of company, Organisation or Association |
| 5c. VAT number                  | + | + | * | - | VAT/CVR number |
| 5e. Person                      | * | * | * | + | Name of individual |
| 5f. Address 1                   | + | + | + | + | Mandatory address field |
| 5g. Address 2                   | * | * | * | * | Optional address field |
| 5h. Address 3                   | * | * | * | * | Optional address field |
| 5i. Postal code                 | + | + | + | + | Mandatory zip/postal code |
| 5j. City                        | + | + | + | + | Mandatory city name |
| 5k. Country code                | + | + | + | + | Mandatory two-letter country code ([ISO-3166-1][ISO-3166-1]) |
| 5l. E-mail address              | + | + | + | + | Mandatory e-mail address |
| 5m. Phone number                | + | + | + | + | Mandatory phone number |
| 5n. Fax number                  | * | * | * | * | Optional fax/facsimile number |
| **Billing contact section**     |   |   |   |   | The billing contact section can either be filled in as a user-id or a complete set of data, if not filled in data from the above Registrant contact section will be used | 
| 6.  User ID                     | ! | ! | ! | ! | Existing user-id |
| 6a. User type (CPAI)            | + | + | + | + | User type `C` (company), `P` Public Organisation, `A` Association or `I` individual |
| 6b. Company/Organisation        | + | + | + | - | Name of company, Organisation or Association |
| 6c. VAT number                  | + | + | * | - | VAT/CVR number |
| 6d. EAN number                  | - | + | - | - | EAN-number for eletronical billing, only applicable for public organisations |
| 6e. Person                      | * | * | * | + | Name of individual |
| 6f. Address 1                   | + | + | + | + | Mandatory address field |
| 6g. Address 2                   | * | * | * | * | Optional address field |
| 6h. Address 3                   | * | * | * | * | Optional address field |
| 6i. Postal code                 | + | + | + | + | Mandatory zip/postal code |
| 6j. City                        | + | + | + | + | Mandatory city name |
| 6k. Country code                | + | + | + | + | Mandatory two-letter country code ([ISO-3166-1][ISO-3166-1]) |
| 6l. E-mail address              | + | + | + | + | Mandatory e-mail address |
| 6m. Phone number                | + | + | + | + | Mandatory phone number |
| 6n. Fax number                  | * | * | * | * | Optional fax/facsimile number |

<a name="form-keys"></a>
## Form Keys

  <table border="0">
    <tbody>
      <tr>
        <td valign="top">!</td>
        <td>If this field is filled in, the rest of the section does not need to be completed because the contents of the other fields will automatically be filled in with details from the user ID concerned.</td>
      </tr>
      <tr>
        <td valign="top">+</td>
        <td>Field must be filled in.</td>
      </tr>
      <tr>
        <td valign="top">-</td>
        <td>Field must not be filled in.</td>
      </tr>
      <tr>
        <td valign="top">*</td>
        <td>Field may be filled in.</td>
      </tr>
      <tr>
        <td valign="top">^</td>
        <td>Field may be filled in, but only if the preceding field has been filled in.</td>
      </tr>
    </tbody>
  </table>
  <p>&nbsp;</p>
  <p><strong>Max. number of characters for the individual fields</strong></p>
  <table border="1">
    <tbody>
      <tr valign="top">
        <td><br></td>
        <td>
          <p><strong>-</strong></p>
        </td>
        <td>
          <p><strong>a</strong></p>
        </td>
        <td>
          <p><strong>b</strong></p>
        </td>
        <td>
          <p><strong>c</strong></p>
        </td>
        <td>
          <p><strong>d</strong></p>
        </td>
        <td>
          <p><strong>e</strong></p>
        </td>
        <td>
          <p><strong>f</strong></p>
        </td>
        <td>
          <p><strong>g</strong></p>
        </td>
        <td>
          <p><strong>h</strong></p>
        </td>
        <td>
          <p><strong>i</strong></p>
        </td>
        <td>
          <p><strong>j</strong></p>
        </td>
        <td>
          <p><strong>k</strong></p>
        </td>
        <td>
          <p><strong>l</strong></p>
        </td>
        <td>
          <p><strong>m</strong></p>
        </td>
        <td>
          <p><strong>n</strong></p>
        </td>
      </tr>
      <tr valign="top">
        <td>
          <p><strong>1</strong></p>
        </td>
        <td><br></td>
        <td>
          <p>13</p>
        </td>
        <td>
          <p>40</p>
        </td>
      </tr>
      <tr valign="top">
        <td>
          <p><strong>2</strong></p>
        </td>
        <td><br></td>
        <td>
          <p>66</p>
        </td>
        <td>
          <p>1</p>
        </td>
        <td>
          <p>1</p>
        </td>
        <td>
          <p>20</p>
        </td>
        <td>
          <p>20</p>
        </td>
      </tr>
      <tr valign="top">
        <td>
          <p><strong>3</strong></p>
        </td>
        <td><br></td>
        <td>
          <p>254</p>
        </td>
        <td>
          <p>15</p>
        </td>
        <td>
          <p>254</p>
        </td>
        <td>
          <p>15</p>
        </td>
        <td>
          <p>254</p>
        </td>
        <td>
          <p>15</p>
        </td>
        <td>
          <p>254</p>
        </td>
        <td>
          <p>15</p>
        </td>
        <td>
          <p>254</p>
        </td>
        <td>
          <p>15</p>
        </td>
        <td>
          <p>254</p>
        </td>
        <td>
          <p>15</p>
        </td>
        <td>
          <p>254</p>
        </td>
        <td>
          <p>15</p>
        </td>
      </tr>
      <tr valign="top">
        <td>
          <p><strong>4</strong></p>
        </td>
        <td>
          <p>13</p>
        </td>
        <td>
          <p>1</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>20</p>
        </td>
        <td><br></td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>10</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>2</p>
        </td>
        <td>
          <p>254</p>
        </td>
        <td>
          <p>20</p>
        </td>
        <td>
          <p>20</p>
        </td>
      </tr>
      <tr valign="top">
        <td>
          <p><strong>5</strong></p>
        </td>
        <td>
          <p>13</p>
        </td>
        <td>
          <p>1</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>20</p>
        </td>
        <td><br></td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>10</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>2</p>
        </td>
        <td>
          <p>254</p>
        </td>
        <td>
          <p>20</p>
        </td>
        <td>
          <p>20</p>
        </td>
      </tr>
      <tr valign="top">
        <td>
          <p><strong>6</strong></p>
        </td>
        <td>
          <p>13</p>
        </td>
        <td>
          <p>1</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>20</p>
        </td>
        <td>
          <p>13</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>10</p>
        </td>
        <td>
          <p>40</p>
        </td>
        <td>
          <p>2</p>
        </td>
        <td>
          <p>254</p>
        </td>
        <td>
          <p>20</p>
        </td>
        <td>
          <p>20</p>
        </td>
      </tr>
    </tbody>
  </table>

<a name="general-advice-concerning-completion-of-the-application-form"></a>
# General advice concerning completion of the application form
Your application will be rejected if you modify the form or break the lines.

<a name="submission-of-the-application-form"></a>
# Submission of the application form
Send one application per e-mail, entering `hostmaster@dk-hostmaster.dk` as the address in the &ldquo;To&rdquo; field. The application must not be sent as an attached file, Cc or similar.

It must be sent as plain text in one of the following formats:

  * US-ASCII
  * ISO-8859-1
  * Windows-1252

If we accept your application, you will receive a unique tracking number. You should save this and use it as your reference in the future.

If we reject your application, you will not receive a tracking number. We will however advise you of why we have rejected the application.

You will find the blank forms here:

  * [3.04 english version](https://raw.githubusercontent.com/DK-Hostmaster/mailform-service-specification/master/3.04/3.04en.txt)
  * [3.04 danish version](https://raw.githubusercontent.com/DK-Hostmaster/mailform-service-specification/master/3.04/3.04da.txt), please note that this file is encoded using ISO-8859-1

<a name="resources"></a>
# Resources 

<a name="mailing-list"></a>
## Mailing list

DK Hostmaster operates a mailing list for discussion and inquiries about the DK Hostmaster mail-form service. To subscribe to this list, write to the address below and follow the instructions. Please note that the list is for technical discussion only, any issues beyond the technical scope will not be responded to, please send these to the contact issue reporting address below and they will be passed on to the appropriate entities within DK Hostmaster.

* tech-discuss+subscribe@liste.dk-hostmaster.dk

<a name="issue-reporting"></a>
## Issue Reporting

For issue reporting related to this specification, the pre-activation service, sandbox or production environments, please contact us.  You are of course welcome to post these to the mailing list mentioned above, otherwise use the address specified below:

* info@dk-hostmaster.dk

[ISO-3166-1]: https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2
