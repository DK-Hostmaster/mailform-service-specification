# DK Hostmaster Mailform Service Specification

Public specification for the DK Hostmaster mailform domain registration service.

# **_DRAFT_**

2015/01/30
Revision: 5.0

# Table of Contents

<!-- MarkdownTOC -->

- [Introduction](#introduction)
- [About this Document](#about-this-document)
  - [Document History](#document-history)
- [The .dk Registry in Brief](#the-dk-registry-in-brief)
- [Mail-form Service](#mail-form-service)
- [The Form](#the-form)
- [General advice concerning completion of the application form](#general-advice-concerning-completion-of-the-application-form)
- [Submission of the application form](#submission-of-the-application-form)
- [Resources](#resources)
  - [Mailing list](#mailing-list)
  - [Issue Reporting](#issue-reporting)

<!-- /MarkdownTOC -->

# Introduction

This documentation primarily describes the current version 5.00, earlier revisions might still be actively supported for for documentation on these revisions please see:

  * [Version 4.00][README_4.00.md]
  * [Version 3.04][README_3.04.md] - _will be deprecated by the 1. of june 2015_

# About this Document

This specification describes version 5 (5.X.X) of the service and version 5.XX of the form implementations. Future releases will be reflected in updates to this specification, please see the document history section below.

Any future extensions and possible additions and changes to the implementation are not within the scope of this document and will not be discussed or mentioned throughout this document.

This document is owned and maintained by DK Hostmaster A/S and must not be distributed without this information.

All examples provided in the document are fabricated or changed from real data to demonstrate commands etc. any resemblence to actual data are coincidental.

## Document History

* 5.0 2015-01-30 
  * Documentation migrated from proprietary text/HTML files to dedicated Github repository, so we reset history, but start from version 5.00 to be consistent with earlier documentation, API revisions and service versions.

# The .dk Registry in Brief

DK Hostmaster is the registry for the ccTLD for Denmark (dk). The current model used in Denmark is based on a sole registry, with DK Hostmaster maintaining the central DNS registry.

# Mail-form Service

The DK Hostmaster mail-form service is a service offered to external parties offering registration of danish domain names on the ccTLD .dk to registered registrars.

The service requires the use of and possible development of client-side software and integration. This is beyond the scope of this specification as the API and other assets for assisting in this are the primary object of this document.

In addition to the assets, DK Hostmaster aims to assist client, users and developers of client software with integration towards DK Hostmaster and therefore provide facilities to ease this integration.

# The Form

The top of the form reads [`CPAI`]. The 4 letters describe 4 columns that continue down the form. They stand for:

  * _C_ompany (Danish: Virksomhed)
  * Danish _P_ublic sector organisation (Danish: Offentlig virksomhed)
  * _A_ssociation (Danish: Forening)
  * _I_ndividual (Danish: Privatperson)
  
  The columns determine how the individual sections are to be filled in. If, for example, the registrant is a company, then column _'C'_ must be used for section 4. If the billing contact is a Danish public sector organisation, then _'P'_ must be used when filling in section 6.

  Field 2c must, for now, only contain an 'N'.
  
  Field 2d concerns the billing contact and may be used only if the billing contact is a Danish public sector organisation that is to be invoiced via the Danish OIOXML/UBLXML standard. Field 2e also concerns the billing contact, but may be used by anyone requiring a purchase order number on future invoices relating to the domain name.
  
  Fields 2d and 2e are not included in section 6 because the electronic account code (Danish: DimensionsKontoStreng) and purchase order number will be linked with the individual domain name and not the billing contact's user ID. If the billing contact is changed, the electronic account code and purchase order number will therefore be removed from the domain name.

  The other fields in sections 1, 2 and 3 are not associated with any specific user type.
  
  If section 5 is not filled in, section 4 will automatically be copied into section 5.
  
  If section 6 is not filled in, section 5 will automatically be copied into section 6.
  
  Section 7-12 is about DNSSEC and shall only be put to use of the keyholder (section 7) and up to 5 keysets (sections 8-12) should be appointed to the domain from the time of set up.

| DK Domain Version Number | + | + | + | + | 5.00en
| Field types.....................[CPAI]

| Field | C | P | A | I | Description |
| Registrar |
| 1a. Registrar ID | + | + | + | + | |
| 1b. Registrar's reference | * | * | * | * | |
| Domain name |
| 2a. Domain name | + | + | + | + | |
| 2b. Registration period (years). | + | + | + | + | |
| 2c. VID (VIP domain name) | + | + | + | + | |
| 2d. Billing contact's PO-number | * | * | * | * | |
| 2e. Electronic account code | - | * | - | - | |
| 2f. Preactivations token | * | * | * | * | |
| Name servers |
| 3a. Name | * | * | * | * | |
| 3b. Name | * | * | * | * | |
| 3c. Name | * | * | * | * | |
| 3d. Name | * | * | * | * | |
| 3e. Name | * | * | * | * | |
| 3f. Name | * | * | * | * | |
| 3g. Name | * | * | * | * | |
| Registrant |
| 4.  User ID | ! | ! | ! | ! | |
| 4a. User type (CPAI) | + | + | + | + | |
| 4b. Company/Organisation | + | + | + | - | |
| 4c. VAT number | + | + | * | - | |
| 4e. Person | - | - | - | + | |
| 4f. Address 1 | + | + | + | + | |
| 4g. Address 2 | * | * | * | * | |
| 4h. Address 3 | * | * | * | * | |
| 4i. Postal code | + | + | + | + | |
| 4j. City | + | + | + | + | |
| 4k. Country code | + | + | + | + | |
| 4l. E-mail address | + | + | + | + | |
| 4m. Phone number | + | + | + | + | |
| 4n. Fax number | * | * | * | * | |
| Administrator |
| 5.  User ID | ! | ! | ! | ! | |
| 5a. User type (CPAI) | + | + | + | + | |
| 5b. Company/Organisation | + | + | + | - | |
| 5c. VAT number | + | + | * | - | |
| 5e. Person | * | * | * | + | |
| 5f. Address 1 | + | + | + | + | |
| 5g. Address 2 | * | * | * | * | |
| 5h. Address 3 | * | * | * | * | |
| 5i. Postal code | + | + | + | + | |
| 5j. City | + | + | + | + | |
| 5k. Country code | + | + | + | + | |
| 5l. E-mail address | + | + | + | + | |
| 5m. Phone number | + | + | + | + | |
| 5n. Fax number | * | * | * | * | |
| Billing contact |
| 6.  User ID | ! | ! | ! | ! | |
| 6a. User type (CPAI) | + | + | + | + | |
| 6b. Company/Organisation | + | + | + | - | |
| 6c. VAT number | + | + | * | - | |
| 6d. EAN number | - | + | - | - | |
| 6e. Person | * | * | * | + | |
| 6f. Address 1 | + | + | + | + | |
| 6g. Address 2 | * | * | * | * | |
| 6h. Address 3 | * | * | * | * | |
| 6i. Postal code | + | + | + | + | |
| 6j. City | + | + | + | + | |
| 6k. Country code | + | + | + | + | |
| 6l. E-mail address | + | + | + | + | |
| 6m. Phone number | + | + | + | + | |
| 6n. Fax number | * | * | * | * | |
| Keyholder (DNSSEC) |
| 7.  User ID | ! | ! | ! | ! | |
| 7a. User type (CPAI) | + | + | + | + | |
| 7b. Company/Organisation | + | + | + | - | |
| 7c. VAT number | + | + | * | - | |
| 7d. Person | * | * | * | + | |
| 7e. Address 1 | + | + | + | + | |
| 7f. Address 2 | * | * | * | * | |
| 7g. Address 3 | * | * | * | * | |
| 7h. Postal code | + | + | + | + | |
| 7i. City | + | + | + | + | |
| 7j. Country code | + | + | + | + | |
| 7k. E-mail address | + | + | + | + | |
| 7l. Phone number | + | + | + | + | |
| 7m. Fax number | * | * | * | * | |
| 8a. Keytag | * | * | * | * | |
| 8b. Algorithm | ^ | ^ | ^ | ^ | |
| 8c. Digest_type | ^ | ^ | ^ | ^ | |
| 8d. Digest | ^ | ^ | ^ | ^ | |
| 9a. Keytag | * | * | * | * | |
| 9b. Algorithm | ^ | ^ | ^ | ^ | |
| 9c. Digest_type | ^ | ^ | ^ | ^ | |
| 9d. Digest | ^ | ^ | ^ | ^ | |
| 10a. Keytag | * | * | * | * | |
| 10b. Algorithm | ^ | ^ | ^ | ^ | |
| 10c. Digest_type | ^ | ^ | ^ | ^ | |
| 10d. Digest | ^ | ^ | ^ | ^ | |
| 11a. Keytag | * | * | * | * | |
| 11b. Algorithm | ^ | ^ | ^ | ^ | |
| 11c. Digest_type | ^ | ^ | ^ | ^ | |
| 11d. Digest | ^ | ^ | ^ | ^ | |
| 12a. Keytag | * | * | * | * | |
| 12b. Algorithm | ^ | ^ | ^ | ^ | |
| 12c. Digest_type | ^ | ^ | ^ | ^ | |
| 12d. Digest | ^ | ^ | ^ | ^ | |

  ## Key
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
      <tr valign="top">
        <td>
          <p><strong>7</strong></p>
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
          <p>2</p>
        </td>
      </tr>
      <tr valign="top">
        <td>
          <p><strong>8</strong></p>
        </td>
        <td>
          <p>5</p>
        </td>
        <td>
          <p>3</p>
        </td>
        <td>
          <p>3</p>
        </td>
        <td>
          <p>256</p>
        </td>
      </tr>
      <tr valign="top">
        <td>
          <p><strong>9</strong></p>
        </td>
        <td>
          <p>5</p>
        </td>
        <td>
          <p>3</p>
        </td>
        <td>
          <p>3</p>
        </td>
        <td>
          <p>256</p>
        </td>
      </tr>
      <tr valign="top">
        <td>
          <p><strong>10</strong></p>
        </td>
        <td>
          <p>5</p>
        </td>
        <td>
          <p>3</p>
        </td>
        <td>
          <p>3</p>
        </td>
        <td>
          <p>256</p>
        </td>
      </tr>
      <tr valign="top">
        <td>
          <p><strong>11</strong></p>
        </td>
        <td>
          <p>5</p>
        </td>
        <td>
          <p>3</p>
        </td>
        <td>
          <p>3</p>
        </td>
        <td>
          <p>256</p>
        </td>
      </tr>
      <tr valign="top">
        <td>
          <p><strong>12</strong></p>
        </td>
        <td>
          <p>5</p>
        </td>
        <td>
          <p>3</p>
        </td>
        <td>
          <p>3</p>
        </td>
        <td>
          <p>256</p>
        </td>
      </tr>
    </tbody>
  </table>
  
# General advice concerning completion of the application form
Your application will be rejected if you modify the form or break the lines.

# Submission of the application form
Send one application per e-mail, entering `hostmaster@dk-hostmaster.dk` as the address in the &ldquo;To&rdquo; field. The application must not be sent as an attached file, Cc or similar.

It must be sent as plain text in one of these formats:

  * US-ASCII
  * ISO-8859-1
  * Windows-1252

If we accept your application, you will receive a unique tracking number. You should save this and use it as your reference in the future.

If we reject your application, you will not receive a tracking number. We will however advise you of why we have rejected the application.

You will find the blank forms here:

  * [5.00 english version](https://raw.githubusercontent.com/DK-Hostmaster/mailform-service-specification/master/5.00/5.00en.txt)
  * [5.00 danish version](https://raw.githubusercontent.com/DK-Hostmaster/mailform-service-specification/master/5.00/5.00da.txt)

# Resources 

## Mailing list

DK Hostmaster operates a mailing list for discussion and inquiries about the DK Hostmaster mail-form service. To subscribe to this list, write to the address below and follow the instructions. Please note that the list is for technical discussion only, any issues beyond the technical scope will not be responded to, please send these to the contact issue reporting address below and they will be passed on to the appropriate entities within DK Hostmaster.

* mailform-discuss+subscribe@liste.dk-hostmaster.dk

## Issue Reporting

For issue reporting related to this specification, the pre-activation service, sandbox or production environments, please contact us.  You are of course welcome to post these to the mailing list mentioned above, otherwise use the address specified below:

* tech@dk-hostmaster.dk
