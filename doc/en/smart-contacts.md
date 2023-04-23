<!--
 Copyright (C) 2022 Innovate for Vegas Foundation
 
 This file is part of ov-smart-social.
 
 ov-smart-social is free software: you can redistribute it and/or modify
 it under the terms of the GNU General Public License as published by
 the Free Software Foundation, either version 3 of the License, or
 (at your option) any later version.
 
 ov-smart-social is distributed in the hope that it will be useful,
 but WITHOUT ANY WARRANTY; without even the implied warranty of
 MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 GNU General Public License for more details.
 
 You should have received a copy of the GNU General Public License
 along with ov-smart-social.  If not, see <http://www.gnu.org/licenses/>.
-->

# Smart Social Smart Contacts

This is the age of the QR Code, used often to share URLs for websites and sign-in forms and whatnot, but perhaps more so to share contact information. Contact information across platforms, across devices, across language barriers, across any divide, is a constant requirement every day, and it can be made more useful with some creative application of existing standards and offline device features.

The Smart Contacts component of Smart Social should function independently, but is intended to integrate nicely with other Smart Social components and external services.

## Highest Priority Considerations

It is often the case that a person would like to share one contact configuration in one context, and some other configuration in another. For examples (see User Stories section for more detail), a user may want to have contact information to share for one job or role, another set for a completely different job or role, and yet another configuratton for personal use without reference to any job or role. It is critical that the user always has control over which information is shared in which context, if at all.

An extremely unlikely circumstance, wherein some user creates and publishes Smart Contact information for some other person, without permission, could be considered a violation of a person’s privacy. While this is difficult to check, it is something to be aware of, and it may come to pass that user verification is required, via email, phone number check, or similar. Verifying an email address seems like an easy first pass, though this requires that a user share this personal information where they not want to share their email address in general. It is something to ponder sooner rather than later.

## Specification Details

If a Smart City relies on Twitter and Nextdoor to inform its population of important updates, there is something missing. That is Smart Contacts.

Maintaining a locale-based anonymous communication channel is reasonably simple with modern technology and enables one-way broadcast based on location, and two-way conversation regarding service requests and other lower-priority discussion (this would not be intended to take the place of emergency services contacts such as 9-1-1 and similar).

## External Reference Materials

[vCard RFC](https://datatracker.ietf.org/doc/html/rfc6350)

[CardDAV RFC](https://datatracker.ietf.org/doc/html/rfc6352)

[Lightweight Directory Access Protocol](https://ldap.com/)

[Schema.org Person type](https://schema.org/Person)

## User Stories

Individual stories may be converted into Issues, or consolidated or exploded as needed for development and implementation.

**Terms**:

- **Consumer**: an end user of Smart Contacts, may be a human or some automation, and may be creating Contacts and/or Consuming Contacts.
- **ExtSource**: an external origin for contacts to capture, store, and possibly re-publish
- **IntSource**: an internal origin of contacts to store and publish.
- **Peer**: a special case Consumer or ExtSource, often both.
- **Developer**: one who makes use of Smart Contacts APIs (or CardDAV) or similar to build on the platform

### Typical Uses

- **Card**: As a Consumer, I would like to publish my Contact information to the Smart Contact server.
  - **Conversation**: The implication here is that a Consumer needs to create an account of some kind (this is purposely vague for this User Story) and then create a Contact associated with their account, with information they provide which may or may not match exactly their account information (eg a different email address, a different full name, a different role at org, etc etc).
  - **Confirmation**:
    - Consumer is able to create a Contact record with field values they provide.

Converted to https://github.com/InnovateForVegas/ov-smart-social/issues/9

---

- **Card**: As a Consumer, I would like to publish multiple variable Contact informations to the Smart Contact server, without each Contact associated with another to other Consumers.
  - **Conversation**: Once a Consumer can create one Contact record, they are able to connect multiple Contact records, with variable information as they see fit, with each Contact record completely separate from every other owned by that Consumer. This enables a Consumer to share their Contact information in different contexts, with different information for each, as they see fit.
  - **Confirmation**:
    - Consumer is able to create multiple Contact record with field values they provide, with each completely disassociated from the others when viewed or used by other Consumers.

Converted to https://github.com/InnovateForVegas/ov-smart-social/issues/10

---

- **Card**: As a Consumer, I would like to publish a specific Contact in a profile or similar for public consumption in search results or via other links.
  - **Conversation**: One Consumer publishes their Contact information to the Smart Contact server, and another Consumer (or even the same Consumer) searches for that Contact information via some query keys, the result of that search, or perhaps the Contact revealed in a direct public URL, is selectable and controllable by the Consumer that owns that Contact record among one or more Contact records.
    - Consumer is able to select a specific Contact record that is made public in a search results profile or similar, without identifying other Contact records owned by the Consumer.

Converted to https://github.com/InnovateForVegas/ov-smart-social/issues/11

---

- **Card**: As a Consumer, I would like to view a Contact in a mobile or desktop web browser.
  - **Conversation**: A Contact record visible via a browser-based web page is useful for associating public Contact information with a public Event or other content (within the Smart Social system or otherwise). The profile view of a Contact record should include appropriate meta tag data and schema.org annotation. The Contact record may also be displayed with a VCard (.vcf) link so Consumer may download the Contact record information in standard form.
  - **Confirmation**:
    - Consumer may view a public Contact record in their web browser, as normal web content, with a link to download the VCard form of the Contact record for their own uses.

Converted to https://github.com/InnovateForVegas/ov-smart-social/issues/12
